# Changelog - PDP

## Version 0.4.5 - August 1, 2021

* K8s integration enhancements

## Version 0.4.4 - July 25, 2021

* Stdout logs enhancements
* Improve testing coverage
* Add data-ex endpoint as v0

## Version 0.4.3 - July 18, 2021

* Dataextractor warm cache entry once
* Crash fix on dataextractor failure
* Upgrade OPA to v0.30.1

## Version 0.4.2 - June 28, 2021

* Add process metrics on status report

## Version 0.4.1 - June 14, 2021

* Report cache metrics
* Upgrade OPA to v0.28.0

## Version 0.4.0 - May 27, 2021

* Add kill functionality

## Version 0.3.10 - May 9, 2021

* Add cache warming

## Version 0.3.8 - April 20, 2021

* Allow dynamic labels from the discovery bundle
* Update used libraries 

## Version 0.3.6 - April 12, 2021

* Fixed an issue in policy-tests where unmarshal of a response may fail if a runtime error occurred 

## Version 0.3.5 - April 12, 2021

* Add support of comparing JSON files that include arrays in [`build.json_partial_compare(expectedJson, actualJson)`](https://docs.build.security/library/built-in-functions/build.json_partial_compare)\`\`

## Version 0.3.4 - March 25, 2021

* Support usage of [BUNDLE\_COMMIT](../documentation/policy-decision-points-pdp/pdp-deployments/#supported-environments) using git commit SHA for pulling specific policies
* Bug fix - supporting \[\]uint8 as returned value from external data-source

## Version 0.3.3 - March 22, 2021

* Align policy playground and policy testing result

## Version 0.3.0 - March 18, 2021

* policy testing support

## Version 0.2.2 - March 16, 2021

* build.json\_partial\_compare

## Version 0.2.1 - March 15, 2021

* Rate limiting support

