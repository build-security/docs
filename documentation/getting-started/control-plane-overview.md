# Control Plane Overview

The control plane is where you will interface with the build.security platform. This includes defining and integrating build.security with your data sources, PDPs, and PEPs. Creating your authorization policies and monitoring the authorization decisions.

The control plane is divided into the following areas:

* Navigation panel on the left enables you to access each of the main elements in the build.security system
* Toolbar at the top
* Main display area where you will configure, monitor, and manage all the elements that go into creating and manage your authorization policies.

![build.security control plane navigation panel and main display area](https://files.readme.io/1ebfc4a-policy.PNG)

### Navigation Panel Options

| Menu Option | Description |
| :--- | :--- |
| Dashboard | Currently under development. |
| [Policy Enforcement Points]() | Collection of integration points for build.security's platform. The Policy Enforcement Points are tasked with enforcing the authorization decision. The Policy Enforcement Points screen contains links to all current options for integrating an enforcement point with build.security. |
| [Policy Decision Points \(PDPs\)](../policy-decision-points-pdp/) | Policy Decision Points are defined in the build.security system by a unique name. On the Policy Decision Point screen, you can:  - View the existing details of each PDP - Edit the existing PDPs - Create new PDPs - Publish policy bundles to PDPs |
| [Data Sources](../data-sources/) | A data source is defined as a source for information that supplies the Policy Decision Points with the relevant data in real-time according to the defined policy rules. |
| [Decision Logs](../decision-logs/) | The decision logs screen enables you to view all decisions made by the PDPs managed in this project. |
| [Project settings](../project-settings/) | The project settings option enables you to configure and manage your project. It includes the following options:  - General settings - PDP settings - Decision log |
| [Policies](../policies/) | From the policies option, you can build, modify or view the project's authorization policies. These represent your organization's authorization policy for accessing any \(or all\) of the services or resources within the organization.  In this area, you can define policy items that together determine what the policy will be. |
| [System Settings](../system-settings/) | The system settings option \(located in the lower left area control plane\) opens the system screen enabling you to manage users, view the audit log or configure log shipping. |

![Navigation panel](https://files.readme.io/d211284-control_navigationsysset.PNG)

### Main Toolbar

Although most of the features and commands in build.security are easily accessed from the control plane navigation panel, some helpful and important options can be accessed from the main toolbar as well.

The main build.security toolbar is located at the top of the control plane window and contains the following icons:

![Main toolbar](https://files.readme.io/4c9dda3-toolbar.PNG)

The following table details each of the items in the main toolbar.

<table>
  <thead>
    <tr>
      <th style="text-align:left">Location</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">Hamburger (three horizonal lines) icon</td>
      <td style="text-align:left">Expands/collapses the control plane navigation panel. You can set the
        navigation panel to be visible at all times (or hidden at all times) by
        clicking on the pin/unpin icon on the <a href="../system-settings/">system settings</a> button.</td>
    </tr>
    <tr>
      <td style="text-align:left">Project/switch project</td>
      <td style="text-align:left">Current project name appears in the toolbar on the left. To switch to
        another project, press the down arrow. A list of projects is available.
        If you don&apos;t see the project you want, click <b>Browse all Projects</b>.
        <br
        />
        <br />This will open the <a href="../projects/project-selection-screen.md">project selection screen</a> where
        you can either select an existing project or create a new one.</td>
    </tr>
    <tr>
      <td style="text-align:left">Publish</td>
      <td style="text-align:left">Publishes the latest configurations and policy versions to the PDP.</td>
    </tr>
    <tr>
      <td style="text-align:left">User avatar icon</td>
      <td style="text-align:left">
        <p><b>User identification: </b>Shows your user name and email address.
          <br
          />
          <br /><b>Change Theme: </b>Toggles the current theme display between day (light
          background) and night (dark background).
          <br />
          <br /><b>Documentation: </b>Provides a link to build.security&apos;s online
          documentation.</p>
        <p></p>
        <p><b>Support: </b>Access the build.security support portal.
          <br />
          <br /><b>Log Out: </b>Logs you out of build.security and closes the current
          user session.</p>
      </td>
    </tr>
  </tbody>
</table>

![User avatar options](https://files.readme.io/23e73c5-toolbar-right.png)



