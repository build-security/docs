---
description: >-
  Description of all major changes and enhancement in build.security's control
  plane
---

# Changelog - Control Plane

## Version 1.0.0 - July 25, 2021

**Major Features**

* K8s admission control webhook enhancements 

**Minor Enhancements** 

* Managed \(cloud\) PDP optimization 
* Multiple UI enhancements and bug fixes



## Version 0.9 - July 18, 2021

**Major Features**

* Freemium plan support 

**Minor Enhancements** 

* Support signup on mobile 
* Managed \(cloud\) PDP enhancements
* Multiple UI enhancements and bug fixes

## Version 0.8 - July 1st, 2021

**Major Features**

* Policy page new layout 

**Minor Enhancements** 

* Shared project enhancements
* Improve login mechanism 
* Multiple UI enhancements and bug fixes

## Version 0.7 - June 21, 2021

**Major Features**

* [Shared projects](https://docs.build.security/documentation/projects/sharing-a-project) 
* [Environments](https://docs.build.security/documentation/environments)

**Minor Enhancements** 

* Add cache hit ratio to decision logs 
* Multiple UI enhancements and bug fixes

## Version 0.6 - June 2, 2021

**Major Features**

* Roles and Permissions table - defining your organization's RBAC model with an easy and simple UI

**Minor Enhancements**

* Onboarding enhancements 

## Version 0.5 - May 23, 2021

**Major Features**

* [Onboarding](https://docs.build.security/documentation/getting-started/onboarding) - guiding the user to create a policy, publish it to a cloud PDP and test it. 

**Minor Enhancements**

* Cache improvements 
* Multiple UI enhancements and bug fixes

## Version 0.4 - April 25, 2021

**Major Features**

* Code editors now support keyboard shortcuts and general IDE-like experience

**Minor Enhancements**

* log ingestion performance improvements
* Multiple UI enhancements and changes
* Just-In-Time Compilation status indication
* cURL button is now part of the playground; including the user input
* A new option to hide / remove all inactive PDPs from PDP screen

## Version 0.3 - April 13, 2021

**Major Features**

* [Git integration support](../documentation/projects/commit-project-to-git.md)
* [Support for social log-in](../documentation/logging-in/using-social-provider-authentication.md)
* [Single Sign On support \(via OKTA\)](../documentation/logging-in/using-single-sign-on.md)

**Minor Enhancements**

* Improved decision-logs ingestion rate
* Adding an indication of the control plane version 
* Allow filtering decision logs by the Result or Input fields

**Fixes**

* Supporting large message size in policy playground evaluation tasks
* Sort PDP instances with online instances on top of Offline instances
* Fixed issue where inactive rules with syntax error are causing Rego compilation errors

**Behavioral Changes**

* Policies containing errors can no longer be published until all Rego compilation errors in the project are resolved

## Version 0.2 - March 21, 2021

**Major Features**

* [Policy Unit Testing](../quickstarts/testing-your-policy/policy-unit-testing.md)
* Additional filters in the decision logs \(input / result\)
* [MySQL support](../documentation/data-sources/new-mysql-data-source.md)
* [Policy Authoring](../documentation/policies/policy-items/managing-policy-items.md)- new look and feel
* [Log shipping](../documentation/system-settings/log-shipping-integration.md) support for Datadog, Elasticsearch

**Minor Enhancements**

* Supporting non-English characters in policy names
* More debug logs in the PDP
* Policy playground now auto-populates with the user's last input
* ['Strict mode'](../documentation/policies/policy-evaluation-playground.md#strict-mode) is now turned on by default within the playground. Read more [here](../documentation/policies/policy-evaluation-playground.md#strict-mode)
* PDP version is now displayed in the PDP screen right beside each PDP instance
* Text areas can now be copied via easy "copy to clipboard" button
* Text areas can now be expandable
* [Cache control](../documentation/policies/policy-evaluation-playground.md#use-cache-setting) in the policy playground
* Ability to re-order policy rules within the policy tab
* Support of [library rules](https://library.build.security/) + JIRA search library rule
* New built-in functions
  * [build.json\_partial\_compare](../library/built-in-functions/build.json_partial_compare.md)
  * [build.rate\_limit](../library/built-in-functions/build.rate_limit.md)
  * [cache.insert](../library/built-in-functions/cache.md)
  * [cache.get](../library/built-in-functions/cache.md)
  * [cache.delete](../library/built-in-functions/cache.md)
* [JAVA SDK](https://github.com/build-security/opa-java-client) for non-middleware usage

**Fixes**

* Bug displaying policy compilation errors when one policy referenced another policy via `import` 
* All policy packages are now sent to the PDP as part of the policy playground.
* Symfony PHP middleware fixes.
* Minor fixes in the "View Schema" of the DynamoDB data source.
* An audit log was missing when publishing to PDPs.

**Behavioral Changes**

* Removal of versioning per policy \(in favor of future Git integration\)

## Version 0.1 - November 18, 2020

**Major Features**

* JIT compilation for policies while authoring
* New policy components
* Envoy integration

**Minor Enhancements**

* Decision log filter by decision ID
* UX improvements

