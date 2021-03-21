# Changelog

## Version 0.2 - March 21, 2021

**Major features**

*  Policy Testing
* Additional ****filters in the decision logs \(input / result\)
* [MySQL support](../data-sources/new-mysql-data-source.md)
* New look and feel
* Log shipping support for datadog, Elasticsearch

**Minor enhancements**

* Supporting non-English characters in policy names
* More debug logs in the PDP
* ['Strict mode' is now turned on by default within the playground. read more here.](../policies/policy-evaluation-playground.md#strict-mode)
* PDP version is now displayed in the PDP screen right beside each pdp instance
* Text areas can now be copied via easy "copy to clipboard" button
* Text areas can now be expandable
* [Cache control in the policy playground](../policies/policy-evaluation-playground.md#use-cache-setting)
* Ability to re-order policy rules within the policy tab
* Support of [library rules](https://library.build.security/) + first JIRA search library rule
* new builtin functions
  * [build.json\_partial\_compare](../library/built-in-functions/build.json_partial_compare.md)
  * [build.rate\_limit](../library/built-in-functions/build.rate_limit.md)
  * [cache.insert](../library/built-in-functions/cache.md)
  * [cache.get](../library/built-in-functions/cache.md)
  * [cache.delete](../library/built-in-functions/cache.md)
* JAVA SDK for non-middleware usage

**Fixes**

* bug displaying policy compilation errors when one policy referenced another policy via `import` 
* bug where not all policy packages were sent to the PDP as part of the policy playground
* PHP symfony middleware fixes
* Minor fixes in the "fetch schema" of the DynamoDB data-source
* An audit log was missing when publishing to PDPs

**Behavioural changes**

* Removal of versioning per policy \(in favour of future git integration\)

## Version 0.1 - November 18, 2020

**Major features**

* JIT compilation for policies while authoring
* New policy components
* Envoy integration

**Minor enhancements**

* Decision log filter by decision ID
* UX improvements



