# Docker Authorization Plugin

### Introduction

Anyone with permission to access the Docker daemon automatically has permission to run any Docker client command. Similarly, those with access to the Docker daemon can also use the Docker Engine API to contact the daemon.

If you require greater access control, you can create authorization plugins and add them to your Docker daemon configuration. Using an authorization plugin, a Docker administrator can configure granular access policies for managing access to the Docker daemon.

build.security provides and supports an open sources docker authorization plugin that seamlessly integrates with our PDP.

### Basic Principles

Docker’s [plugin infrastructure](https://docs.docker.com/engine/extend/plugin_api/) enables extending Docker by loading, removing and communicating with third-party components using a generic API. The access authorization subsystem was built using this mechanism.

Using this subsystem, you don’t need to rebuild the Docker daemon to add an authorization plugin. You can add a plugin to an installed Docker daemon. You do NOT need to restart the docker daemon to install a new plugin.

An authorization plugin approves or denies requests to the Docker daemon based on both the current authentication context and the command context. The authentication context contains all user details and the authentication method. The command context contains all the relevant request data.

Authorization plugins must follow the rules described in [Docker Plugin API](https://docs.docker.com/engine/extend/plugin_api/). Each plugin must reside within directories described under the [Plugin discovery](https://docs.docker.com/engine/extend/plugin_api/#plugin-discovery) section in docker's documentation.

### Basic Architecture

You are responsible for registering your plugin as part of the Docker daemon startup. You can install multiple plugins and chain them together. This chain can be ordered. Each request to the daemon passes in order through the chain. Only when all the plugins grant access to the resource, is the access granted.

Just run the following to get started quickly:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/build-security/pdp-docker-authz/master/install.sh)" -s -p "http://localhost:9000/v1/data/policy/docker/authz"
```

When an HTTP request is made to the Docker daemon through the CLI or via the Engine API, the authentication subsystem passes the request to the installed authentication plugin\(s\). The request contains the user \(caller\) and commands context. The plugin is responsible for deciding whether to allow or deny the request.

The sequence diagrams below depict an allow and deny authorization flow:

Each request sent to the plugin includes the authenticated user, the HTTP headers, and the request/response body. Only the user name and the authentication method used are passed to the plugin. Most importantly, no user credentials or tokens are passed. Finally, not all request/response bodies are sent to the authorization plugin. Only those request/response bodies where the Content-Type is either text/\* or application/json are sent.

For commands that can potentially hijack the HTTP connection \(HTTP Upgrade\), such as exec, the authorization plugin is only called for the initial HTTP requests. Once the plugin approves the command, authorization is not applied to the rest of the flow. Specifically, the streaming data is not passed to the authorization plugins. For commands that return chunked HTTP response, such as logs and events, only the HTTP request is sent to the authorization plugins.

### Example

Below you can find an example of the JSON that is sent from the authorization plugin and into the Policy Decision Point for the simple command:

```bash
docker run python:3.7
```

Which translates into the following Docker engine API request:

```text
POST /containers/create
```

With the following body as payload:

```javascript
{
  "Hostname": "",
  "Domainname": "",
  "User": "",
  "AttachStdin": false,
  "AttachStdout": true,
  "AttachStderr": true,
  "Tty": false,
  "OpenStdin": false,
  "StdinOnce": false,
  "Env": [
    "FOO=bar",
    "BAZ=quux"
  ],
  "Cmd": [
    "date"
  ],
  "Entrypoint": "",
  "Image": "python:3.7",
  "Labels": {
    "com.example.vendor": "Acme",
    "com.example.license": "GPL",
    "com.example.version": "1.0"
  },
  "Volumes": {
    "/volumes/data": {}
  },
  "WorkingDir": "",
  "NetworkDisabled": false,
  "MacAddress": "12:34:56:78:9a:bc",
  "ExposedPorts": {
    "22/tcp": {}
  },
  "StopSignal": "SIGTERM",
  "StopTimeout": 10,
  "HostConfig": {
    "Binds": [
      "/tmp:/tmp"
    ],
    "Links": [
      "redis3:redis"
    ],
    "Memory": 0,
    "MemorySwap": 0,
    "MemoryReservation": 0,
    "KernelMemory": 0,
    "NanoCPUs": 500000,
    "CpuPercent": 80,
    "CpuShares": 512,
    "CpuPeriod": 100000,
    "CpuRealtimePeriod": 1000000,
    "CpuRealtimeRuntime": 10000,
    "CpuQuota": 50000,
    "CpusetCpus": "0,1",
    "CpusetMems": "0,1",
    "MaximumIOps": 0,
    "MaximumIOBps": 0,
    "BlkioWeight": 300,
    "BlkioWeightDevice": [
      {}
    ],
    "BlkioDeviceReadBps": [
      {}
    ],
    "BlkioDeviceReadIOps": [
      {}
    ],
    "BlkioDeviceWriteBps": [
      {}
    ],
    "BlkioDeviceWriteIOps": [
      {}
    ],
    "DeviceRequests": [
      {
        "Driver": "nvidia",
        "Count": -1,
        "DeviceIDs\"": [
          "0",
          "1",
          "GPU-fef8089b-4820-abfc-e83e-94318197576e"
        ],
        "Capabilities": [
          [
            "gpu",
            "nvidia",
            "compute"
          ]
        ],
        "Options": {
          "property1": "string",
          "property2": "string"
        }
      }
    ],
    "MemorySwappiness": 60,
    "OomKillDisable": false,
    "OomScoreAdj": 500,
    "PidMode": "",
    "PidsLimit": 0,
    "PortBindings": {
      "22/tcp": [
        {
          "HostPort": "11022"
        }
      ]
    },
    "PublishAllPorts": false,
    "Privileged": false,
    "ReadonlyRootfs": false,
    "Dns": [
      "8.8.8.8"
    ],
    "DnsOptions": [
      ""
    ],
    "DnsSearch": [
      ""
    ],
    "VolumesFrom": [
      "parent",
      "other:ro"
    ],
    "CapAdd": [
      "NET_ADMIN"
    ],
    "CapDrop": [
      "MKNOD"
    ],
    "GroupAdd": [
      "newgroup"
    ],
    "RestartPolicy": {
      "Name": "",
      "MaximumRetryCount": 0
    },
    "AutoRemove": true,
    "NetworkMode": "bridge",
    "Devices": [],
    "Ulimits": [
      {}
    ],
    "LogConfig": {
      "Type": "json-file",
      "Config": {}
    },
    "SecurityOpt": [],
    "StorageOpt": {},
    "CgroupParent": "",
    "VolumeDriver": "",
    "ShmSize": 67108864
  },
  "NetworkingConfig": {
    "EndpointsConfig": {
      "isolated_nw": {
        "IPAMConfig": {
          "IPv4Address": "172.20.30.33",
          "IPv6Address": "2001:db8:abcd::3033",
          "LinkLocalIPs": [
            "169.254.34.68",
            "fe80::3468"
          ]
        },
        "Links": [
          "container_1",
          "container_2"
        ],
        "Aliases": [
          "server_x",
          "server_y"
        ]
      }
    }
  }
}
```

Policy can now be enforced on any of the fields in the JSON. Image properties, hostname, identity of the requester, mounted volumes, security flags, CPU and memory limits, Port mappings, CGroups and more.

For a full list of examples and JSON values, see [Docker engine API](https://docs.docker.com/engine/api/latest).

{% hint style="info" %}
**Additional Information**

For more information on the Docker Engine and Docker Authorization plugin - [click here](https://docs.docker.com/engine/extend/) or contact us-[support@build.security](mailto:support@build.security)
{% endhint %}

