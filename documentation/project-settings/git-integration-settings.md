# Git Integration Settings

The [Git integration](../projects/commit-project-to-git.md) feature allows an operator to truly treat all policies as code and reflect them in a designated Git repository to create a proper review and approval workflow, complying with SDLC guidelines. To enable Git integration, the settings in the following table need to be completed.

After you complete the fields, or in the future if you change any values in these fields, click **UPDATE** to save the changes. If build.security is unable to connect to your Git repository, you will receive a message saying "Unavailable: Check Git availability". Check your credentials and then update build.security.

<table>
  <thead>
    <tr>
      <th style="text-align:left">Field</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">Enabled</td>
      <td style="text-align:left">Enable / Disable toggle</td>
    </tr>
    <tr>
      <td style="text-align:left">Git Access Token</td>
      <td style="text-align:left">
        <p>The Git access token.</p>
        <p>Like any other tokens and secrets in the build.security platform, this
          value is kept encrypted in our database with an AWS KMS key. See below
          for an example of how to generate an access token in your Git Hosting Service.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Git Repository</td>
      <td style="text-align:left">
        <p>The target Git repository URL.</p>
        <p>Only HTTP and HTTPS protocols are supported at this point. SSH support
          is coming soon.</p>
      </td>
    </tr>
  </tbody>
</table>

![Git integration settings form](../../.gitbook/assets/image%20%2812%29.png)

### How to generate an access token @ GitHub

1. Go to **Profile Settings -&gt; Developer Settings -&gt; Personal Access Tokens** \([https://github.com/settings/tokens](https://github.com/settings/tokens)\)
2. Click the **Generate new token** button.
3. Give the new token a name and select the "**repo**" scope, as shown below.
4. Click the **Generate token** button at the bottom.
5. Copy and paste the token into build.security Git integration settings page.

![Required scopes for access token \(GitHub\)](../../.gitbook/assets/image%20%287%29.png)

### How to generate an access token @ GitLab

1. Under the user avatar on the right upper side of the screen Go to Profile Settings -&gt; Access Tokens \([https://gitlab.com/-/profile/personal\_access\_tokens](https://gitlab.com/-/profile/personal_access_tokens)\)
2. Set the access token:
   1. Token name 
   2. Expression date \(optional\)
   3. Choose the "read\_repository" and "write\_repository" scopes, as shown in the image below.
3. Click on "**Create personal access token**".
4. Copy and paste the token into build.security Git integration settings page.

![Personal acess token \(GitLab\)](../../.gitbook/assets/image%20%2813%29%20%281%29.png)

