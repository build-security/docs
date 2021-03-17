# Policy Toolbar

The policy toolbar, located just below the main toolbar and above the list of existing policy items, contains the following options:

![Policy toolbar](https://files.readme.io/e6854ae-policy_toolbar1.PNG)



| item | description |  |
| :--- | :--- | :--- |
| Policy name | Indicates the name of the policy currently being displayed in the rule building area. |  |
| Policy version | Displays the current version number and last time it was updated \(date/time in UTC\). |  |
| Default policy type | You can see the current default setting for the policy \(DENY or ALLOW\) and change it by clicking the down arrow and selecting the other option. |  |
| Version number and status | Using the down arrow, you can navigate between different versions. The currently displayed version is indicated to the right of the arrow. |  |
| Create Draft icon | At any time, you can click the Create Draft icon. build.security will then copy the currently displayed version and create a new one. It will automatically be given the next sequential number and be given the status of Draft. For more information about creating a draft, see below. |  |
| MARK AS READY | When viewing a version with a status of either "Archived" or "Draft", you can click the MARK AS READY button. This will change the status of the policy to Pending Publication.  When you click Publish, the Pending Publication policy will be given a status of Published and that will be the policy sent to the PDP for consideration when determining the authorization decision. |  |
| Kebab or three horizonal dots | Offers you access to the **cURL Example** button. Click this to display a cURL example to get or send data using a URL syntax, that can be used to verify functionality between the data source and the PDP. Click the copy icon to copy the command to the clipboard for further use. Click **OK** to close the dialog box. |  |

### Creating a New Draft

Because you cannot edit a published policy version, the easiest way to make a change to a policy marked as ready, is to click **Create Draft**. build.security will create a new version of the currently displayed policy, including duplicating all existing settings. The new version will be given a status of draft while the previous version will remain the Ready version.

