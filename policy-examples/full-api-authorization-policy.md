# Full API Authorization Policy

### Policy use case

To demonstrate our API authorization policy, we'll use a simple example.

We will run a policy that handles HTTP requests from your application and pass to the PDP using Envoy proxy.

To identity attributes/role will be part of JWT token that is part of the authorization header - `request.http.headers.authorization`  
The method and the API that the identity tries to operate will be detailed in `request.http.method` and `request.http.path`

{% hint style="info" %}
#### Not using Envoy proxy?

If you are using one of build.security SDK\`s or middleware as your PEP the request structure is a bit different - click here to [read more](https://docs.build.security/docs/policy-examples#the-authorization-request-structure) about that
{% endhint %}

**We will demonstrate a simple policy:**  
Enables **POST** methods **only** to identities that as part of the JWT claims carries **payload.role == "admin"**

* Enables **GET** methods to **all identities.**
* **All other** requests should be **denied.**

### Building the identity profile

The identity attributes decoded in a JWT token - we will decode the payload claims and use those to identify the identity role.

For this example, you can use the following JWT tokens

1. Alice is with the role `admin` as required to perform POST API requests.

**JWT - `eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJuYW1lIjoiYWxpY2UiLCJyb2xlIjoiYWRtaW4ifQ.YMQDHwn4nBeTU6axg8gDAwegNkLb0uW_cQfv-Pit794`**

![JWT with role==&quot;admin&quot;](https://files.readme.io/b57348c-admin_jwt.png)

Alice is with the role `user`, request with this role should be denied for POST requests but can perform GET API requests

**JWT - `eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJuYW1lIjoiYWxpY2UiLCJyb2xlIjoidXNlciJ9.XWDFKlUpoNCvhmXvNDsXsEPMFouvHUDO1nPvHpHW5FY`**

![JWT with role==&quot;user&quot;](https://files.readme.io/c646814-ujwt_with_user.png)

You can simply create your own JWT tokens - [here](https://jwt.io/).

### Identify the resource & action

In our API authorization use case the **Resource** is the **API request** the identity try to use and the **Action** is the **Method**.

### Policy Rules

After having all of this information in hand we can simply add rules to our - how simple - simple like that

For the **first rule** that enables **POST** methods **only** to identities that as part of the JWT claims carries **payload.role == "admin"** we will create an **empty rule** and paste the following code:

```scala
claims.role == "admin"
input.request.http.method == "POST"
```

For the **second rule** that enables usage of **GET** methods to **all identities.** we will use one of build.security **predefined rules** that handle the request method and set the method `GET`

And the **third rule** that blocks all the rest of the requests will be handled by the policy **default setting** set to DENY:

![API authorization policy](https://files.readme.io/9960490-Screen_Shot_2021-03-06_at_19.04.14.png)



