# Data Sources

A data source is defined as any source \(for example, internal or external database\) for information that supplies the Policy Decision Point with the relevant data in real-time according to the policy rules that you have defined.

{% hint style="info" %}
**Note**

You should define your data sources before configuring your PDPs, if possible.
{% endhint %}

In build.security, you can easily define integrations with a variety of sources that are involved in evaluating an authorization request. These include

* Organizational databases
* Management applications that handle your organization's information

On the control plane menu, you can access a list of all existing data sources by selecting the data source option. As you click on an existing data source, the main display window will show the description and type on the right, as well as current settings or relevant data. Depending on the type of data source, customized information will be displayed below the description/type area.

**Our Support Teams are available to assist you in defining your authorization management needs and requirements in build.security. Contact us at support@build.security**

{% hint style="success" %}
Currently, build.security supports the following:

**Databases**:

* PostgreSQL
* Elasticsearch
* DynamoDB
* MySQL

**Internal JSON files**

build.security offers the ability to create your own internal data source file and then build the JSON file according to your needs within the control plane.
{% endhint %}

{% hint style="info" %}
**Note**

Each data source within a project must be given a unique name.
{% endhint %}

![Data sources screen](https://files.readme.io/b0453b3-ds2.png)



