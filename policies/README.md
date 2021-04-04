# Policies

An organization's policies determine what permissions and restrictions it wants to place on its users as they relate to accessing resources. A policy in build.security contains one or more [policy items](policy-items/) \(predefined rules, empty rules or custom blocks\) that combine to define the organization's authorization policy.

Before creating a policy, it is helpful to configure some of the elements that are likely to be used in the policy. For example, you may want a policy to be applied to specific users. This could be all employees from a department within your organization, all visitors that try to access an organizational resource on specific days or during certain hours. Your policy could use IP addresses to determine access rights, or verify accessibility based on being part of a user list. In some cases, the policy will have to point to this information in your database. To enable build.security to do this, you will want to define at least one [data source](../data-sources/).

Once the policy is defined, you will want build.security to connect to your organization's Policy Decision Points \(PDPs\) and Policy Enforcement Points \(PEPS\), so integration with these must be configured in build.security as well \(see [Creating a New PDP Configuration](../policy-decision-points-pdp/creating-a-new-pdp-configuration.md) and [PEP Integrations](../pep-integrations.md)\).

To help you quickly build your policies, each time you create a policy, you can use predefined common rules that can be included in a policy to define or customize what you wish to implement in your organization.

At any point, you can edit your policies to adapt to any changes you need to make. You can define the policies by creating the rules completely on your own, or use the common rules as a starting point.

### Understanding Policy Components

Before beginning, you should define what you want to accomplish. Review the resources you have and the identities who need to be granted \(or restricted\) access. Let's start by defining some of the elements of a policy:

* A policy relates to a **resource**. A resource can represent an application \(for example, an online banking application\), a database, a server, hardware device accessed through an online application, software applications, digital assets, etc.
* **Identities** are granted or denied access to a resource. Identities can be real users such as employees, web-based members or visitors, 3rd party services etc.
* A policy can factor in data from **data sources** defined and integrated with build.security to define identity attributes \(for example, a policy might allocate resource access based on an employee's department, job title, location, etc.\)
* Once defined, a policy is published to the **PDPs**. Although there can only be one active version of a policy at any given time, previous versions are archived \(and can be restored\), and draft versions are saved, assigned version numbers, and can be activated at any time.

When an authorization request is received \(for example: can this user be granted access to the QA department server?\), the PDP evaluates the request based on the latest information provided to it by build.security. This information, known as the bundle, will include the latest policy version, any changes made to data sources, etc.\). The PDP will then evaluate the request on the basis of the policy and information, and determine whether the authorization request should be allowed or denied.

### Available Actions

In the Policies area of the navigation panel, you can:

* [Create a policy](creating-a-new-policy.md)
* [Edit an existing policy](editing-policy-settings.md)
* [Delete a policy](deleting-a-policy.md)
* [Managing policy items](policy-items/managing-policy-items.md)
* [Publish a policy](../projects/publish-project-configuration.md)

![Policy screen](https://files.readme.io/4bc2597-policy2.PNG)



