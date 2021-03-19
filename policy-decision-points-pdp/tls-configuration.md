# TLS Configuration



Any PDP instance can receive HTTPS requests if given a certificate and a private key.

If you have a certificate and private key that you would like the PDP to use:

1. Assign the following names to the certificate and key: `public.crt` and `private.key`
2. Place them in a directory called `https` under your working directory.
3. Run the PDP deployment command from the server using the following syntax:

```text
docker run \
  -p 8181:8181 \
  -d \
  -e API_KEY="..." \
  -e API_SECRET="..." \
  -e CONTROL_PLANE_ADDR="https://api.dev.build.security/v1/api/pdp" \
  -e PDP_LOG_LEVEL=error \
  --mount type=bind,source="$(pwd)"/https,target=/app/https \
  buildsecurity/pdp sh -c "./opa_plus run --server --log-level error --skip-version-check --config-file config.yaml --tls-cert-file https/public.crt --tls-private-key-file https/private.key"
```

### Using Insecure HTTP Connections - TLS Enabled

By default, OPA ignores insecure HTTP connections when TLS is enabled. To allow insecure HTTP connections, in addition to HTTPS connections, run the PDP deployment command from the server in the following form:

```text
docker run \
  -p 8181:8181 \
  -p 8282:8282 \
  -d \
  -e API_KEY="..." \
  -e API_SECRET="..." \
  -e PDP_LOG_LEVEL=error \
  -e CONTROL_PLANE_ADDR="https://api.dev.build.security/v1/api/pdp" \
  --mount type=bind,source="$(pwd)"/https,target=/app/https \
  buildsecurity/pdp sh -c "./opa_plus run --server --log-level error --skip-version-check --config-file config.yaml --tls-cert-file https/public.crt --tls-private-key-file https/private.key --addr https://0.0.0.0:8181 --addr http://0.0.0.0:8282"
```

This will cause the PDP to listen to HTTP traffic on port `8282`, and to HTTPS traffic on port `8181`.

### Validation using cURL

To validate that everything works as expected, you can use cURL:

**1. HTTP:**

```text
curl http://localhost:8282/v1/data
```

**2. HTTPS**

```text
curl -k https://localhost:8181/v1/data
```

{% hint style="info" %}
**Note**

cURL’s `-k/--insecure` flag is only needed if you are using a self-signed certificate \(or any certificate that was not signed by a trusted CA\).
{% endhint %}

