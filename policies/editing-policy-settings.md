# Editing Policy Settings



In the lower part of the control plane's navigation panel, you can view a list of all currently defined policies. When you click on a policy name, the main display area will offer you a complete view of the policy including a list of policy items, the type of policy it is \(deny or allow\), etc. In addition to changing the policy items, you can also edit settings related to the policy, as detailed below.

**To edit a policy:**

1. Locate the policy you wish to edit and click the wrench icon beside it. The Policy Settings page opens with all currently defined values displayed.

![Edit policy settings option](https://files.readme.io/922a14f-editpolicy.PNG)

You can edit the Policy Name and/or the Policy Description fields.

1. If you click the **&gt;** icon beside **Advanced**, you can also edit the Decision Path and/or the Package Name fields, as follows:

* **Decision Path**: defines the JSON path separating the decision results from the full results returned for each decision. This is the decision that will be reflected in the decision log table \(for example: deny, allow\).
* **Package name**: the name of the policy that should be used when querying the PDP for an authorization decision.

{% hint style="success" %}
For example, if package name is `envoy.auth` as shows in the example below, in order to query this policy in runtime, the endpoint shall be: `http://<hostname>:8181/v1/data/envoy/authz`
{% endhint %}

As all policies in the project are sent to all the PDPs in the same project, two different policies cannot share the same package name.

{% hint style="info" %}
**Note**

You cannot change the integration type that was set when the policy was created. You can delete the current policy and create another one as needed.
{% endhint %}

When you finish editing the policy, click **Save** \(or Cancel to close the screen without saving your changes\).

![Policy settings screen](https://files.readme.io/001ceb2-policysettings.PNG)



