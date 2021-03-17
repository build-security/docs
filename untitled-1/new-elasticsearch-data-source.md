# New Elasticsearch Data Source

Elasticsearch is an open source solution built on Apache Lucene. By connecting the Elasticsearch data source to build.security, you can run anything from simple to complex queries against the data in Elasticsearch that will be used by the PDP to determine the authorization decision.

**To create an Elasticsearch data source in the control plane:**

1. Click the **NEW DATA SOURCE** button on the data source screen. The New Data Source panel will open on the right.
2. In the **Name** field, enter the name of the new data source.
3. In the **Description** field, enter a description \(optional\).
4. In the **Type** area, select **Elasticsearch**.
5. In the **Scheme** field, select either https or http.
6. In the **Host** field, enter either the IP address or the DNS of the data source.
7. In the **Port** field, enter the port of the data source through which communication with build.security will take place.
8. In the **Cache TTL** field, enter the amount of time the cache memory of queries retrieved from the databases to the PDP will be cached and available for the PDP. Acceptable values \(in seconds\) is 0-600.
9. Click **SAVE** to create the new data source.

The new Elasticsearch data source will now appear in the list of existing data sources on the data source screen.

![New Elasticsearch data source](https://files.readme.io/58c4baa-new_elastic.PNG)



