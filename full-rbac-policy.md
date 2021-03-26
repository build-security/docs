# RBAC Policy

The following will demonstrate building a policy using a simple Role Based Access Control in the build.security's system.

### Roles and Permissions Mapping Creation

First, we'll define a very basic roles and permissions mapping. We'll do so using the internal data source.

1. Create a new internal data source \(see [here](data-sources/new-internal-data-source.md) for more instructions\)
2. Use the following json object:

```javascript
{
    "roles": {
        "admin": {
            "permissions": [
                "overview",
            ],
            "sub_roles": ["developer"]
        },
        "developer": {
            "permissions": [
                "overview.view"
            ],
            "sub_roles": []
        }
    },
    "users": {
        "alice": {
            "id": 1,
            "role": "admin"
        },
        "bob": {
            "id": 2,
            "role": "developer"
        }
    }
}
```

Looking closely in the object, we'll identify:

* There are 2 roles: `admin` and `developer`.
* There are 2 users: `alice` and `bob`.
* `Alice` is an `admin`, `bob` is a `developer`.
* Every `admin` is also a `developer` \(note the `sub_roles` field of the `admin` role\)
* We're using dot notation permissions, with hierarchy. `admin` has the `overview` permissions \(and everything that starts with `overview` while the `developer` role has only `overview.view` permission.

1. Save the internal data source with the name "roles2permissions"

### Policy Creation

Now that we have a data source that represents the users, the roles and their permissions, we can move forward to the policy creation phase.

1. Create a new policy
2. Add a new custom rule with the following code snippet:

```scala
# Use the data in hand to create a graph of the roles and the attached permissions
roles_graph[entity_name] = descendants {
    data.datasources.roles2permissions.roles[entity_name]
    descendants := data.datasources.roles2permissions.roles[entity_name].sub_roles
}

permissions_map[entity_name] = permissions {
    data.datasources.roles2permissions.roles[entity_name]
    reachable := graph.reachable(roles_graph, {entity_name})
    permissions := {item | reachable[k]; item := data.datasources.roles2permissions.roles[k].permissions[_]}
}

# Use the name of the user from the request and returns its role as given by the data
role_of_user := role {
    role := data.datasources.roles2permissions.users[input.user].role
}

# Returns true of all the required permissions are satisfied by the user's granted permissions
rbac {
    granted_permissions := { i | i := permissions_map[role_of_user][_]}
    required_permissions := { i | i := input.required_permissions[_]}
    some i,j
    startswith(required_permissions[i], granted_permissions[j])
}
```

1. Create a new empty rule that only checks for `rbac` to evaluate to true. In the management UI the rule will look like this:

![RBAC rule](https://files.readme.io/f46f474-emptry_rbac_rule.png)

So the generated code of it will look like this:

```scala
# RBAC
active[decision] {
    rule_type := "allow"
    rbac
    decision := {
        "result": rule_type,
        "message": ""
    }
}
```

Policy is ready, next - test the policy.

### Testing the Policy

One way to test the policy is to [deploy a PDP](policy-decision-points-pdp/creating-a-new-pdp-configuration.md) and querying it using cURL or straight from your application.  
Another option is to use build.security's policy evaluator.  
For the following input, where `alice` is trying to do `overview.edit`, the request will get allowed:

```javascript
{
  "user": "alice",
  "required_permissions": [
    "overview.edit"
    ]
}
```

But for this same request for `bob` \(who is a `developer`\) the request will get denied:

```javascript
{
  "user": "bob",
  "required_permissions": [
    "overview.edit"
    ]
}
```

