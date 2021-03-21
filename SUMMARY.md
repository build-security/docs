# Table of contents

* [build.security's mission](README.md)

## Documentation <a id="about-build.security"></a>

* [About build.security](about-build.security/about-build.security-1/README.md)
  * [Architecture](about-build.security/about-build.security-1/getting-started.md)
  * [Using OPA for Applications Authorization](about-build.security/about-build.security-1/using-opa-for-applications-authorization.md)
* [Getting Started](about-build.security/getting-started/README.md)
  * [Logging In](about-build.security/getting-started/control-plane-overview.md)
  * [Control Plane Overview](about-build.security/getting-started/logging-in.md)
* [Changelog](about-build.security/changelog.md)

---

* [System Settings](system-settings/README.md)
  * [Managing Users](system-settings/managing-users.md)
  * [Roles](system-settings/roles.md)
  * [User API Key Management](system-settings/user-api-key-management.md)
  * [Internal Audit](system-settings/internal-audit.md)
  * [Log Shipping Integration](system-settings/log-shipping-integration.md)
* [Projects](projects/README.md)
  * [Project Selection Screen](projects/project-selection-screen.md)
  * [Creating a project](projects/creating-a-project.md)
  * [Deleting a project](projects/deleting-a-project.md)
  * [Publish Project Configuration](projects/publish-project-configuration.md)
* [Project Settings](project-settings/README.md)
  * [PDP Settings](project-settings/pdp-settings.md)
  * [Decision Log Settings](project-settings/decision-log-settings.md)
  * [Log Shipping](project-settings/log-shipping.md)
* [Policy Decision Points \(PDP\)](policy-decision-points-pdp/README.md)
  * [Creating a New PDP Configuration](policy-decision-points-pdp/creating-a-new-pdp-configuration.md)
  * [Generating API Keys for a PDP](policy-decision-points-pdp/generating-api-keys-for-a-pdp.md)
  * [PDP Deployments](policy-decision-points-pdp/pdp-deployments.md)
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
  * [Decision Details](decision-logs/decision-details.md)
  * [Decision Log Masking](decision-logs/decision-log-masking.md)
* [Impact Analysis](impact-analysis/README.md)
  * [Rule Tracing](impact-analysis/rule-tracing.md)
* [PEP Integrations](pep-integrations.md)
* [Policies](policies/README.md)
  * [Policies Screen](policies/policies-screen.md)
  * [Policy Toolbar](policies/policy-toolbar.md)
  * [Policy Evaluation Playground](policies/policy-evaluation-playground.md)
  * [Policy Code Panel](policies/policy-code-panel.md)
  * [Creating a New Policy](policies/creating-a-new-policy.md)
  * [Editing Policy Settings](policies/editing-policy-settings.md)
  * [Deleting a Policy](policies/deleting-a-policy.md)
  * [Policy Item Status](policies/policy-item-status.md)
* [Policy Items](policy-items/README.md)
  * [Managing Policy Items](policy-items/managing-policy-items.md)
  * [Predefined Rules \(Templates\)](policy-items/predefined-rules-templates.md)
  * [Empty Rules](policy-items/empty-rules.md)
  * [Custom Blocks](policy-items/custom-blocks.md)

## LIBRARY <a id="built-in-functions"></a>

* [Built-In Functions](built-in-functions/built-in-functions/README.md)
  * [cache](built-in-functions/built-in-functions/cache.md)
  * [build.json\_partial\_compare](built-in-functions/built-in-functions/build.json_partial_compare.md)
  * [build.geo\_from\_ip](built-in-functions/built-in-functions/build.geo_from_ip.md)
  * [build.rate\_limit](built-in-functions/built-in-functions/build.rate_limit.md)
  * [build.query\_raw](built-in-functions/built-in-functions/build.query_raw/README.md)
    * [DynamoDB](built-in-functions/built-in-functions/build.query_raw/dynamodb.md)
    * [MySQL](built-in-functions/built-in-functions/build.query_raw/mysql.md)
    * [Elasticsearch](built-in-functions/built-in-functions/build.query_raw/elasticsearch.md)
    * [PostgreSQL](built-in-functions/built-in-functions/build.query_raw/postgresql.md)
* [Library Rules](https://library.build.security)

## PDP DEPLOYMENT METHODS

* [Standalone Docker](pdp-deployment-methods/standalone-docker-1.md)
* [Kubernetes](pdp-deployment-methods/kubernetes.md)

## PEP INTEGRATIONS <a id="pep-integrations-1"></a>

* [Docker Authorization Plugin](pep-integrations-1/docker-authorization-plugin.md)
* [Envoy Proxy Plugin](pep-integrations-1/envoy-proxy-plugin.md)

---

* [Node.js](https://github.com/build-security/opa-express-middleware)
* [PHP Symfony](https://github.com/build-security/opa-symfony-middleware)
* [ASP.Net](https://github.com/build-security/OPA-AspDotNetCore-Middleware)

## POLICY EXAMPLES

* [Full API Authorization Policy](policy-examples/full-api-authorization-policy.md)

---

* [Full RBAC Policy](full-rbac-policy.md)
* [Docker Authorization Policy](docker-authorization-policy.md)
* [Internal Data Source](internal-data-source.md)

## QUICKSTARTS

* [Testing Your Policy](quickstarts/testing-your-policy/README.md)
  * [Dry Run Evaluation](quickstarts/testing-your-policy/dry-run-evaluation.md)

## WHITE PAPERS <a id="whitepapers"></a>

---

* [Performance Benchmark](https://build.security/whitepaper-performance/)

