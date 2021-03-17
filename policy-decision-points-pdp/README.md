# Policy Decision Points \(PDP\)

Policy Decision Points are responsible for making authorization decisions based on the organization's authorization policy. After evaluating the authorization request against the policies created within build.security, the PDP determines whether or not access to the resource will be allowed or denied.

Within the build.security project, you can manage multiple PDP configurations. Each PDP configuration defines all the necessary details to set and load a PDP in your organizational environment that will determine the authorization decision, which is then enforced by the Policy Enforcement Point \(PEP\), which is also integrated with the control plane.

When you open the PDP navigation option, all currently defined PDPs are listed in the table in the main display area.

For each PDP configuration, the following information is displayed:

| Field Name | Description |
| :--- | :--- |
| **Name** | Indicates the name of the PDP. Note that each name must be unique in the project. The name of the PDP does not have to be identical to the PDP in the organization. Within build.security, each PDP represents a pointer to the organization's PDP.  When you click on **&gt;** next to the name of a PDP, the view expands to offer additional details about the PDP, including information about the API key and deployment instructions \(as detailed below\). |
| **Creation Date \(UTC\)** | The date and time that the PDP was created. |
| **Last Update \(UTC\)** | The last time \(UTC\) the PDP was updated \(that the name or description was changed\). |
| **Actions** | There are three actions that can be performed for each PDP: - [Edit a PDP](https://docs.build.security/docs/edit-pdp-configuration-information) - [Delete a PDP](https://docs.build.security/docs/deleting-a-pdp-instance) |

### Available Actions

**On the Policy Decision Points screen, you can:**

* [Creating a new PDP configuration](https://docs.build.security/docs/define-new-pdp-configuration)
* [Generate API keys for your PDPs](https://docs.build.security/docs/generate-keys-for-a-pdp-instance)
* [Edit an Existing PDP](https://docs.build.security/docs/edit-pdp-configuration-information)
* [Delete a PDP](https://docs.build.security/docs/deleting-a-pdp-instance)

![Policy Decision Points screen](https://files.readme.io/10d5cca-pdp.PNG)

### PDP Expanded View

You can also access additional information about each PDP by clicking **&gt;**. The row expands to display the following information:

* API key
* Creation date and last update of the API key.
* Deployment instructions \(see [Deploying a build.security PDP](https://docs.build.security/docs/deploying-a-pdp)\).
* IP address \(the internal IP address of the machine running the configuration\).
* Status of the connection between the PDP and the build.security control plane \(green confirms communication between the two\).
* Last seen \(UTC time\).
* Policies: a list of policies that have been published to the PDP for evaluation of authorization requests.
* Remove from list option: deletes old records that are inactive. A new record will be added when the PDP authenticates with the control plane.

![Information displayed when expanding a PDP](https://files.readme.io/5cd6f8e-expanded_pdpconfig_line-blur.PNG)

### PDP Use Case Example

A docker running an OPA-based Policy Decision Point \(PDP\) in your cluster gets the authorization request from your API application \(PEP\). The PDP makes the authorization decisions according to the cached policy and specific configurations received from the control plane.

Upon making the decision, the organization's PDP returns the decision to build.security and sends its decision to the PEP, which is responsible for enforcing.

Following this, based on the configuration settings, the PDP sends the authorization decision to be logged in the decision log table.

