# Getting Started

The control plane offers a user-friendly authorization management interface to the build.security platform that dramatically simplifies the process of building and managing your organization's authorization policies. build.security significantly reduces development time and allows organizations to create authorization policies without writing a single line of code. Once created, you can access decision logs that enable you to evaluate and fine-tune your authorization policies, even perform [test your policy](../policies/policy-testing/) in a variety of ways prior to enabling a policy change.

### Basic build.security Tasks

The build.security workflow is based on a few basic steps including:

### Configuration

After you [log into the platform](../logging-in/logging-in-1.md), you will need to configure some basic elements in the build.security interface, including:

* [Selecting or creating a project](../projects/project-selection-screen.md)
* [Defining one or more data sources](../data-sources/)
* [Defining one or more Policy Decision Points \(PDPs\)](../policy-decision-points-pdp/creating-a-new-pdp-configuration.md)
* [Enabling decision logs](../project-settings/decision-log-settings.md) \(by default, already enabled\) 
* [Enabling log shipping ](../project-settings/log-shipping.md#enabling-a-log-shipping-integration)\(by default, disabled\)
* [Enabling Git integration](../project-settings/git-integration-settings.md) \(by default, disabled\)



{% hint style="info" %}
In certain scenarios, upon logging in, a user might automatically enter directly into the [control plane ](control-plane-overview.md)of a specific project and not have an option to create. select or move between projects.
{% endhint %}

### Policy Management

* Defining and publishing a policy which expresses your authorization requirements for allowing or denying your users access to your resources
* [Creating an authorization policy](../policies/creating-a-new-policy.md)
* [Publishing an authorization policy](../projects/publish-project-configuration.md)

At any time, you may decide to add additional policies or change existing ones. Finally, build.security enables you to log authorization decisions, centrally collect them and then view / forward them.

In addition, using the `Monitored` status option for a policy item, you can [analyze the impact](../impact-analysis/) that a policy item would have on the authorization decision, without actually activating it.

