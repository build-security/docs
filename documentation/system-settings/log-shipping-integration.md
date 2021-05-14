# Log Shipping Integration



Using build.security's log shipping feature, you can automatically send decision log backups from the control plane to one or more databases within your organization. The first step in enabling this process is to define the integration between build.security and the internal database where you wish to collect the build.security log results.

Once you have created the integration, you can then assign whether or not log shipping should be enabled on a project-by-project basis.

### Creating a Log Shipping Integration

**To create a log shipping integration:**

1. On the System Settings option, select **Log Shipping**.
2. Click **NEW INTEGRATION**. The New Log Shipping panel will open.
3. In the **Name** field, enter the name of the new integration.
4. In the **Description** field, enter a description \(optional\).
5. In the **API Key field**, enter the API key that will enable communication between build.security and the Datadog implementation in your organization.
6. Click **Save** to create the integration.

{% hint style="info" %}
**Note**

Once you have created at least one log shipping integration, you can apply log shipping to your project in the [Project Settings screen](../projects/project-selection-screen.md).
{% endhint %}

![New log shipping integration](https://files.readme.io/7104a4f-new_log_shipping_integration.PNG)

### Deleting a Log Shipping Integration

Before you can delete a log shipping integration from the build.security control plane, you must first remove any connections you have created between that integration and any projects you have configured to use it \(see [Disabling Log Shipping](../project-settings/log-shipping.md) for more information\). If you do not first remove this connection, the following error message will appear:

![Error message](https://files.readme.io/94500e7-lserror.PNG)

**To delete a log shipping integration:**

1. On the System Settings screen, select **Log Shipping**.
2. Locate the integration you wish to delete and press the kebab \(three vertical dots\) on the right side.
3. Select **Delete** and then **Confirm**.

The integration is removed. Note that if you wish to enable this integration again, you will have to recreate it, including entering the API key again.

![Removing a log shipping integration](https://files.readme.io/e0b1cff-removinglsintegration.PNG)



