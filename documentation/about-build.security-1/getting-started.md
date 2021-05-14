# Architecture

build.security’s architecture can be divided into four major components:

* [Policy Administration Point \(PAPs\)](getting-started.md#policy-administration-point-paps)
* [Policy Decision Points \(PDPs\)](getting-started.md#policy-decision-points-pdp)
* [Policy Enforcement Points \(PEPs\)](getting-started.md#policy-enforcement-points-pep)
* [Policy Information Points \(PIPs\)](getting-started.md#policy-information-points-pip)

![build.security architecture](https://files.readme.io/4b01271-image.png)

### Policy Administration Point \(PAPs\)

**The Policy Administration Point \(PAP\)** also known as the build.security control plane, is where you can:

* Author and publish new policies \(leveraging git integration as source of truth for policies\)
* Manage and view existing policies
* Test policies with evaluation data
* View decision logs
* Configure system-wide and project-wide settings, integrations, and configurations
* Manage PDPs at scale
* Perform impact analysis on how policy items would impact the organization \(its identities, its resources, etc.\), if activated

The control plane is offered as a managed service in build.security’s cloud or in the customer’s private cloud. The control plane does not have access to the data plane and handles only configurations, policies, and meta-data.

![build.security control plane](https://files.readme.io/1ee5e3f-policy.PNG)

### Policy Decision Points \(PDP\)

**The Policy Decision Points \(PDP\)** are OPA-based docker containers that serve the purpose of getting a JSON request, running a policy on it along with the data at hand, and producing a JSON decision with sub-millisecond latency.  
The [PDPs](../policy-decision-points-pdp/pdp-deployments/) can be deployed as sidecar containers or as a service, in the cloud or on-prem.  
The PDPs come with built-in connectors to a wide range of data sources, enabling the use of external information as part of the policy evaluation phase. To minimize latency and increase performance, an in-memory caching layer is also part of the PDP.

![Policy Decision Points in build.security](https://files.readme.io/41612c7-pdps.PNG)

### Policy Information Points \(PIP\)

**The Policy Information Points \(PIP\)** are any private/public data sources the operator can utilize in order to make better access control decisions. These might be \(but are not limited to\) ticketing systems, code repositories, relational databases, NoSQL databases, SaaS applications, HR applications, CRMs etc.

### Policy Enforcement Points \(PEP\)

**The Policy Enforcement Points \(PEP\)** are those who are responsible for enforcing the decision given by the PDPs. The[ enforcement points]() could be in the form of API gateways, reverse proxies, middlewares, SDKs, and more.

![Policy Enforcement Points integration options](https://files.readme.io/68ee5c3-pep.PNG)

### Key Concepts

* **Data Driven**
  * PDPs are designed to be connected to any external data source, fetching real time information to make better authorization decisions. External datasource could be databases, HR applications, ticketing systems, billing applications and more
  * Using build.security's `tagging` mechanism, data \(and policies\) can be segregated and partitioned into the relevant PDPs, providing the necessary information to the right places \(and only the necessary information\)
* **Performance**
  *  build.security's PDPs are built on top of OPA, the de-facto policy engine that is very lightweight and performant. Check out our [performance benchmark](https://build.security/whitepaper-performance/).
  * The PDPs are stateless by design \(except for in-memory caching\) hence can be automatically scaled out as necessary.
  * The PDPs are equipped with in-memory caching mechanism, further improving performance when interacting with external data sources.
* **Policy-as-Code**
  * The underlying authorization policies are "as code". Specifically - [rego](https://www.openpolicyagent.org/docs/latest/policy-language/). All policies can synchronized with a git repository allowing proper audit, review and approval before rolled out to production. Furthermore, policies can be unit-tested, just like code, making sure edge cases are taken care of.
* **Decoupling policy from business logic**
  * Access policies tend to start small but grow big very fast
  * These policies are often "buried" within home-grown applications, right beside and in-between other business logic, making it hard to maintain and review when changes are needed.
  * It's best to decouple access policies from business logic, manage it centrally, but enforce it in a distributed manner.
* **Cloud native and open source**
  * Built on top of OPA, build.security's PDP can integrate into many [cloud native applications](https://www.openpolicyagent.org/docs/latest/ecosystem/)
  * All integrations can be managed and control from a single pane of glass.



