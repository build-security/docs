# Policy Items

A policy is built by defining one or more policy items. Some policies can be adequately expressed with a single policy item. Others may require a combination of several policy items.

Policy items are basically snippets of code written in Rego combined to create OPA-based policies. There are three types of policy items that can be defined and customized in the control plane. These include:

* Rules from templates
* Empty rules
* Custom blocks

![Policy item types](https://files.readme.io/4be19c2-Policy_Items_types.png)



<table>
  <thead>
    <tr>
      <th style="text-align:left">Policy Type</th>
      <th style="text-align:left">
        <p></p>
        <p>Explanation</p>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">Rules from templates</td>
      <td style="text-align:left">For each integration, build.security provides a number of basic or common
        rules that are typical for an organization to include in their authorization
        policies. These are rules that are written in Rego for you for each of
        the relevant integrations. These rules already contain the logic within
        them and only require you to input specific
        <br />
        <br />You can select one of these rules and, where necessary, define a parameter
        (for example, if you wanted to allow or deny destination addresses, you
        would need to provide a list of IP addresses).</td>
    </tr>
    <tr>
      <td style="text-align:left">Empty rule</td>
      <td style="text-align:left">An empty rule enables you to define allow/deny rules where you set the
        rule data, all the logical components that will build the rule, etc. You
        can also set a return message that be included in the authorization response.
        <br
        />
        <br />If defined, this message will appear in the Results area in the decision
        log table (where it can, for example, help you understand which policy
        was used to evaluate the authorization decision) and can be used as needed
        by your organization&apos;s application.</td>
    </tr>
    <tr>
      <td style="text-align:left">Custom block</td>
      <td style="text-align:left">A custom block offers you a flexible place to write you own Rego code.
        In this block, you can write your own rules, functions, declare statements,
        etc.</td>
    </tr>
  </tbody>
</table>

When you add a new policy item, it is immediately added to the policy items table is expanded, enabling you to see the various elements of the policy item and what you may need to do to properly enable the rule. For example, you might need to define the HTTP method, add port number information, etc.

### Policy Items Table

The policy item table includes the following elements:

| Option | Explanation |
| :--- | :--- |
| Type | Type options include: Allow, Deny, or Custom. |
| Name | The name of the policy item, as defined when the policy item was created. |
| Creating Date \(UTC\) | The date and time the policy item was created \(in UTC\). |
| Last Update \(UTC\) | The last date and time the policy item was updated \(in UTC\). |
| Status | Options include Active, Inactive, Monitored. For more information, see [Rule Status](https://docs.build.security/docs/rule-statuses-and-versions). |
| Actions | Click the kebab \(three vertical dots\) to access the Delete option. For more information, see Managing Policy Items |

### Errors in Policy Items

As you are creating a policy item, you will be notified if an error in the code has been detected. There are several ways that you can know when this has happened. These include:

* In the Type column of the policy items table, an error icon will appear

![Error icon in type column](https://files.readme.io/c00bd4b-error-type.PNG)

The Expanded/Unexpanded icon of the policy code panel will display an error icon.

![Policy code icon](https://files.readme.io/caa0caa-errors.png)

An error window will appear in the lower part of the policy code panel indicating the line where the error has occurred as well as an indication of the problem.

![Error message display](https://files.readme.io/f9adbae-errorwindow.PNG)



