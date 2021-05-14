# Decision Details

For each authorization decision reported back to build.security, an entry is logged to the decision logs table. Although the basic details of the decision are visible in the unexpanded view of the table, additional, more in-depth details can be viewed by expanded any line in the [decision logs table](./) to show more about each decision.

### Expanded Decision Details View

These details include information elements in the internal processes needed to evaluate and reach a decision. The expanded view is divided into the following areas:

| Area | Description |
| :--- | :--- |
| Decision ID | A unique identifier identifying the decision. Use the Copy to clipboard icon to copy the ID as needed. |
| Metrics | Includes the duration for each of the following:  _Input parse_ Query compile _Query evaluation_ Query parse _Module parse_ Module compile \* Request process |
| Input syntax | Input code |
| Result syntax | Full result returned |
| Rule evaluation | A rule-by-rule display of the authorization decision as it was sent to the PEP \(Decision\) and what the decision would be when the monitored policy item was considered \(Monitored Decision\). |

{% hint style="info" %}
**Note**

The rule evaluation section will only be displayed when a rule's status is "monitored" and rule tracing is enabled.
{% endhint %}

### Rule Evaluation Area

Under the headings of ALLOW or DENY, relevant rules of the policy are listed and the decision for each policy item appears to the right. Each of the listed items are color-coded based on their status \(blue=active; orange-monitored; gray=inactive\). Finally, at the bottom of the Rule Evaluation is the authorization decisions that were reached by the PDP \(the Decision and the Monitored Decision\).

![Decision details](https://files.readme.io/e0869bd-expandmetricsdecisionlog.PNG)



