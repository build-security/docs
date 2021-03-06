# New PostgreSQL Data Source

PostgreSQL is a widely used relational database system that can be used as a data-source in _build.security._

You may run any query, from within the policy, to extract any data that is required for making an authorization decision.

**To define a PostgreSQL data source in the control plane:**

1. Click the **NEW DATA SOURCE** button on the data source screen. The New Data Source panel will open on the right.
2. In the **Name** field, enter the name of the new data source.
3. In the **Description** field, enter a description \(optional\).
4. In the **Type** area, select **PostgreSQL**.
5. In the **Host** field, enter either the IP address or the DNS of the data source.
6. In the **Port** field, enter the port of the data source through which communication with build.security will take place.
7. In the **Username** field, enter the username of the PostgreSQL user name.
8. In the **Password Environment Variable** field, enter PDP environment variable from which the database password will be retrieved. For security purposes, the data source password will be stored within the PDP as an environment variable. After creating the PostgreSQL data source, you will need to declare the environment variable when [deploying the PDP](../policy-decision-points-pdp/pdp-deployments/).
9. In the **Database Name** field, enter the name of the PostgreSQL database.
10. In the **Cache TTL** field, enter the amount of time the cache memory of queries retrieved from the databases to the PDP will be cached and available for the PDP. Acceptable values \(in seconds\) is 0-600.
11. Click **SAVE** to create the new data source.

The new PostreSQL data source will now appear in the list of existing data sources on the data source screen.

![New PostgreSQL data source](https://files.readme.io/ce23f99-new_postgres.PNG)

{% hint style="success" %}
For usage example, see [here](../../library/built-in-functions/build.query_raw/postgresql.md).
{% endhint %}

