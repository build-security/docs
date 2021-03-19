# PDP debugging

In order to have more visibility into the decision making process within the PDP and / or troubleshooting, there's an option to turn on debug logs.

Debug logs are sent to the standard output \(stdout\) and can be viewed through the `docker logs` command.

In order to turn on the debug logs, just define an environment variable with the name `PDP_LOG_LEVEL` with value `debug`. 

Example command for standalone docker:

```text
docker pull buildsecurity/pdp; \
docker run \
  -p 8181:8181 \
  -d \
  -e API_KEY="xHRdaKEbaSc9ps7nqC9h39ZgUQbNar8W" \
  -e API_SECRET="***************" \
  -e PDP_LOG_LEVEL=debug \
  -e CONTROL_PLANE_ADDR="https://api.dev.build.security/v1/api/pdp" \
buildsecurity/pdp
```

{% hint style="warning" %}
**Note**

The verbose nature of the debug logs has a great impact on performance, hence the default log level is `error`
{% endhint %}

