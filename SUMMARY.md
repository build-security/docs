# Table of contents

* [build.security's mission](README.md)

## CHANGELOG

* [Changelog - Control Plane](changelog/changelog.md)
* [Changelog - PDP](changelog/changelog-pdp.md)

## Documentation

* [About build.security](documentation/about-build.security-1/README.md)
  * [Architecture](documentation/about-build.security-1/getting-started.md)
  * [Using OPA for Applications Authorization](documentation/about-build.security-1/using-opa-for-applications-authorization.md)
* [Getting Started](documentation/getting-started/README.md)
  * [Control Plane Overview](documentation/getting-started/control-plane-overview.md)
  * [Main Toolbar](documentation/getting-started/main-toolbar.md)
  * [Navigation Panel Options](documentation/getting-started/navigation-panel-options.md)
* [Logging In](documentation/logging-in/README.md)
  * [With build.security Credentials](documentation/logging-in/logging-in-1.md)
  * [Using Single Sign On](documentation/logging-in/using-single-sign-on.md)
  * [Using Social Provider Authentication](documentation/logging-in/using-social-provider-authentication.md)

---

* [System Settings](system-settings/README.md)
  * [Managing Users](system-settings/managing-users/README.md)
    * [About Roles](system-settings/managing-users/roles.md)
  * [User API Key Management](system-settings/user-api-key-management.md)
  * [Internal Audit](system-settings/internal-audit.md)
  * [Log Shipping Integration](system-settings/log-shipping-integration.md)
  * [Single Sign On](system-settings/single-sign-on.md)
* [Projects](projects/README.md)
  * [Project Selection Screen](projects/project-selection-screen.md)
  * [Creating a project](projects/creating-a-project.md)
  * [Deleting a project](projects/deleting-a-project.md)
  * [Publish Project to PDPs](projects/publish-project-configuration.md)
  * [Commit Project to Git](projects/commit-project-to-git.md)
* [Project Settings](project-settings/README.md)
  * [PDP Settings](project-settings/pdp-settings.md)
  * [Decision Log Settings](project-settings/decision-log-settings.md)
  * [Log Shipping](project-settings/log-shipping.md)
  * [Git Integration Settings](project-settings/git-integration-settings.md)
* [Policy Decision Points \(PDP\)](policy-decision-points-pdp/README.md)
  * [Creating a New PDP Configuration](policy-decision-points-pdp/creating-a-new-pdp-configuration.md)
  * [Generating API Keys for a PDP](policy-decision-points-pdp/generating-api-keys-for-a-pdp.md)
  * [PDP Deployments](policy-decision-points-pdp/pdp-deployments/README.md)
    * [Kubernetes](policy-decision-points-pdp/pdp-deployments/kubernetes.md)
    * [Kubernetes with Helm Chart](policy-decision-points-pdp/pdp-deployments/deploy-pdp-with-helm-chart.md)
    * [Standalone Docker](policy-decision-points-pdp/pdp-deployments/standalone-docker-1.md)
  * [PDP Hardening](policy-decision-points-pdp/pdp-hardening.md)
  * [Editing a PDP Configuration](policy-decision-points-pdp/editing-a-pdp-configuration.md)
  * [Deleting a PDP](policy-decision-points-pdp/deleting-a-pdp.md)
  * [Caching Mechanism](policy-decision-points-pdp/caching-mechanism.md)
  * [TLS Configuration](policy-decision-points-pdp/tls-configuration.md)
  * [PDP debugging](policy-decision-points-pdp/pdp-debugging.md)
* [Data Sources](data-sources/README.md)
  * [Defining a New Data Source](data-sources/defining-a-new-data-source.md)
  * [New Internal Data Source](data-sources/new-internal-data-source.md)
  * [New PostgreSQL Data Source](data-sources/new-postgresql-data-source.md)
  * [New Elasticsearch Data Source](data-sources/new-elasticsearch-data-source.md)
  * [New DynamoDB Data Source](data-sources/new-dynamodb-data-source.md)
  * [New MySQL Data Source](data-sources/new-mysql-data-source.md)
  * [Editing an Existing Data Source](data-sources/editing-an-existing-data-source.md)
  * [Deleting a Data Source](data-sources/deleting-a-data-source.md)
* [Decision Logs](decision-logs/README.md)
  * [Decision Log Filters](decision-logs/decision-log-filters.md)
  * [Decision Logs Toolbar](decision-logs/decision-logs-toolbar.md)
  * [Decision Details](decision-logs/decision-details.md)
  * [Decision Log Masking](decision-logs/decision-log-masking.md)
* [Impact Analysis](impact-analysis/README.md)
  * [Rule Tracing](impact-analysis/rule-tracing.md)
* [PEP Integrations](pep-integrations.md)
* [Policies](policies/README.md)
  * [Creating a New Policy](policies/creating-a-new-policy.md)
  * [Building a Policy](policies/building-a-policy.md)
  * [Policy Testing](policies/policy-testing/README.md)
    * [Creating a Policy Unit Test](policies/policy-testing/creating-and-running-tests.md)
    * [Running a Policy Unit Test](policies/policy-testing/running-a-policy-unit-test.md)
  * [Policies Screen](policies/policies-screen/README.md)
    * [Policy Toolbar](policies/policies-screen/policy-toolbar.md)
  * [Policy Evaluation Playground](policies/policy-evaluation-playground.md)
  * [Policy Code Panel](policies/policy-code-panel.md)
  * [Deleting a Policy](policies/deleting-a-policy.md)
  * [Editing Policy Settings](policies/editing-policy-settings.md)
  * [Policy Items](policies/policy-items/README.md)
    * [Policy Item Status](policies/policy-items/policy-item-status.md)
    * [Managing Policy Items](policies/policy-items/managing-policy-items.md)
    * [Predefined Rules \(Templates\)](policies/policy-items/predefined-rules-templates.md)
    * [Empty Rules](policies/policy-items/empty-rules.md)
    * [Custom Blocks](policies/policy-items/custom-blocks.md)

## LIBRARY

* [Built-In Functions](library/built-in-functions/README.md)
  * [cache](library/built-in-functions/cache.md)
  * [build.json\_partial\_compare](library/built-in-functions/build.json_partial_compare.md)
  * [build.geo\_from\_ip](library/built-in-functions/build.geo_from_ip.md)
  * [build.rate\_limit](library/built-in-functions/build.rate_limit.md)
  * [build.query\_raw](library/built-in-functions/build.query_raw/README.md)
    * [DynamoDB](library/built-in-functions/build.query_raw/dynamodb.md)
    * [MySQL](library/built-in-functions/build.query_raw/mysql.md)
    * [Elasticsearch](library/built-in-functions/build.query_raw/elasticsearch.md)
    * [PostgreSQL](library/built-in-functions/build.query_raw/postgresql.md)
* [Library Rules](https://library.build.security)

## PEP INTEGRATIONS <a id="pep-integrations-1"></a>

* [Envoy Proxy Integration](pep-integrations-1/envoy-proxy-plugin.md)
* [Kafka Topic Authorization](pep-integrations-1/kafka-topic-authorization.md)

---

* [Node.js](https://github.com/build-security/opa-express-middleware)
* [PHP Symfony](https://github.com/build-security/opa-symfony-middleware)
* [ASP.Net](https://github.com/build-security/OPA-AspDotNetCore-Middleware)
* [JAVA](https://github.com/build-security/opa-java-client)
* [JAVA-Spring](https://github.com/build-security/opa-java-spring-client)
* [AWS API Gateway](https://github.com/build-security/aws-api-gateway-authz)

## TUTORIALS <a id="policy-examples"></a>

* [Full API Authorization Policy](policy-examples/full-api-authorization-policy.md)

---

* [RBAC Policy](full-rbac-policy.md)
* [Using Internal Data Source](internal-data-source.md)
* [Working with Environments \(Dev vs. Production\)](working-with-envs.md)

## QUICKSTARTS

* [Testing Your Policy](quickstarts/testing-your-policy/README.md)
  * [Policy Unit Testing](quickstarts/testing-your-policy/policy-unit-testing.md)
  * [Dry Run Evaluation](quickstarts/testing-your-policy/dry-run-evaluation.md)

## WHITE PAPERS <a id="whitepapers"></a>

* [Performance Benchmark](https://build.security/whitepaper-performance/)

