# Policy Testing

build.security enables you to create your authorization policies as code. One of the major benefits of doing this is the ability to unit test each section of the code to ensure that it behaves as you would expect. As you build or make changes to your policies, it is likely that you will want to test them to ensure they are working properly. 

You can also test edge cases that are unlikely to be tested in "normal" scenarios but might show up in extreme or unusual cases easily in build.security. And finally, yet another benefit of the policy-as-code method in build.security is that future policy changes can also be verified quickly to avoid any opportunity for broken code to introduce the effectiveness of the policies you have created for your organization.

build.security enables you to test your policies in three different ways:

* The **policy evaluation playground** enables you to input the text of an authorization request and see what the output would be. This is a simulation, a dry run, and is not treated as an actual request, is not enforced, and does not appear in the decision log. Upon seeing the output, you can decide whether this policy is behaving as you would expect. For more information, see [Policy Evaluation Playground](../policy-evaluation-playground.md).
* The **policy unit testing** option, based on the [policy testing in OPA](https://www.openpolicyagent.org/docs/latest/policy-testing/), enables you to enter the input and output of an authorization request to confirm the full lifecycle of the request. As with the policy evaluation playground, it does not impact on the decision logs or present any enforcement issues. For more information, see [Policy Unit Testing](../../../quickstarts/testing-your-policy/policy-unit-testing.md).
* Using the **monitored status** for a predefined rule or an empty rule enables you to test how that rule would impact your policy without impacting your current authorization policy. The results of this monitoring can be seen in the decision logs table. For more information, see [Rule Tracing](../../impact-analysis/rule-tracing.md).

{% hint style="info" %}
You can perform policy unit testing by clicking on the test icon beside the policy name in the navigation panel. For more information, see [Creating and Running Tests](creating-and-running-tests.md).
{% endhint %}

#### Policy Testing Screen <a id="policy-testing-screen"></a>

The policy unit testing screen features two buttons: **Run Tests** and **New Test**. The table below the buttons displays a list of currently defined tests, including the following information for each test:‌

* Test name
* Last run \(UTC\)
* Last resolution
* Task duration \(msec\)
* Status

![Policy unit testing screen](../../../.gitbook/assets/image%20%285%29.png)

