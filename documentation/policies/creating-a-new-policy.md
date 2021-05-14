# Creating a New Policy



Policies are listed in the lower part of the navigation panel. You can create as many policies as you need. Each policy must have a unique policy name and package name associated with it. As you begin creating a policy, you will be asked to select one of several integrations. build.security has predefined some of the most common rules you are likely to want to use, customized to each integration. When you select one of these predefined rules, you may need to provide a data value for a parameter \(for example, port number\(s\), IP address\(es\), etc.\).

**To create a new policy:**

1. In the Policies area, click the plus sign \(**+**\). The Create a New Policy panel will open on the right.
2. Begin by selecting the integration for which you wish to create a policy. Options include: Envoy, Docker, Java Spring, ASP.NET, Node Express, SymfonyPHP, or Custom. Using the Custom option enables you to begin with a blank policy and customize it yourself.

{% hint style="info" %}
**Note**

Once you select an integration, you cannot edit this value. You can delete the current policy and create another one as needed, but you cannot change the integration setting once you have created the policy.
{% endhint %}

![New policy panel](https://files.readme.io/68688e1-policy_wizard_panel.png)

In the **Integration Instructions** area, you can click to go to build.security GitHub repository and download the relevant middleware for your integration or to the build.security documentation for more information on how to integrate build.security middlewares with your application.

1. Click **Next** to advance to the next screen in the new policy wizard. The Policy Settings area opens.
2. In the **Policy Name** field, enter the name of the policy.
3. In the **Policy Description** field, enter text that will describe this policy \(optional\).
4. In the Advanced area \(accessed by clicking the **&gt;** arrow\), you can set the following:

* **Decision Path**: this field determines the JSON path where the policy file is stored within the PDP. When you set up your integration, you define this location so that when the PDP evaluates an authorization request, it will be evaluated against the policy located in the location defined by the Decision Path field.
* **Package Name**: this is the name that identifies which policy is run when querying the PDP. For example, if the package name is **authz**, the query path for this policy might be: `http://localhost:8181/v1/data/authz` This value set in this field must be unique within the project.

1. In the lower area of the panel, you can enable \(default\) or disable the **Start with best practice rules \(recommended\)** field. This is recommended, as build.security has already created the most common rules that are likely to be used for each integration.
2. Click **SAVE** to create the new policy.

Once created, the policy will appear in the list of policies on the control plane. The next step will be to add [Policy Items](https://docs.build.security/docs/policy-items).

