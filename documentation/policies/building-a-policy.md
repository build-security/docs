# Building a Policy

Let's deep dive into how to author an authorization policy that fits your use case. First, we'll break down the general authorization problem, and then we will break down all the authorization decision components. Using this methodology you will be able to see the logic behind your use case and implement policy in a fast and secure way.

## General Authorization Problem

The example we are using is intentionally simplified to allow for greater clarity. build.security can easily create simple policies or very complex ones. But let's start with a simple one. One of the most common use cases for an authorization policy is:

 **Allow or Deny** an **identity** to **perform** one or more **actions on a resource.**

![Authorization request infrastructure](https://files.readme.io/88d4953-Bob-authorization.jpg)

###  Authorization use cases examples

* Is Bob, a new employee in our coffee store, allowed to sell to business customers?
* Is Laura, the head of the IT team, allowed to enter the server room? If so, is she allowed to change the door password in the organization's security management console?
* Can Alice, the New DevOps engineer just promoted from the QA team, deploy a new pod to the company's managed Kubernetes cluster? 

All of these questions are formulated around the same general question:  **Is an identity Allowed or Denied permission to perform some or any action on a resource?** 

To show how even this simply example can become a bit more complex, consider a scenario where we add another dimension to this general authorization problem description. 

**Are there any conditions that the identity, resource, or the environment needs to fulfill in order to perform the action?** 

![Request context dimension \(in this case, a time restriction\)](https://files.readme.io/658f7a6-Bob-authorization_night.jpg)

### Let's extended the Authorization use cases we set above

* If Bob, the new employee in our coffee store, is allowed to sell coffee to business customers, do we need to first check if the item is available and if we can supply it to the customer?
* If Laura, the head of the IT team, can access our secured and valuable server room, can she access it on weekends?
* If Alice, our DevOps engineer, can deploy a new pod to the company's Kubernetes cluster, can she do that even if there are open bugs in Jira on the component she is trying to deploy?

{% hint style="success" %}
**Next Step**

Now let's try to break this problem into smaller pieces and answer each part according to the data that we have.
{% endhint %}

## **Authorization Request Structure**

The authorization request is sent from the PEP \(Policy Enforcement Point\) to the PDP \(Policy Decision Point\). The request contains all the data that the PDP will use to make a decision or to retrieve additional data from other data sources.

**Option 1:** build.security provides a variety of [middleware and SDK\`s]() that you can simply integrate into your application and have it send the requests automatically and also enforce the decisions that are being made.

**Option 2:** Alternatively - we also support the use of a reverse proxy such as Envoy [configuring](../../pep-integrations-1/envoy-proxy-plugin.md).

## Identify the Identity Attributes

Each authorization request is submitted to the PDP following an action attempted by any virtual identity \(a service, identity, or any other active source trying to use your application's resources\).

The more information given to the PDP, the more secured and fine-grained the authorization policy can be.

A few examples of identity attributes that could be sent to the PDP are: 

1. JWT tokens, encapsulating claims of the identity 

2. Plain text HTTP headers that simply specify the user or the service. 

3. Any other form of identification you find useful

Sometimes, these attributes will include everything the PDP needs to make a wide authorization decision. However, in some cases, the PDP will use the given input to enrich the context it has leveraging external data sources.

![Identify the identity](https://files.readme.io/92610b3-policy_authorization_examples-01.png)

## Identify the Resource and Action

First, let's give some examples of actions and resources that are in common use and may  suit your use case.

* **Sell** **Products** to customers 
* Using REST API, call **apply** a **Method** on a service 
* **Open** a **door** of a classified room.

In terms of how to identify the action and the resource attributes, you will find that it will be accomplished in a manner similar to how you identified the identity. Your application will pass the information as part of the authorization request and you can enrich the information using real-time data from any data source.

Common examples of attributes for an action or a resource could be:

 1. HTTP method \(GET / POST / PUT / DELETE\)

 2. HTTP request path \(query parameters, path components etc.\`\)



![](https://files.readme.io/93b8351-policy_authorization_examples-02.png)

## Determining the Authorization Decision

After the PDP has all the information it needs on the identity, resource, and action, we can build a policy that will be evaluated by the PDP to enable it to determine the appropriate authorization decision.

The first step is to decide what the **default behavior** of the policy should be.

If the request doesn't match any of the rules that we set, do you want the PDP to **Allow** or **Deny** the action execution?

![Default behavior](https://files.readme.io/9d7d0e7-policy_authorization_examples-03.png)

Now, having defined all the required preparatory steps, we can easily write our rules by answering one of two questions:

1. If by default we **Deny** actions, which cases do we want to Allow?
2. If by default we **Allow** actions, which cases do we want to Deny?

{% hint style="success" %}
Well done
{% endhint %}

When you have your authorization rules defined, you can start implanting the authorization policy in the build.security control plane and deploy it within seconds to build.security OPA-based Policy Decision Point.

**What use case are you facing?** 

* [**API Authorization management**](../../policy-examples/full-api-authorization-policy.md)**:** Matching the Identity Role to a set of permission or entitlements and by that decide if the method trying to be executed on this API is allowed.
* Traditional  [**RBAC policy**](../../policy-examples/full-rbac-policy.md)**:** Matching the Identity Role to set of permission or entitlements. 
* [**Docker Authorization policy**:]() Simply enforcing the most common rules validating the docker image.
* [**Compare the request to a JSON data file**:](../../policy-examples/internal-data-source.md) Comparison of attributes from the authorization request to a JSON file managed within a control plane.

{% hint style="info" %}
build.security will be happy to assist your onboarding:

Feel free to open a technical support assistance ticket to our build.security support team in our [support portal](https://build-security.atlassian.net/servicedesk/customer/user/login?destination=portals) and we'll guide you on how to use those examples and customize them to your use case.
{% endhint %}



















\*\*\*\*

\*\*\*\*

