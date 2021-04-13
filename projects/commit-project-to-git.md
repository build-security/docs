# Commit Project to Git

The Git integration feature allows an operator to truly treat all policies as code and reflect them in a designated Git repository. This enables you to:

* Perform a proper review and approval workflow
* Comply with SDLC guidelines

To enable Git integration, see the [git integration settings screen](../project-settings/git-integration-settings.md).

{% hint style="success" %}
Make sure to read our [guide](../working-with-envs.md#overview) around best practices for development and production environments.
{% endhint %}

At any time, an operator can choose to commit the project settings and policies to a designated Git branch. build.security's control plane acts as a "Git client". When clicking the "commit" button, the following commands take place:

1. The operator is asked to provide the remote branch name
2. If the branch exists in the remote repository, build.security's git client will `pull` latest and `commit` the changes.
3. If the branch do not exist in the remote repository, build.security's git client will create a new branch with the same name under the repository's `default` branch, and then will follow stop \#2 above.

{% hint style="warning" %}
**Important - use only build.security to modify policies**

It is highly recommended to author and change configuration settings from within the build.security control plane, and use the git integration for review and auditing perspectives only. 

In certain environments, the project's artifacts in git can be used as source of truth.
{% endhint %}

### .buildsecurity git YAML file

When pulling the remote git branch, build.server's git client looks for a `.buildsecurity` yaml file, which can hold basic information on where to store the project's artifacts within the branch.

Format:

```yaml
version: 0.1
path: my_policies_folder
```

| Field | Description | Default value |
| :--- | :--- | :--- |
| version | The version of the YAML file |  |
| path | The relative path to store the project's artifacts in | policies |

In order to enable the git integration feature, follow the instructions on the [git settings screen](../project-settings/git-integration-settings.md).

