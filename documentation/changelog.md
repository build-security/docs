# Changelog

## Version 0.2 - March 21, 2021

**Major Features**

* [Policy Unit Testing](../quickstarts/testing-your-policy/policy-unit-testing.md)
* Additional filters in the decision logs \(input / result\)
* [MySQL support](../data-sources/new-mysql-data-source.md)
* New look and feel
* [Log shipping](../system-settings/log-shipping-integration.md) support for datadog, Elasticsearch

**Minor Enhancements**

* Supporting non-English characters in policy names
* More debug logs in the PDP
* Policy playground now auto-populates with the user's last input
* ['Strict mode'](../policies/policy-evaluation-playground.md#strict-mode) is now turned on by default within the playground. Read more [here.](../policies/policy-evaluation-playground.md#strict-mode)
* PDP version is now displayed in the PDP screen right beside each pdp instance
* Text areas can now be copied via easy "copy to clipboard" button
* Text areas can now be expandable
* [Cache control](../policies/policy-evaluation-playground.md#use-cache-setting) in the policy playground
* Ability to re-order policy rules within the policy tab
* Support of [library rules](https://library.build.security/) + JIRA search library rule
* New builtin functions
  * [build.json\_partial\_compare](../library/built-in-functions/build.json_partial_compare.md)
  * [build.rate\_limit](../library/built-in-functions/build.rate_limit.md)
  * [cache.insert](../library/built-in-functions/cache.md)
  * [cache.get](../library/built-in-functions/cache.md)
  * [cache.delete](../library/built-in-functions/cache.md)
* [JAVA SDK](https://github.com/build-security/opa-java-client) for non-middleware usage

**Fixes**

* Bug displaying policy compilation errors when one policy referenced another policy via `import` 
* Bug where not all policy packages were sent to the PDP as part of the policy playground
* PHP symfony middleware fixes
* Minor fixes in the "View Schema" of the DynamoDB data-source
* An audit log was missing when publishing to PDPs

**Behavioural Changes**

* Removal of versioning per policy \(in favour of future Git integration\)

## Version 0.1 - November 18, 2020

**Major Features**

* JIT compilation for policies while authoring
* New policy components
* Envoy integration

**Minor Enhancements**

* Decision log filter by decision ID
* UX improvements

