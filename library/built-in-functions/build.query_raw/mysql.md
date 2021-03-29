# MySQL

### Overview

This is a short example of how to use your MySQL data source as part of your authorization policy using build.security build-in function named `build.query_raw` and use the data retrieved from your MySQL within the authorization rules.

{% hint style="warning" %}
**Preconditions**

The datasource is available and [created](https://docs.build.security/docs/defining-a-new-data-source) within build.security control plane and you passed all relevant environment variables during the PDP [deployment/setup](doc:https://docs.build.security/docs/pdp-implementation).
{% endhint %}

### Build policy rules

1. Create or use an already existed policy.
2. In your policy screen, create a new policy item from the type "Custome code".
3. Copy and paste the following code snippet:

```scala
mysqldata := build.query_raw(data.datasources["mysql"], "SELECT * FROM employee WHERE age BETWEEN 25 to 45 ", [])
```

4. Change the variables according to your needs

* `mysqldata` - The variable that will contain the DB query result, you will use during the policy rules authoring.
* `mysql`: The data source name within your project.
* `SELECT * FROM employee WHERE age BETWEEN 25 to 45` - The query that the PDP will send to the data source in order to retrieve the data.

Another example that uses variables will look similar to this:

```scala
mysqldata := build.query_raw(data.datasources["mysql"], "SELECT * FROM users WHERE Name = ?", [input.user])
```

Once finished you can simply use the data in any other place in the policy by using the variable name- in our case `mysqldata`.

{% hint style="info" %}
**Supported PDP version** 

This built-in function supported from version V0.0.1 and above 
{% endhint %}

