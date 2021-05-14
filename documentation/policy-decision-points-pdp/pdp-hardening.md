# PDP Hardening

To keep your policies and authorization data secure, the PDP rejects unauthorized requests.  
This is accomplished by adding a system policy - `system.authz`, which authorizes each request to the PDP, as described in [OPA's Documentation](https://www.openpolicyagent.org/docs/latest/security/#authentication-and-authorization).

With the build.security authorization scheme, users can be authorized to access all the policies they configured. Authorization is based only on the first level of the package name. For example, if a user creates a policy with the package name `my.policy`, that user will be allowed to access any policy under `my`.

Apart from user policies, the `/health` and the `/metrics` endpoints are also available. These are endpoints that expose information about the current state of the PDP.

More information on these endpoints can be found here:

* [health](https://www.openpolicyagent.org/docs/latest/rest-api/#health-api),
* [metrics](https://www.openpolicyagent.org/docs/latest/rest-api/#performance-metrics).

### PDP Hardening Example

For a project containing the following package names:

```text
Default.Policy
a.b.c
a.b.d
```

The generated policy will be:

```text
package system.authz
default allow = false
system_valid_paths := [
  "metrics",
  "health"
]

user_valid_paths := [
  "Default",
  "a"
]

allow {
    input.method == "GET"
    input.path[0] == system_valid_paths[_]
}

allow {
    input.method == "POST"
    input.path[0] == "v1"
    input.path[1] == "data"
    input.path[2] == user_valid_paths[_]
}
```

###  Code Examples

**Unauthorized**:

```text
❯ curl -X GET -d '{"input":{}}' http://localhost:8181/v1/data
{
  "code": "unauthorized",
  "message": "request rejected by administrative policy"
}

❯ curl -X GET -d '{"input":{}}' http://localhost:8181/v1/health
{
  "code": "unauthorized",
  "message": "request rejected by administrative policy"
}

❯ curl -X GET -d '{"input":{}}' http://localhost:8181/v1/policies
{
  "code": "unauthorized",
  "message": "request rejected by administrative policy"
}
```

**Authorized**:  


```text
❯ curl -X GET -d '{"input":{}}' http://localhost:8181/v1/data/Default
{"decision_id":"ad9fc821-763f-47b5-b8aa-a0e92d4b168c","result":{"Policy":{"allow":true}}}%

❯ curl -X GET -d '{"input":{}}' http://localhost:8181/v1/data/a
{"decision_id":"d3b485ff-1596-45ca-b919-79400f1adc06","result":{"b":{"c":{"deny":true},"d":{"allow":true}}}}%

❯ curl -X GET -d '{"input":{}}' http://localhost:8181/health
{}%

❯ curl -X GET -d '{"input":{}}' http://localhost:8181/metrics
# HELP go_gc_duration_seconds A summary of the pause duration of garbage collection cycles.
# TYPE go_gc_duration_seconds summary
go_gc_duration_seconds{quantile="0"} 4.0245e-05
...
```

