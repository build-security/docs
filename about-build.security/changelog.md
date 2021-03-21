# Changelog

## Version 0.2

**Major features**

*  Policy Testing
* Additional ****filters in the decision logs \(input / result\)
* MySQL support
* New look and feel

**Minor enhancements**

* Supporting non-English characters in policy names
* More debug logs in the PDP
* 'Strict mode' is now turned on by default within the playground. read more here.
* PDP version is now displayed in the PDP screen right beside each pdp instance
* Text areas can now be copied via easy "copy to clipboard" button
* Text areas can now be expandable
* Cache control in the policy playground
* Ability to re-order policy rules within the policy tab
* Support of [library rules](https://library.build.security/) + first JIRA search library rule
* new builtin functions
  * build.json\_partial\_compare
  * build.rate\_limit
  * cache.insert
  * cache.get
  * cache.delete
* JAVA SDK for non-middleware usage

**Fixes**

* bug displaying policy compilation errors when one policy referenced another policy via `import` 
* bug where not all policy packages were sent to the PDP as part of the policy playground
* PHP symfony middleware fixes
* Minor fixes in the "fetch schema" of the DynamoDB data-source
* An audit log was missing when publishing to PDPs

**Behavioural changes**

* Removal of versioning per policy \(in favour of future git integration\)

