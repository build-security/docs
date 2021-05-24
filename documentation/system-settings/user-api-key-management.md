# User API Key Management

All actions that can be done in the build.security control plane are available through a RESTful API interface as well. For authentication of the request, you will need to generate an API key and secret. The process for doing this is detailed below.

### Creation of the First User API Key

If you have not yet generated an API key for a user, you can do this on the user management screen.

**To create the first User API key:**

Click the expand arrow to the left of the user for whom you wish to generate the API key. If the user already has a key, the key value, creation date and last time it was updated will be displayed. If no API key has been created, the following information will be displayed:

![Generate API Key](https://files.readme.io/2772593-needAPI.PNG)

Click the **Generate API Key +** button. The build.security system will generate the key and display the following:

![API Key and Secret](https://files.readme.io/0f8c38d-yourapikey.png)

{% hint style="info" %}
**Note**

The API key and secret are only visible in this area. Once you compact the expand arrow, the secret will not be visible again. You can, however, generate a new one for an existing API key or delete the API key entirely and create a new key and secret as needed.
{% endhint %}

Click **Download** to download the key. A .csv file will be created and a dialog box will open, enabling you to download the file and save it locally. Once completed \(or if you do not wish to download the file at this time\), click **Dismiss**.

