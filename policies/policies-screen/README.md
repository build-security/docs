# Policies Screen

When you add a policy or click on an existing policy, the policies screen opens with an [additional toolbar](policy-toolbar.md) just below the main toolbar. Following is a quick introduction to the various parts of the policies screen.

{% hint style="info" %}
**Note**

To the right of the list of rules are two icons that open up the [Policy Code panel](../policy-code-panel.md) and the [Policy Evaluation Playground panel](../policy-evaluation-playground.md).
{% endhint %}

![](../../.gitbook/assets/new-policy.png)

Area

| Description | For more information |  |
| :--- | :--- | :--- |
| Policy Toolbar | Name and description of the policy and time it was last updated Policy type \(Deny, Allow\) Kebab \(three vertical black dots\) with cURL Example | See [Policy toolbar](policy-toolbar.md) |
| New Policy Item | Opens the new policy item wizard | See [Managing Policy Items](../policy-items/managing-policy-items.md) |
| Policy Items Table | Table listing all currently defined policy items including type, name, creating date, last update, status, up/down arrows to reorder the list of policy items and the Actions column with a kebab icon \(enabling you to delete the policy item\). | See [Policy Items](../policy-items/) |
| Policy Code Panel | The policy code panel offers you the ability to view and copy the compiled Rego code that is sent to your PDP for the current policy being displayed.   In the lower area of the Policy code tab, an error window will appear if there is a code error identified. The line where the error exists as well as a brief explanation about the error will appear as well. | See [Policy Code Panel](../policy-code-panel.md) |
| Policy Evaluation Playground | The policy evaluation playground enables the policy admin to validate changes that are made to the policy while the policy rule is still in Draft mode | See [Policy Evaluation Playground](../policy-evaluation-playground.md) |

