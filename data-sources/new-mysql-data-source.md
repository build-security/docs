# New MySQL Data Source

MySQL is a widely used open-source relational database system that can be used as a data-source in _build.security._

You may run any query, from within the policy, to extract any data that is required for making an authorization decision.

**To create a new MySQL data source in the control plane:**

1. Click the **NEW DATA SOURCE** button on the data-source screen. The New Data Source panel will open on the right.
2. In the **Name** field, enter the name of the new data-source.
3. In the **Description** field, enter a description \(optional\).
4. In the **Type** area, select **MySQL**.
5. In the **Host** field, enter either the IP address or the hostname of the data-source.
6. In the **Port** field, enter the port that the data-source exposes for accepting connections.
7. In the **Username** field, enter the username that should be used for authenticating the connection.
8. In the **Password Environment Variable** field, enter PDP environment variable from which the database password will be retrieved. For security purposes, the data-source password will be stored within the PDP as an environment variable. After creating the MySQL data-source, you will need to declare this variable when [deploying the PDP](../policy-decision-points-pdp/pdp-deployments.md).
9. In the **Database Name** field, enter the name of the MySQL database that should be used.
10. In the **Cache TTL** field, enter the amount of time that query results should be cached by the PDP. Acceptable values \(in seconds\) are 0-600.
11. Click **SAVE** to create the new data-source.

The new MySQL data-source will now appear in the list of existing data-sources on the data-source screen.

![New MySQL data source](https://files.readme.io/1c3c0a3-Screen_Shot_2021-03-08_at_11.47.34.png)

{% hint style="success" %}
For usage example, see [here](../library/built-in-functions/build.query_raw/mysql.md).
{% endhint %}

