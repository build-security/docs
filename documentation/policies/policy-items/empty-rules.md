# Empty Rules

If you prefer, you can create your own rule in Rego using the empty rule option. After you add a new policy item and select **Empty rule**, it is added to the policy item table. You can then expand this rule in the policy item table to enable you to:

* Set the rule declaration: ALLOW or DENY
* Customize the name of the empty rule to help you identify it better - the rule name will be part of the policy code as a comment above the rule statement
* Add a description for your rule - will be available on build.security control plane only
* Enter the code that will define your rule. As you enter the code, you will see it appear in the Rego code section on the right.
* Enter return message \(optional\) - this message will be part of the decision if the rule will be applied during the authorization request evaluation
* Set the rule status \(options include active, inactive, and monitored\)

![Empty rule](https://files.readme.io/ec20096-emptyrule1.PNG)



