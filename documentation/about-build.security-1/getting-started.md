# Architecture

build.security’s architecture can be divided into four major components:

* Policy Administration Point \(PAPs\)
* Policy Decision Points \(PDPs\)
* Policy Enforcement Points \(PEPs\)
* Policy Information Points \(PIPs\)

![build.security architecture](https://files.readme.io/4b01271-image.png)

### Policy Administration Point \(PAPs\)

**The Policy Administration Point \(PAP\)** also known as the build.security control plane, is where the you can:

* Author and publish new policies
* Manage and view existing policies
* Test policies with evaluation data
* View decision logs
* Configure system-wide and project-wide settings, integrations, and configuration
* Manage PDPs at scale
* Perform impact analysis on how policy items would impact the organization \(its identities, its resources, etc.\), if activated

The control plane is offered as a managed service in build.security’s cloud or in the customer’s private cloud. The control plane does not have access to the data plane and handles only configurations, policies, and meta-data.

![build.security control plane](https://files.readme.io/1ee5e3f-policy.PNG)

### Policy Decision Points \(PDP\)

**The Policy Decision Points \(PDP\)** are OPA-based docker containers that serve the purpose of getting a JSON request, running a policy on it along with the data at hand, and producing a JSON decision with sub-millisecond latency.  
The [PDPs](../../policy-decision-points-pdp/pdp-deployments/) can be deployed as sidecar containers or as a service, in the cloud or on-prem.  
The PDPs come with built-in connectors to a wide range of data sources, enabling the use of external information as part of the policy evaluation phase. To minimize latency and increase performance, an in-memory caching layer is also part of the PDP.

![Policy Decision Points in build.security](https://files.readme.io/41612c7-pdps.PNG)

### Policy Information Points \(PIP\)

**The Policy Information Points \(PIP\)** are any private/public data sources the operator can utilize in order to make better access control decisions. These might be \(but are not limited to\) ticketing systems, code repositories, relational databases, NoSQL databases, SaaS applications, HR applications, CRMs etc.

### Policy Enforcement Points \(PEP\)

**The Policy Enforcement Points \(PEP\)** are those who are responsible for enforcing the decision given by the PDPs. The[ enforcement points](../../pep-integrations.md) could be in the form of API gateways, reverse proxies, middlewares, SDKs, and more.

![Policy Enforcement Points integration options](https://files.readme.io/68ee5c3-pep.PNG)

