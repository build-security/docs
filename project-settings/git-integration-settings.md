# Git Integration Settings

The [git integration](../projects/commit-project-to-git.md) feature allows an operator to truly treat all policies as code and reflect them in a designated git repository for proper review and approval workflow, complying with SDLC guidelines. In order to enable git integration, the following settings are to be properly filled.

After you complete the fields, or in the future if you change any values in these fields, click **UPDATE** to save the new settings.

| Field | Description |
| :--- | :--- |
| Enabled | Enable / Disable toggle |
| Git Username | The git username |
| Git Access Token | The git access token. Like any other tokens and secrets in the build.security platform, this value is kept encrypted in our database with an AWS KMS key. See below for an example of how to generate an access token in github. |
| Git repository | The target git repository. Only http and https protocols are supported at this point. SSH support is coming soon. |

![git integration settings form](../.gitbook/assets/image%20%2811%29.png)

### How to generate an access token @ github

1. Go to Profile Settings -&gt; Developer Settings -&gt; Personal Access Tokens \([https://github.com/settings/tokens](https://github.com/settings/tokens)\)
2. Click the "Generate new token" button
3. Give the new token a name and choose the "repo" scope, as shown in the image below.
4. Copy the token and paste it in the build.security git integration settings form

![Required scopes for access token \(github\)](../.gitbook/assets/image%20%287%29.png)



