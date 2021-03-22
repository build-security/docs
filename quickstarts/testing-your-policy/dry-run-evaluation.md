# Dry Run Evaluation

### Introduction

The policy evaluation panel enables you to perform a dry-run of an authorization request on an active Policy Decision Point point at any time during policy authoring.

Using this feature you can reduce the policy authoring working time and approve your policy is tested according to your needs.

The simplicity of testing in one click aside of the policy rules will help understand each change you do on the policy immediately.

**So let's get started...**

{% hint style="warning" %}
#### **Active** PDP is required

The evaluation calculation is done on an active real PDP instance. You can [verify](../../policy-decision-points-pdp/) that you have an active instance, if not simply [deploy](../../policy-decision-points-pdp/creating-a-new-pdp-configuration.md) a new Decision point.
{% endhint %}

### Our Policy

We will use a simple basic policy which DENYs access by default and ALLOWs access to requests where `input.role == "admin"`

![Allow admins policy](https://files.readme.io/ccdf0f2-Screen_Shot_2021-03-05_at_2.18.31.png)

### Evaluating the Request

First, we will try evaluating Alice's request, `alice` is a regular `user` so according to our authorization policy her request is denied as we can see in the result below `"allow": false`

![Denied access example](https://files.readme.io/95699a5-Screen_Shot_2021-03-05_at_2.18.44.png)

And Bob's request, which is an `admin` - access is allowed.

![Allowed access example](https://files.readme.io/7239952-Screen_Shot_2021-03-05_at_2.19.05.png)

{% hint style="success" %}
#### Congratulations

First, for Bob who gains access, and for you- now you can go and use build.security's policy evaluator. If you want more information - feel free to contact us on our [support portal](https://build-security.atlassian.net/servicedesk/customer/portals)
{% endhint %}



