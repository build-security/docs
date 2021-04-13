# Single Sign-On
If you are not familiar with Single Sign-On, please read https://auth0.com/docs/sso
This guide uses the field names as they are displayed in Okta.
Field names may vary over different identity providers, but most likely be similar.

{% hint style="info" %}
**Note**

Currently, we support only the OpenID Connect protocol for Single Sign-On.
If you use other protocol (e.g, SAML), please contact support@build.security/
{% endhint %}

To define an identity provider, please click on the "System Settings" button on the navigation menu, then click on the "Single Sign On" button.
(Add picture)

## Defining build.security at your identity provider
In Okta, you will create a new application, that will connect with build.security.
* If your identity provider lets you choose application type, please choose `Single Page App (SPA)`
* If your identity provider lets you choose `Allowed grant types`, please choose `Authorization Code`, `implicit`, `Allow ID Token with implicit grant type`
* Please copy the `build.security Redirection URL` field and paste it in your identity provider, under `Login redirect URIs`.
This is the URL that your identity provider will redirect your users to, after successful authentication, so your identity provider must allow that specific URL.
In Okta, you will find that field under your application that you want to connect with build.security
* Copy the Client ID and paste it in build.security

## Redirection URL
Your identity provider should supply an `Authorize URL`. You should complete that URL as follows:
* `response type` - "id_token"
* `response mode` - "fragment"
* `scope` - "openid%20email%20profile"
* `redirect uri` - https%3A%2F%2Fconsole.poc.build.security
Paste that URL in build.security under `Redirection URL`

## Discovery URL
Also known as well-known URL. That is the URL that helps build.security to verify the authentication process against your identity provider. 
Some identity providers supply that URL for all customers under the same template.
For example, in okta, that URL is: https://<YOUR_DOMAIN>.okta.com/.well-known/openid-configuration
