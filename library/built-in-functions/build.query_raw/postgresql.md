# PostgreSQL

### Overview

This is a short example of how to use your PostgreSQL data source as part of your authorization policy using build.security built-in function named `build.query_raw` and use the data retrieved from your PostgreSQL within the authorization rules.

{% hint style="warning" %}
**Preconditions**

The datasource is available and [created](https://docs.build.security/docs/defining-a-new-data-source) within build.security control plane and you passed all relevant environment variables during the PDP [deployment/setup](doc:https://docs.build.security/docs/pdp-implementation).
{% endhint %}

### Build policy rules

1. Create or use an already existed policy.
2. In your policy screen, create a new policy item that is "Custom code" type.
3. Copy and paste the following code snippet:

Rego

```scala
emails := build.query_raw(data.datasources["MyPostgresDB"], "SELECT \"email\" FROM public.\"users\" where \"name\" = $1", [input.name])
```

4.Change the variables according to your needs

* `emails` - The variable that will contain the DB query result, you will use during the policy rules authoring.
* `MyPostgresDB`: The data source name within your project.
* `"SELECT \"email\" FROM public.\"users\" where \"name\" = $1"` - The query that the PDP will send to the data source in order to retrieve the data.
* `["input.name"]`: The parameter that will replace the "$1" variable within the query.

Once finished you can simply use the data in any other place in the policy by using the variable name- in our case `emails`.

{% hint style="info" %}
**Supported PDP version** 

This built-in function supported from version V0.0.1 and above 
{% endhint %}

