# Envoy Proxy Integration

### Introduction

Envoy is an open-source edge and service proxy, designed for cloud-native applications.

When a request comes to the Envoy proxy, it delegates the request's metadata \(name and description\) and payload to an external engine \(PDP\) which is responsible for deciding whether to allow or deny the request reaching upstream.

The following sequence diagram describes the full authorization request flow using Envoy, as mention above:

![Full request flow using Envoy](https://files.readme.io/e10a137-Enovy_-_PDP_1.png)

{% hint style="info" %}
**Additional Information**

For more information on external authorization filter - [click here](https://www.envoyproxy.io/docs/envoy/latest/intro/arch_overview/security/ext_authz_filter.html?highlight=authorization#)
{% endhint %}

###  Prerequisites

This tutorial requires docker-compose \(tested on 1.27.4\)

### 1. Enable gRPC on the PDP settings

In the [PDP settings screen](../project-settings/pdp-settings.md#envoy-integration-settings), make sure gRPC is enabled.

### 2. Grab API Key and Secret for your PDP

In the Policy Decision Points screen, grab an [API and secret](../policy-decision-points-pdp/generating-api-keys-for-a-pdp.md).

### 3. Create Envoy config file

Create the following `config.yaml` file. The configuration instructs the proxy to listen on port `10000` and to behave as a reverse proxy to `google.com`. Envoy would also delegate all incoming requests to the sidecar PDP in order to allow / deny the access

```yaml
admin:
  access_log_path: /tmp/admin_access.log
  address:
    socket_address:
      protocol: TCP
      address: 127.0.0.1
      port_value: 9901
static_resources:
  listeners:
  - name: listener_0
    address:
      socket_address:
        protocol: TCP
        address: 0.0.0.0
        port_value: 10000
    filter_chains:
    - filters:
      - name: envoy.filters.network.http_connection_manager
        typed_config:
          "@type": type.googleapis.com/envoy.config.filter.network.http_connection_manager.v2.HttpConnectionManager
          stat_prefix: ingress_http
          route_config:
            name: local_route
            virtual_hosts:
            - name: local_service
              domains: ["*"]
              routes:
              - match:
                  prefix: "/"
                route:
                  host_rewrite: www.google.com
                  cluster: service_google
          http_filters:
          - name: envoy.ext_authz
            typed_config:
              "@type": type.googleapis.com/envoy.config.filter.http.ext_authz.v2.ExtAuthz
              with_request_body:
                max_request_bytes: 8192
                allow_partial_message: false
              failure_mode_allow: false
              grpc_service:
                google_grpc:
                  target_uri: pdp:9191
                  stat_prefix: ext_authz
                timeout: 120s
          - name: envoy.filters.http.router
            typed_config: {}
  clusters:
  - name: service_google
    connect_timeout: 0.25s
    type: LOGICAL_DNS
    dns_lookup_family: V4_ONLY
    lb_policy: ROUND_ROBIN
    load_assignment:
      cluster_name: service_google
      endpoints:
      - lb_endpoints:
        - endpoint:
            address:
              socket_address:
                address: www.google.com
                port_value: 443
    transport_socket:
      name: envoy.transport_sockets.tls
      typed_config:
        "@type": type.googleapis.com/envoy.api.v2.auth.UpstreamTlsContext
        sni: www.google.com
```

### 4. Create docker-compose file

In order to quickly spin up the Envoy and the PDP dockers and their common network, create the following docker-compose file, **while using the API key and secret from step 1**:

```yaml
version: "3.8"
services:
  envoy:
    image: envoyproxy/envoy:v1.16.0
    ports:
      - "9901:9901"
      - "10000:10000"
    networks:
      - dev
    volumes:
      - "./config.yaml:/etc/envoy/envoy.yaml"
    command:
      - --log-level error
      - --component-log-level ext_authz:trace,connection:trace,grpc:trace
      - --config-path /etc/envoy/envoy.yaml
  pdp:
    image: buildsecurity/pdp:latest
    networks:
      - dev
    environment:
      - API_KEY=rHlKxxnyb45AVkhGtXLQQmiAZLHie3FH
      - API_SECRET=****
      - CONTROL_PLANE_ADDR=https://api.dev.build.security/v1/api/pdp
      - MYSQL_PASSWORD=""
networks:
  dev:

```

{% hint style="warning" %}
**Remember**

Do not forget to to replace **API\_KEY** and **API\_SECRET** with your own
{% endhint %}

### 5. Start the proxy and the PDP

execute `docker-compose up` , output shall be:

![docker-compose for envoy + pdp](../.gitbook/assets/image%20%284%29.png)

### 6. Test it!

In the build.security control plane:

1. Observe your just new PDP in the Policy Decision Points screen
2. Create a new Envoy policy
3. Change the default behaviour of the policy to be `ALLOW`
4. [Publish](../projects/publish-project-configuration.md) changes to the PDP
5. Open a browser and go to `localhost:10000`
6. Observe the newly created [decision logs](../decision-logs/)

![Envoy decision logs](../.gitbook/assets/image%20%283%29.png)

### 7. Change the default policy and test again...

1. Change the default behaviour of the policy to `DENY`
2. Browse again
3. This time - the access shall be denied



{% hint style="info" %}
#### Additional information

For more information on Envoy - [click here](https://www.envoyproxy.io/) or contact us-[support@build.security](mailto:support@build.security)
{% endhint %}

