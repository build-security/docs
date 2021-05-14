# Deleting a Data Source

You can delete a data source at any time by clicking on the three vertical dots on beside the name of the data source you wish to delete. You can then click **Delete**.

You will be asked to confirm that you wish to take this action. Click **Confirm** to delete the PDP, or **Cancel** to close the **Confirm** box without deleting the data source.

![Delete data source](https://files.readme.io/8215f3e-editds.PNG)

{% hint style="info" %}
**Important**

If you delete a data source that is responsible for supplying data that is used in determining an authorization decision, build.security will no longer be able to consider that data once the data source has been deleted.

Therefore, if you created a policy that relies on pulling information from a data source, before deleting that data source, verify that you have removed that dependency within the policy.
{% endhint %}

