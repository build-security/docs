# Environments

Environments are a logic entity of multiple Policy Decision Points that share certain characteristics. There is no limitation of how many environments a projects can hold, nor the amount of PDPs in a certain environment.

Common use case is to divide the project's PDPs into 3 environments:

1. dev - PDPs that are used for development purposes.
2. staging - PDPs that are used to mimic production deployments
3. production - production PDPs

### Environment settings

Each environment provides the operator with the ability to decide how policies will get served to the PDPs in that environment. The possible publishing methods are:

* Direct - Policies are sent directly from the control plane and into the PDPs in real-time.
* git \(requires [git integration](project-settings/git-integration-settings.md) to be enabled\)
  * branch - policies are served according to the tip of a specific git branch
  * commit SHA - policies are served according to a specific git commit SHA
  * tag - policies are served according to a specific git tag 

The following illustrates a common use case where `Development` environment receives policies directly from the control plane, while`Staging` and `Production` are integrated with their appropriate branches within git:

![Environments screen](../.gitbook/assets/image%20%2826%29.png)

When creating or editing a new environment, the operator can choose the policies publishing method:

![New environment settings](../.gitbook/assets/image%20%2825%29.png)

