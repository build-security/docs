# PDP Deployments

The Policy Decision Point \(AKA PDP\) is responsible for making authorization decisions and is typically installed and maintained in your environment. build.security PDP can run in a variety of architectures.

In order for the decision engine to work, it is required:

1. Communicate with a build.security control plane to:

* Pull the latest up-to-date project configuration changes
* Send decision logs.

1. Communicate with your organizational databases on which the decisions rely.
2. Communicate with the applications which are based on the decision engine in enforcing permissions \(detailed in the [PEP](../../pep-integrations.md) section\).

![Policy Decision Points](https://files.readme.io/981bdf2-Policy_Decision_Points.jpg)

### Environment Variables

There's a list of an environment variables you can use in order to configure the PDP in runtime:

| Environment variable name | description |
| :--- | :--- |
| API\_KEY | The API key to be used by the PDP to authenticate with the build.security control plane |
| API\_SECRET | The API secret to be used by the PDP to authenticate with the build.security control plane |
| CONTROL\_PLANE\_ADDRESS | The control plane address to be used by the PDP |
| PDP\_LOG_\__LEVEL | The PDP log level. `debug` / `error`. Default is `error`. |
| BUNDLE\_COMMIT | The git commit SHA to be used for pulling specific policies. This feature assumes [git integration](../../project-settings/git-integration-settings.md) is enabled as the control needs the ability to pull and serve the specific policies and configurations to the PDP. |

### Supported Environments

To deploy your PDP correctly, use the relevant installation instructions for your environment.

[Standalone Docker](standalone-docker-1.md)  
[Kubernetes](kubernetes.md)

