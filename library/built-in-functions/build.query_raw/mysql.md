# MySQL

### Overview

This is a short example of how to use your MySQL data-source as part of your authorization policy using build.security built-in function named `build.query_raw` and use the data retrieved from your MySQL within the authorization rules.

{% hint style="warning" %}
**Preconditions**

The data-source is available and has been [created](https://docs.build.security/data-sources/new-mysql-data-source) in the build.security control-plane, and you have passed all relevant environment variables (such as the connection password) during the PDP [deployment/setup](https://docs.build.security/policy-decision-points-pdp).
{% endhint %}

### Build policy rules

1. Create or use an already exiting policy.
2. In your policy screen, create a NEW POLICY ITEM of type "Custom block".
3. Copy and paste the following code snippet:

```scala
mysqldata := build.query_raw(data.datasources["mysql"], "SELECT * FROM employee WHERE age BETWEEN 25 to 45 ", [])
```

4. Modify the variables according to your needs

Let's review the arguments and variables in the previous example:
* `mysqldata` - The variable that will contain the DB query result, you will use during the policy rules authoring.
* `mysql`: The data-source name within your project.
* `SELECT * FROM employee WHERE age BETWEEN 25 to 45` - The query that the PDP will send to the data-source in order to retrieve the data.

Another example that uses variables will look similar to this:

```scala
mysqldata := build.query_raw(data.datasources["mysql"], "SELECT * FROM users WHERE Name = ?", [input.user])
```

Once finished you can simply use the data elsewhere in the policy by using referring the variable name where the results has be set - in our case `mysqldata`.

{% hint style="info" %}
**Supported PDP version** 

This built-in function supported from version V0.1.16 and above 
{% endhint %}

