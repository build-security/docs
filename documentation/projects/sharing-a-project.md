# Sharing a Project

A common requirement is the ability to share policies and datasources with other projects. A typical use case is to provide a development team with the ability to author domain specific policies, which can be used by other policies, written by other team in the organization.

### Sharing a project

In order to mark a project as "shareable", toggle the library setting in the project [General Settings](../project-settings/general-settings.md) screen and publish the project.

From this point forward, other projects in the same tenant can reference policies and datasources of this "shared library project".

### Referencing a shared project

In order to reference a policy of a shared library project, the syntax is:

```scala
#data.<library_slug>.<policypackagename>.<function_name>
data.shared_project_slug.main_policy.allow
```

In order to reference a datasource of a shared library project, the syntax is:

```scala
#data.<library_slug>.datasources.<datasource_name>
data.shared_project_slug.datasources.postgresql
```

### Bundle implications

Shared projects\` policies and datasource definitions will be included in all the bundles generates by all projects in the tenant.

