# Policy Item Status



Each policy item is assigned a status that identifies what affect it should have within the PDP's evaluation process. build.security's predefined rules and empty rules that you create can have one of three Statuses at any given time.

![Policy item statuses](https://files.readme.io/af8f045-rule_statuses2.PNG)

Custom blocks can have a status of Active or Inactive only.

| Status | Description | Color Indicator |
| :--- | :--- | :--- |
| **Active** | Each authorization request will be evaluated against this policy item as part of the authorization decision.  Also, when considered in the authorization decision, results of this policy item will be logged in the decision log table. | Blue |
| **Inactive** | The policy item will not be considered when an authorization decision is determined.  Therefore, the authorization result will not be affected by this policy item. | Grey |
| **Monitored** | The policy item is part of the policy and for each rule \(predefined or empty rule that you created\), it is possible to see what the outcome would be if the rule was active.  The monitored status enables you to evaluate what impact a rule would have on its authorization decisions before deciding whether to activate the rule.  Altough a monitored rule is NOT part of the actual authorization decision, it will be logged in the decision log table in the [Evaluation area](https://docs.build.security/docs/decision-log-filters2#rule-evaluation-area) so you can see what impact the rule would have had, if the rule had been activated.  Note that only build.security common rules and empty rules that you create can be given a status of monitored.  For more information, see [Impact Analysis.](https://docs.build.security/docs/impact-analysis-1) | Orange |

### Assigning a Policy Item Status

When you first create a policy item, it is given the status of Active automatically. For predefined rules and rules you created using the empty rules option, you can select from Active, Inactive, or Monitored. For custom rules, you can select from Active or Inactive..

To update the policy so that the PDP will consider the changes that you made, you will need to publish the policy. See [Publish Project Configuration](https://docs.build.security/docs/policy-deployment), for more details.

**To assign or change the status of a policy item:**

1. Navigate to the policy and policy item \(common rule or empty rule that you created\) that you wish to modify \(or assign\).
2. In the Status column of the policy item, press the down arrow. The display will expand to show you available options.
3. Choose the appropriate option. Note that when you select the option, it will then appear in the Status column and the Last Updated column will update as well.
4. It is important to publish this status change to the PDP if you want this status to be considered during the evaluation and authorization decision process.

