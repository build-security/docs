# Impact Analysis

One of the more unique features of the build.security platform is the ability to conduct a full impact analysis on your authorization policy BEFORE you apply the policy to your end-users.

Using this feature, you can quickly and confidently explore different policy strategies and track their respective impacts on production and real-time traffic without any of the inherent risks that a new policy might deliver to end-users.

In build.security, a policy is built with one or more items. Each item is given a status as it is created. By default, the initial status is **Inactive**. Once you have completed the task of creating the item and are ready to have it included in the policy decision process, you will likely change the status to **Active**. When the policy item's status is Active, it is part of the policy and part of the authorization decision returned by the PDP.

A third status option is Monitored. When combined with the [rule tracing](https://docs.build.security/docs/policy-rule-tracing) feature, you can perform extensive impact analysis evaluations on various potential policy adjustments without impacting your current authorization policy in any way.

### Monitored Status Enables Evaluating each Policy Item

All policy items with the status of Active are considered to be part of the full policy passed to the PDP to use in the decision-making process. When the authorization decision is made, it is logged to the build.security decision logs.

When you wish to first test how this policy item might change the authorization decision, you can create the policy item and apply a status of Monitored. This means that the policy item will be evaluated as part of the authorization request and a second decision will be logged to the decision log table. The decision will not be factored into the actual decision implemented by the Policy Enforcement Point, but the impact it would have had, had it been Active, is available as the Monitored Decision.

This second calculation is what the decision would be had that Monitored policy item been Active.

{% hint style="info" %}
**Note**

While the monitoring status means that the decision results will not impact on how the policy is currently applied, it can possibly impact on the overall performance.

For this reason, it is not recommended that you use the monitoring/impact analysis feature in production \(or for extended periods of time in production\) as this can impact on performance.
{% endhint %}

### Impact Analysis Example

Consider an organization that currently does not restrict weekend access to its communications servers by its users. The organization has a firm policy of discouraging employees from working overtime and weekends and is considering creating a policy to physically restrict access to the communications servers during downtime. The current authorization policy allows employees from all departments to have access after work hours and on weekends.

Before implementing such a policy, the organization would like to have a better sense of who would be impacted, who is accessing the servers, etc. What would happen if they allowed some departments but restricted others?

To evaluate how this change might affect its organization, four new rules would be added to identify users according to their department affiliation.

In this example, different users are identified:

* Current rule: All employees have access to the communications server - Active rule
* New rule: **Dev** department \(identified based on department\) - Monitored rule
* New rule: **Finance,** **Marketing**, **Support** departments - Monitored rule
* New rule: **Trainees** \(employees during the first 12 months of employment\) - Monitored rule
* New rule: **Clerical employees** \(working in all departments, identified based on Job title\) - Monitored rule

While the current policy allows all employees to have full access, the updated version of the policy will have some new rules that will initially be given a status of Monitored to enable the organization to evaluate how this policy would impact billable overtime hours, system resources, etc.

The new rules will include:

| Rule Name | Description |
| :--- | :--- |
| DEV Access | Users from the Dev department have full access, without restrictions after work hours and on weekends. |
| Finance, Marketing, Support | Users from these departments will have access until 10:00 p.m. and no access on weekends. |
| Trainee-Clerical | Users with Job Titles of Trainee and Clerical will have access until 6:00 p.m. on weekdays and no access on weekends. |

After running these new rules as monitored, the authorization decision would be as follows:

| Request Time | Active Policy | Monitored Policy |
| :--- | :--- | :--- |
| 4:00 p.m. | All have access | All have access |
| 8:00 p.m. | All have access | _Dev has access_ Finance, Marketing, Support have access \* Trainee-Clerical denied |
| Sunday | All have access | _Dev has access_ Finance, Marketing, Support denied \* Trainee-Clerical denied |

The decision log table would provide invaluable information to enable the organization to understand where these requests were coming from, how many there were, and whether it would be beneficial to implement these rules in real-time.

