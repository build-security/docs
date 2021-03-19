# Publish Project Configuration

Policies are passed at run time to your Policy Decision Points \(PDPs\). Therefore, it is important that the PDPs have access to the most recently updated configuration and policies in your organization. The process of ensuring that the most recent configuration and policies are considered is called publishing and is initiated when you press the Publish button on the build.security toolbar.

![Publish button](https://files.readme.io/75c526c-publish.PNG)

When changes are made to your data sources \(creating new ones, modifying configuration settings, etc.\) and/or policies, these changes need to be published to the PDP. Once published, these changes are collected in a bundle that is sent from build.security to the PDP each time the PDP sends a request for an updated bundle.

{% hint style="info" %}
**Note**

Bundle polling settings are configured by clicking the PDP Settings option on the [Project Settings screen](../project-settings/pdp-settings.md).
{% endhint %}

The bundle includes:

* All the updated policies within the project at the moment.
* Data source details.

### Publish to PDPs

**To publish to the PDPs:**

1. Click the **PUBLISH** button on the control plane toolbar. The Publish Project Configurations panel opens, displaying a list of the latest updates to all PDPS in the project, any changes made to data sources, and any version changes to policies. In the lower left of the panel, the last date and time the project was published is listed.

![Publish project configurations panel](https://files.readme.io/5545181-publishproject.PNG)

To complete the publish process, click **Publish**.

![Publish to PDP icon](https://files.readme.io/79ea6a0-toolbar.PNG)

{% hint style="info" %}
**Note**

You can click the **PUBLISH** button at any time. When you do, the Publish Project Configurations panel appears. If there are no updates, the Publish Project Configurations panel will indicate that there have been no updates. You can press **Cancel** to return to the previous screen.
{% endhint %}

Each time you click Publish, you will receive a confirmation message as soon as it is completed successfully. Typically, this is only a few seconds, at most.

![Publish success message](https://files.readme.io/d4f500e-pdppublishsucess.PNG)

{% hint style="success" %}
Comming Soon - intgrate your git repositry and commit your policies for continuase deplyomet  
{% endhint %}

