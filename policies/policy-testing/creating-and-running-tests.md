# Creating and Running Tests

To view existing tests or create a new one, you can access the test screen by clicking on the test icon next to the policy name you wish to test.

![Beside the policy name: test icon and project settings icon](../../.gitbook/assets/policytestingicon.png)

The list of tests offers two buttons: **Run Tests** and **New Test**. The table displays the following columns:

* Test name
* Last run \(UTC\)
* Last resolution
* Task duration \(msec\)
* Status

### Creating a New Test

{% hint style="info" %}
To create or run a test, you must have an online PDP instance. For more information, see [Policy Decision Points \(PDP\)](../../policy-decision-points-pdp/).
{% endhint %}

**To create a new test:**

1. Click the **+ NEW TEST** button. This will create a blank new test below any existing tests.
2. Enter a name and description for the test \(optional\). A default name is given but can be changed now or in the future.
3. In the **Status** column, by default, the test is given an Active status. You can change this to Inactive, if you wish.
4. In the **Input** box, enter the code for the authorization request input that you would like to test.
5. In the **Expected Result** box, enter the code for what you would expect the result to be for this inquiry. 

### Running an Existing Test

