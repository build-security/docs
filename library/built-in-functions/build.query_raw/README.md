# build.query\_raw

### Function Description

`build.query_raw` is one of build.security built-in function to query [Data Sources](https://docs.build.security/docs/data-sources-1) as part of the policy evaluation process.

{% hint style="warning" %}
**Preconditions**

The datasource is available and [created](https://docs.build.security/docs/defining-a-new-data-source) within build.security control plane and you passed all relevant environment variables during the PDP initialization.
{% endhint %}



### Function format

`build.query_raw(data_source, query_string, parameters)`  
**Parameters:**  


* `data_source`: identifier of the data source - use the Datasource name within your project.
* `query string`: string. The SQL/PartiQL query string is applicable for the specific data source.
* `query params`: Array of objects. Optional parameters for the command.

{% code title="build.query\_rew" %}
```sql
user := build.query_raw(data.datasources["my_datasource"],
  "SELECT * FROM users WHERE userId = ?", [input.userId])
```
{% endcode %}

### Function Usage Example

In the following section you will be able to find useful examples around how to use build.query\_raw built-in function according to the database you want to query :

1. [DynamoDB](dynamodb.md)
2. [MySQL](mysql.md)
3. [Elasticsearch](elasticsearch.md)
4. [PostgreSQL](postgresql.md)



