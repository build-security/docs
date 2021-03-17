# Decision Log Settings

The decision log screen displays an up-to-date listing of all authorization decisions received in the field. You can configure the decision log on the project settings screen. Select _Decision Log_ to see the settings options. These include:

* Configuring whether the PDP should collect and store decision logs
* Setting the the frequency for when the decision log will be updated
* Setting **Input / Output** to mask any sensitive data before it gets sent from the PDP

After you complete the fields, or in the future if you change any values in these fields, click **UPDATE** to save the new settings.

| Decision logs | Enable or disable whether the PDP collects and stores decision logs.  Note that disabling the decision logs will improve the evaluation time of your authorization request but will prevent you from gaining visibility retrospective. |
| :--- | :--- |
| Min delay \(seconds\) | The minimum interval \(in seconds\) between times that the PDP waits before uploading a new chunk of the decision logs. |
| Max delay \(seconds\) | The maximum interval \(in seconds\) between times that the PDP waits before uploading a new chunk of the decision logs. |
| Input/Output masking | Policy queries may contain sensitive information \(passwords, account numbers, credit card numbers, social security or other identification numbers\). These details can be configured in the Input/Output box so that sensitive data is masked before being sent to the control plane. See below for more information on masking options. |
| Rule tracing | Enables Rule tracing in the decision log table. For more information, see [Rule Tracing](https://docs.build.security/docs/policy-rule-tracing). |

### Decision Log Masking

In the decision log, the full input and result content of the authorization request / response are stored. To hide sensitive information from the decision log, you can specify which fields will be hidden \(or masked\) in the decision log.

There are a few restrictions on the JSON Pointers that the PDP will mask:

* Pointers must be prefixed with /input or /result.
* Pointers may be undefined. For example /input/name/first in the example above would be undefined. Undefined pointers are ignored.
* Pointers must refer to object keys. Pointers to array elements will be treated as undefined. For example /input/emails/0/value is allowed but /input/emails/0 is not.

More information regarding decisions log masking can be found in the [OPA documentation](https://www.openpolicyagent.org/docs/v0.13.5/decision-logs/#masking-sensitive-data)

{% hint style="info" %}
**Note**

Since log masking is done on the PDP side, after changing any one of the settings - a **PUBLISH** operation is required.
{% endhint %}



![Decision log settings](https://files.readme.io/a9ff648-ruletracingprojsettings.PNG)



