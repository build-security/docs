# Projects

### About Projects

Within build.security, a project can be considered your workspace. Within this workspace, you will create, manage, and evaluate your authorization policy. Once you have defined what you want to authorize \(or deny\) within your organization, you'll configure build.security to interact with each of the key elements required to implement the authorization policy. This means defining where the data will come from, what impacts the decision \(for example, time or day, location, personal attributes such as department, created by an organization to apply and manage its authorization policies.

After logging in and entering the control plane, all that you see when clicking one of the options in the top part of the navigation panel is related to a single project that you have just entered.

![Control plane offers access to all elements of the project](https://files.readme.io/228d37d-policy.PNG)

### Project Contents

Within the project, you can create and manage:

* **Policies**: a policy defines the organization's authorization requirements, essentially what resources users will be allowed or denied access to.
* **Data sources**: an internal or external data source \(for example an internal database, a PostgreSQL database, etc.\) responsible for supplying relevant data in real-time.
* **Policy Decision Points**: PDPs are responsible for making authorization decisions based on the organization's authorization policy. build.security's PDP screen enables you to configure
* **Policy Enforcement Points**: PEPs are responsible for enforcing the authorization decisions they receive from the organization's PDPs. PEPs are integrated with build.security.
* **Decision logs**: an ongoing log of all authorization decisions that were made with additional drill-down options to view decision metrics, input, results and more.

### Project Details

The main details defined when creating a new project are:

* Project name
* Description of the project \(optional\)

These values are defined when the project is created and can be accessed and edited later on the [Project Settings](../project-settings/) screen.

![Project screen](https://files.readme.io/872aba7-newproject.PNG)





