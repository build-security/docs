# Rule Tracing

Rule tracing is an important feature in build.security. Just as the decision log enables you to evaluate how authorization decisions are being implemented in your organization, rule tracing enables you to focus in more depth on how each policy item impacts the authorization response.

The [decision log ](../decision-logs/)screen offers information about each decision as a whole, including the overall decision that was determined by the PDP and sent to the PEP for enforcement.

However, it is possible, with rule tracing, to drill down and study not only the authorization decision as a whole, but how individual items within the policy helped determine the authorization decision. For example, consider a policy that contains three elements to it. Two are given the status of Active while one is given a "Monitored" status.

Rule tracing means that two authorization decisions will be returned.

### Actual Decision

The first decision \(shown as Decision in the decision log's rule evaluation area\) is the actual decision returned by the PDP. In this decision, the impact of the third policy item with the Monitored status was not considered. In a real-life scenario, it has no impact on the authorization decision and whether or not an identity is allowed or denied access to the organization's resource.

### Monitored Decision

The second decision \(shown as Monitored Decision in the decision log's rule evaluation area\) is the authorization decision that would have been returned, if that third policy item \(the one with the Monitored status\) had been included in the evaluation process.

When rule tracing is enabled in the [project settings screen](../project-settings/), in addition to the metrics, input and result areas in the expanded view, an additional area also appears. This is the rule evaluation section of the expanded decision details view.

Perhaps even more impressive is that this evaluation can be done **BEFORE** implementing a rule in real-time. Instead, by giving a rule a status of **Monitored**, you can analyze the impact a rule will have on an authorization request without actually activating the rule.

{% hint style="info" %}
**Note**

Processing performance can be slower when rule tracing is enabled.
{% endhint %}

### Enabling Rule Tracing

* On the Project Settings screen, select the Decision Log option and then enable the Rule tracing option.

![Project Settings - rule tracing option](https://files.readme.io/27acc98-ruletracingprojsettings.PNG)



