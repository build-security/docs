# Log Shipping

Using build.security's log shipping feature, you can automatically send decision log backups from the control plane to one or more databases within your organization. Typically, organizations use log shipping to enable them to maintain one unified logging infrastructure. Implementing log shipping can be done easily and quickly by:

1. Creating a [log shipping integration](https://docs.build.security/docs/log-shipping)
2. Enabling the log shipping integration on a project-by-project basis.

### Enabling a Log Shipping Integration

**To enable a log shipping integration:**

1. In the Project Settings screen, select **Log Shipping**.
2. In the **Integrations** box, select the log shipping integration you wish to apply to the current project.
3. Click **UPDATE**. Log shipping is now enabled for this project and all decision log entries for this project will now be shipped according to the details defined for the selected integration.

![Selecting a log shipping integration](https://files.readme.io/d609cdd-logshipping.PNG)

### Disabling a Log Shipping Integration

If you wish to stop log shipping via a specific integration, on the Project Settings screen:

1. Click **Log Shipping**.
2. In the Integrations box, identify the integration you wish to disable and click the **X** beside that integration.

![](https://files.readme.io/6db2848-logshippingdisable.PNG)

The integration will be removed from the current project.

{% hint style="info" %}
**Note**

Removing this integration from the current project will not have any affect on that integration in relation to any other project.

Also, before deleting the integration entirely from the build.security control plane, the integration must be disabled in all projects with which it was previously integrated.
{% endhint %}

