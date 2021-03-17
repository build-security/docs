# Deleting a PDP

When you delete a PDP from build.security's control plane, build.security will no longer be able to communicate with the organization's Policy Decision Point represented by the deleted item. This means that the PDP will not be able to request bundle updates from build.security. It also means that any decisions made by the PDP will not be logged in the control plane's decision logs.

{% hint style="info" %}
**Important**

Before you delete a PDP or the API key defined in the Keys Management section below the PDP, verify that there is no dependency defined between build.security policies and this PDP.

If the PDP \(or the API key\) is deleted while this dependency exists, the next time the PDP attempts to pull a bundle, build.security will not be able to authenticate the request and therefore will not be able to send the bundle to the PDP.
{% endhint %}

**To delete a PDP:**

1. Open the Policy Decision Points screen on the control plane.
2. Locate the PDP you wish to delete.
3. Click the kebab \(three vertical dots\) at the end of the PDP entry.
4. From the drop-down menu, click **Delete**. You will be asked to confirm that you wish to take this action.
5. Click **Confirm** to delete the PDP.

![Editing/deleting the PDP](https://files.readme.io/6515537-pdpeditdelete.PNG)



