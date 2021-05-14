# Standalone Docker

### Install your PDP

For each PDP configuration, you can simply copy the docker run command and paste it into your terminal and run a new PDP instance.

![PDP instaltion instractions](https://files.readme.io/9bd680e-Screen_Shot_2021-02-18_at_11.07.01.png)

If you didn't create an API key and secret for your PDP yet please do that before - for more information: [Generate Keys for your PDP](../generating-api-keys-for-a-pdp.md).

{% hint style="info" %}
**Reminder**

_Add to the command any environment variable that relevant to the PDP work such as data source connection details._  
Set the relevant port \(or ports if using both HTTP and HTTPS\) - default is 8181
{% endhint %}

### Verify your PDP runs properly

Once you tun the docker command you can view the PDP instance status and additional information on the right part of the PDP information table.

![PDP instance table](https://files.readme.io/cbe0623-Screen_Shot_2021-02-18_at_11.29.37.png)

you can also test by sending POST cURL command to your PDP and view the response retrieve from the PDP in your terminal or in the decision log.

```bash
curl -X POST -d '{"input":{}}' http://<pdp_hostname>:8181/v1/data/<policy_path>
```

![cURL example](https://files.readme.io/3add866-Screen_Shot_2021-02-18_at_11.47.41.png)

###  

