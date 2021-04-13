# Single Sign-On
If you are not familiar with Single Sign-On, please read https://auth0.com/docs/sso
This guide uses the field names as they are displayed in Okta.
Field names may vary over different identity providerd, but most likely be similiar.

{% hint style="info" %}
**Note**

Currently we support only OpenID Connect protocol for Single Sign-On.
If you use other protocol (e.g, SAML), please contact support@build.security/
{% endhint %}

To define an identity provider, please click the "System Settings" button on the navigation menu, then click on the "Single Sign On" button.
(Add picture)

## Defining build.security at your identity provider
In Okta, you will create a new application, that will connect with build.security.
* If your identity provider let you choose application type, please choose "Single Page App (SPA)"
* If your identity provider let you choose "Allowed grant types", please choose "Authorization Code", "implicit", "Allow ID Token with implicit grant type"
* Please copy "build.security Redirection URL" field and paste it in your identity provider, under "Login redirect URIs".
This is the URL that your identity provider will redirect your users to, after a successfull authentication, so your identity provider must allow that specific URL.
In Okta, you will find that field under your application that you want to connect with build.security
* Copy the Client ID and paste in build.security

## Redirection URL
Your identity provider should supply an "Authorize URL". You should complete the URL as follows:
* response type - "id_token"
* response mode - "fragment"
* scope - "openid%20email%20profile"
* redirect uri - https%3A%2F%2Fconsole.poc.build.security
Paste that URL in build.security under "Redirection URL"

## Discovery URL
Also known as well-nown URL. That is, the URL that help build.security to verify the authentication process against your identity provider. 
Some identity providers supply that url for all customers under the same tamplate.
For example, in okta, that URL is: https://<YOUR_DOMAIN>.okta.com/.well-known/openid-configuration