# Policies Screen

When you add a policy or click on an existing one, the policies screen opens with an [additional toolbar](https://docs.build.security/docs/policy-toolbar) just below the main toolbar. Following is a quick introduction to the various parts of the policies screen.

{% hint style="info" %}
**Note**

To the right of the list of rules are two icons that open up the [Policy Code panel](https://docs.build.security/docs/policy-code-panel) and the [Policy Evaluation Playground panel](https://docs.build.security/docs/policy-evaluation-playground).
{% endhint %}



![Policies screen](https://files.readme.io/0aee74f-mainpolicy.PNG)

Area

| Description | For more information |  |
| :--- | :--- | :--- |
| Policy Toolbar | Name and description of the policy and time it was last updated Policy type \(Deny, Allow\) Version and policy status Mark as Ready button Create new draft button Kebab \(three vertical black dots\) with cURL Example | See [Policy toolbar](https://docs.build.security/docs/policy-toolbar) |
| New Policy Item | Opens the new policy item wizard | See [Managing Policy Items](https://docs.build.security/docs/policy-rules) |
| Policy Items | Table of currently defined policy items including type, name, status and more. | See [Policy Items](https://docs.build.security/docs/policy-items) |
| Policy Code Panel | The policy code panel offers you the ability to view and copy the compiled Rego code that is sent to your PDP for the current policy being displayed.  In the lower area of the Policy code tab, an error window will appear if there is a code error identified. The line where the error exists as well as a brief explanation about the error will appear as well. | See [Policy Code Panel](https://docs.build.security/docs/policy-code-panel) |
| Policy Evaluation Playground | The policy evaluation playground enables the policy admin to validate changes that are made to the policy while the policy rule is still in Draft mode | See [Policy Evaluation Playground](https://docs.build.security/docs/policy-evaluation-playground) |

