# Custom Blocks

The Custom block policy item enables you to write your own custom block using Rego language. Whatever is supported by the Rego language can be used in the custom block and will then be part of your policy.

After you add a new policy item and select **custom block**, it is added to the policy item table. You can then expand this rule in the policy item table to enable you to:

* Customize the name of the Custom Block to help you identify it better - the block name will be part of the policy code as a comment above the block statement.
* Add a description for your block. This will be available in the build.security control plane only and has no affect on the policy itself.
  * Enter the Rego code that will define your block.
  * Set the block status \(options include active, inactive\).

![Custom block rule](https://files.readme.io/3dfa263-customblockrule.PNG)

{% hint style="info" %}
**Hint**

Custom block policy items cannot be monitored. For more information, see [Policy Item Statuses](https://docs.build.security/docs/rule-statuses-and-versions).
{% endhint %}



