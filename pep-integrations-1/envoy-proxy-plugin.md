# Envoy Proxy Plugin

### Introduction

Envoy is an open-source edge and service proxy, designed for cloud-native applications.

When a request comes to the Envoy proxy, it delegates the request's metadata \(name and description\) and payload to an external engine \(PDP\) which is responsible for deciding whether to allow or deny the request reaching upstream.

The following sequence diagram describes the full authorization request flow using Envoy, as mention above:

![Full request flow using Envoy](https://files.readme.io/e10a137-Enovy_-_PDP_1.png)

{% hint style="info" %}
**Additional Information**

For more information on external authorization filter - [click here](https://www.envoyproxy.io/docs/envoy/latest/intro/arch_overview/security/ext_authz_filter.html?highlight=authorization#)
{% endhint %}

###  Envoy HTTP Filter Configuration

* Open the envoy.yaml file.
* Navigate to: filter\_chains &gt; filters &gt; http\_filters.
* Add new ext\_authz filter or create a new one if it is the first filter.

**Configuration Example:**  
Between the comments in the YAML file below, you can view the relevant section that specifies the start and end of the HTTP filter code that needs to be configured. In this example, it directs requests to Google and uses the build.security PDP as an external authorization server.

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
          # The relevant part for configuration in YAML
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
                # next line is a place holder for the PDP Address
                  target_uri: <EXT_AUTHZ_TARGET_URI>  
                  stat_prefix: ext_authz
                timeout: 120s                      
          # End of the relevant part for configuration in YAML
          - name: envoy.filters.http.router
            typed_config: {}
  clusters:
  - name: service_google
    connect_timeout: 0.25s
    type: LOGICAL_DNS
    # Comment out the following line to test on v6 networks
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

{% hint style="warning" %}
#### Remember

**To enable the Envoy proxy to access the external authorization:**

* 1. [Enable the PDP to listen to envoy requests](../project-settings/pdp-settings.md#envoy-integration-settings).
* 1. Replace &lt;EXT\_AUTHZ\_TARGET\_URI&gt; from line 45 with your PDP address and port.

Note: The gRPC port that the PDP listens on is 9191. For example :"10.10.0.1:9191"
{% endhint %}

{% hint style="info" %}
#### Additional information

For more information on Envoy - [click here](https://www.envoyproxy.io/) or contact us-[support@build.security](mailto:support@build.security)
{% endhint %}

