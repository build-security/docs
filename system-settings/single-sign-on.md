# Single Sign-On

If you are not familiar with Single Sign-On, please read [https://auth0.com/docs/sso](https://auth0.com/docs/sso) 

In a nutshell, SSO allows our customers to manage all of their users and appropriate roles in one place, across all of their vendors.

This guide uses the field names as they are displayed in Okta. Field names may vary over different identity providers, but most likely be similar.

{% hint style="info" %}
**Note**

Currently, we support only the OpenID Connect protocol for Single Sign-On. If you use other protocol \(e.g, SAML\), please contact [support@build.security](mailto:support@build.security)
{% endhint %}

To define an identity provider, please click on the "System Settings" button on the navigation menu, then click on the "Single Sign On" button.

![Single Sign-On menu](../.gitbook/assets/image%20%2817%29%20%281%29.png)

### Defining build.security in your chosen Identity Provider

In Okta, you will create a new application, that will connect with build.security.

* If your identity provider lets you choose application type, please choose `Single Page App (SPA)`
* If your identity provider lets you choose `Allowed grant types`, please choose `Authorization Code`, `implicit`, `Allow ID Token with implicit grant type`

![](../.gitbook/assets/image%20%2824%29%20%282%29.png)

* Please copy the `build.security Redirection URL` field and paste it in your identity provider, under `Login redirect URIs`.  This is the URL that your identity provider will redirect your users to after a successful authentication, so your identity provider must know that specific URL in advance.

![Logout redirect URIs &amp; Initiate login URI are not relevant](../.gitbook/assets/image%20%2818%29.png)

* Copy the Client ID from your identity provider and paste it in build.security's console.

![](../.gitbook/assets/image%20%2819%29.png)

In Okta, you will find these fields under your application that you want to connect with build.security.

### Redirection URL

Your identity provider should supply an `Authorize URL`. You should complete that URL as follows:

* `response type` - id\_token
* `response mode` - fragment
* `scope` - `openid` `email` `profile`
* `redirect uri` - &lt;hostname of build.security&gt; \(eg. https://console.poc.build.security\)

  Paste that URL in build.security under `Redirection URL`

* `state` - Please **remove** the state from the redirection url! We will generate this field. 

![](../.gitbook/assets/image%20%2822%29.png)

### Discovery URL

Also known as well-known URL. That is the URL that helps build.security to verify the authentication process against your identity provider. Some identity providers supply that URL for all customers under the same template. 

For example, in okta, that URL is: `https://<YOUR_DOMAIN>.okta.com/.well-known/openid-configuration`

