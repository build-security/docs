# Generating API Keys for a PDP

**To generate API keys for an existing PDP:**

1. On the control plane, select **Policy Decision Points**.
2. Use the **&gt;** next to the PDP for which you wish to generate an API key. The configuration details panel will appear.
3. Click **GENERATE API KEY**.

After processing your request, your API key and secret will be available to view. Also, you can simply copy and paste the contents in a docker run command to run a new PDP using these credentials.

![PDP credentials](https://files.readme.io/2645747-PDP-apikey.png)

{% hint style="warning" %}
**Reminder**

The API secret is displayed only once. build.security does not store the PDP secret in its backend. You can click **Download** to download a .csv file which will contain both your API key and the secret.
{% endhint %}

Click **Dismiss** to close the notice. Although the secret cannot be accessed again, the API key can be accessed in the future by expanding the PDP using the **&gt;** icon.

{% hint style="info" %}
**Note**

Note that if you are using a data source that requires a password \(such as PostgreSQL\), make sure that the relevant environment variable has been added as part of the deployment command.
{% endhint %}

