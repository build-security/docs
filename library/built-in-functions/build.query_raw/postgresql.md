# PostgreSQL

### Overview

This is a short example of how to use your PostgreSQL data source as part of your authorization policy using build.security built-in function named `build.query_raw` and use the data retrieved from your PostgreSQL within the authorization rules.

{% hint style="warning" %}
**Preconditions**

The data-source is available and has been [created](../../../data-sources/new-postgresql-data-source.md) in the build.security control-plane, and you have passed all relevant environment variables \(such as the connection password\) during the PDP [deployment/setup](../../../policy-decision-points-pdp/pdp-deployments.md).
{% endhint %}

### Build policy rules

1. Create or use an already exiting policy.
2. In your policy screen, create a NEW POLICY ITEM of type "Custom block".
3. Copy and paste the following code snippet:

Rego

```scala
emails := build.query_raw(data.datasources["MyPostgresDB"], "SELECT \"email\" FROM public.\"users\" where \"name\" = $1", [input.name])
```

4. Modify the variables according to your needs.

Let's review the arguments and variables in the previous example:

* `emails` - The variable that will contain the DB query result, you will use during the policy rules authoring.
* `MyPostgresDB`: The data source name within your project.
* `"SELECT \"email\" FROM public.\"users\" where \"name\" = $1"` - The query that the PDP will send to the data source in order to retrieve the data.
* `["input.name"]`: The parameter that will replace the "$1" variable within the query.

Once finished you can simply use the data elsewhere in the policy by using referring the variable name where the results has be set - in our case `emails`.

{% hint style="info" %}
**Supported PDP version** 

This built-in function supported from version V0.0.1 and above 
{% endhint %}

