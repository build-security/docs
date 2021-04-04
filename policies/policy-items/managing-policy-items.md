# Managing Policy Items

Policy items can be created by using the new policy item wizards. There are three types of policy items \(build.security predefined rules, custom blocks, empty rules\).

### Creating a New Policy Item

1. On the control plane menu, select the policy for which you wish to add a new policy item. The policies screen opens displaying all currently defined items for that policy.

![Existing policy items](https://files.readme.io/52f6ef6-policyitems.PNG)

Below the [policy toolbar](../policies-screen/policy-toolbar.md), click the **NEW POLICY ITEM** button. The New Policy Item panel opens on the right. Depending on the integration that was selected when you created the policy, you will have the option to select one of the following:

* A predefined rule from common build.security templates: The options for these common rules vary from integration to integration. You can use the scroll bar to scroll through the available options.
* Custom block option to create your own custom block using Rego language
* Empty rule to create your own rule using Rego language.

Select the desired option and click **ADD**.

A new Policy Item will be added to the table of existing items \(for more information, see [Policy Items](./). You can now edit the item by clicking on it. It will expand to display more information about the policy item. To learn more, see:

* [Predefined common rule example](predefined-rules-templates.md)
* [Custom rule example](custom-blocks.md)
* [Empty rule example](empty-rules.md)

If an error in code occurs while you are creating a policy item, the control plane will indicate this error with an error icon and a error window at the bottom of the policy code panel will appear. For more information see [Errors in Code](./#errors-in-policy-items).

### Deleting a Policy Item

**To delete a policy item:**

1. In the navigation panel, click **Policies** and locate the policy you wish to edit. The policies screen will open, showing all of the currently defined policy items for that policy.
2. In the policy items table, locate the policy item you wish to delete.
3. Click the kebab \(three vertical dots\) in the Actions column to the right.
4. Click **Delete**.
5. Click **Confirm** to verify that you wish to delete the policy item.

A confirmation message will appear indicating that the policy item was successfully deleted.

![Confirmation message](https://files.readme.io/7f1cb3b-confirmdelete.PNG)



