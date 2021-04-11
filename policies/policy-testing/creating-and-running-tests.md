# Creating a Policy Unit Test

To view existing tests or create a new policy unit test, you can access the test screen by clicking on the test icon next to the policy name you wish to test.

![Policy unit testing icon](../../.gitbook/assets/image%20%288%29%20%281%29.png)

The list of tests offers two buttons: **Run Tests** and **New Test**. The table displays the following columns:

* Test name
* Last run \(UTC\)
* Last resolution
* Task duration \(msec\)
* Status

**To create a new test:**

1. Click the **+ NEW TEST** button. This will create a blank new test below any existing tests.
2. Enter a name and description for the test \(optional\). A default name is given but can be changed now or in the future.
3. In the **Status** column, by default, the test is given an **Active** status. You can change this to **Inactive**, if you wish.
4. In the **Input** box, enter the code for the authorization request input that you would like to test.
5. In the **Expected Result** box, enter the code for what you would expect the result to be for this inquiry. Note that the expected results is "partially" compared with the actual result. So if, for example, the actual results looks like:

```javascript
{
    "allow": true,
    "permissons": ["iam.read", "iam.edit"]
}
```

 The expected results can look like:

```javascript
{
    "allow": true
}
```

Or it could also look like:

```javascript
{
    "allow": true,
    "permissons": ["iam.read"]
}
```

The test is utilizing [build.json\_partial\_compare](../../library/built-in-functions/build.json_partial_compare.md) builtin.

You can an additional test by simply clicking on the **+ NEW TEST** button. A new test window will open below the first on you have created, enabling you to add another test. If the test is a variation of the one that you just created, you can copy some or all of the code and paste it into the input window.

Once you have finished creating the test, you can [run the test ](running-a-policy-unit-test.md)at this time, or at any time in the future.

![Policy testing screen \(showing 3 tests\)](../../.gitbook/assets/image%20%286%29.png)

