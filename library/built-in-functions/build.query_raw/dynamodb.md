# DynamoDB

### Overview

This is a short example of how to use your DynamoDB data source as part of your authorization policy using build.security built-in function named `build.query_raw` and use the data retrieved from your DynamoDB within the authorization rules.

{% hint style="warning" %}
**Preconditions**

The data-source is available and has been [created](../../../documentation/data-sources/new-dynamodb-data-source.md) in the build.security control-plane, and you have passed all relevant environment variables \(such as the connection password\) during the PDP [deployment/setup](../../../documentation/policy-decision-points-pdp/pdp-deployments/).
{% endhint %}

### Build policy rules

1. Create or use an already exiting policy.
2. In your policy screen, create a NEW POLICY ITEM of type "Custom block".
3. Copy and paste the following code snippet:

```scala
moviesdata := build.query_raw(data.datasources["MyDynamo"], "SELECT * FROM imdb WHERE titleType = ?", ["movie"])
```

4. Modify the variables according to your needs.

Let's review the arguments and variables in the previous example:

* `moviesdata` - The variable that will contain the DB query result, you will use during the policy rules authoring.
* `MyDynamo`: The data-source name within your project.
* `"SELECT * FROM imdb WHERE titleType = ?"` - The [PartiQL query](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/ql-reference.html) that the PDP will send to the data-source in order to retrieve the data.
* `["movie"]`: The parameter that will replace the "?" variable within the query.

Once finished you can simply use the data elsewhere in the policy by using referring the variable name where the results has be set - in our case `moviesdata`.

{% hint style="info" %}
**Supported PDP version** 

This built-in function supported from version V0.1.16 and above 
{% endhint %}

\*\*\*\*



