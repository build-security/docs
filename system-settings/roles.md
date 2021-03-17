# Roles



Roles are used in build.security to allow users different permissions. There are five admin roles granted to users to enable them to view and/or manage various elements within the build.security platform.

Each user's role is assigned when the system admin creates the user and can be changed as needed by editing the user configuration.

| Role | Role Permissions |
| :--- | :--- |
| System Admin | The highest level user of the build.security, system admins are responsible for managing all system settings, managing projects \(creating, deleting, etc.\) and have full permissions in all projects. |
| Project Admin | Includes all permissions for policy admin, plus the ability to manage all other settings within the project such as: _PDPs_ Data sources, \* Full access to all aspects of the project settings. |
| Policy Admin | Includes all permissions for policy editor, plus marking policy versions as ready. |
| Policy Editor | Includes all permissions for policy viewer, plus: the ability to create and manage all the policy version items such as rules, functions, and global scope definitions. |
| Policy Viewer | View policy versions, PDPs, data sources, and decision logs within a project |

{% hint style="info" %}
**Project-Based Permissions**

\Aside from the permissions that the user is granted based on the assigned role, system admins can also grant permissions based on projects. This would allow or deny users to view and/or perform tasks in one or more selected projects or in all projects.
{% endhint %}

