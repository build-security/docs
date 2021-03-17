# New MySQL Data Source

MySQL is a widely used open source object-relational database system that can be connecting to build.security, to enable you can run anything from simple to complex queries \(authorization requests\) against the data in the MySQL database. Based on the policies defined in build.security and the information provided by the data source, the PDP can determine the authorization decision.

**To create a MySQL data source in the control plane:**

1. Click the **NEW DATA SOURCE** button on the data source screen. The New Data Source panel will open on the right.
2. In the **Name** field, enter the name of the new data source.
3. In the **Description** field, enter a description \(optional\).
4. In the **Type** area, select **MySQL**.
5. In the **Host** field, enter either the IP address or the DNS of the data source.
6. In the **Port** field, enter the port of the data source through which communication with build.security will take place.
7. In the **Username** field, enter the username of the MySQL user name.
8. In the **Password Environment Variable** field, enter PDP environment variable from which the database password will be retrieved. For security purposes, the data source password will be stored within the PDP as an environment variable. After creating the MySQL data source, you will need to declare this variable to [deploy the PDP](https://docs.build.security/docs/deploying-a-pdp).
9. In the **Database Name** field, enter the name of the MySQL database.
10. In the **Cache TTL** field, enter the amount of time the cache memory of queries retrieved from the databases to the PDP will be cached and available for the PDP. Acceptable values \(in seconds\) is 0-600.
11. Click **SAVE** to create the new data source.

The new MySQL data source will now appear in the list of existing data sources on the data source screen.

![New MySQL data source](https://files.readme.io/1c3c0a3-Screen_Shot_2021-03-08_at_11.47.34.png)



