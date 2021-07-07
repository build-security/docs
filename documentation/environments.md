# Environments

An environments is a logic entity of multiple Policy Decision Points that share certain characteristics. There is no limitation for how many environments a projects can hold, nor the amount of PDPs that can be created and maintained within any given environment.

Common use case is to divide the project's PDPs into 3 environments:

1. dev - PDPs that are used for development purposes
2. staging - PDPs that are used to mimic production deployments
3. production - production PDPs

### Publishing Methods

Each environment provides the organization with the ability to decide how policies will get served to the PDPs in that environment. Possible publishing methods include:

* Direct: Policies are sent directly from the control plane and into the PDPs in real-time.
* Git: \(requires [Git integration](project-settings/git-integration-settings.md) to be enabled\)
  * branch - policies are served according to the tip of a specific Git branch
  * commit SHA - policies are served according to a specific Git commit SHA
  * tag - policies are served according to a specific Git tag 

The following illustrates a common use case where the `Development` environment receives policies directly from the control plane, while`Staging` and `Production` are integrated with their appropriate branches within Git:

![Environments screen](../.gitbook/assets/image%20%2828%29.png)

When creating or editing a new environment, the organization can choose the policies publishing method:

![New environment settings](../.gitbook/assets/image%20%2826%29.png)



