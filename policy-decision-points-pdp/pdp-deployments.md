# PDP Deployments

The Policy Decision Point \(AKA PDP\) is responsible for making authorization decisions and is typically installed and maintained in your environment. build.security PDP can run in a variety of architectures.

In order for the decision engine to work, it is required:

1. Communicate with a build.security control plane to:

* Pull the latest up-to-date project configuration changes
* Send decision logs.

1. Communicate with your organizational databases on which the decisions rely.
2. Communicate with the applications which are based on the decision engine in enforcing permissions \(detailed in the [PEP](https://docs.build.security/docs/policy-enforcement-points-peps-1) section\).

![Policy Decision Points](https://files.readme.io/981bdf2-Policy_Decision_Points.jpg)

To deploy your PDP correctly, use the relevant installation instructions for your environment.

### Supported Environments

[Standalone Docker](https://docs.build.security/docs/docker)  
[Kubernetes](https://docs.build.security/docs/k8s-deployment)

