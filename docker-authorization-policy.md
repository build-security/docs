# Docker Authorization Policy

###  Overview

This Quickstart is intended to help give you a basic overview of how to set up and begin working with the build.security control plane. In the following example, we'll show you how to enforce access control on Docker Engine's API.

In short, you'll be able to enforce policies on which Docker commands are allowed / denied to be executed, whether they are sent to the Docker Engine from the Docker CLI or from some other Docker orchestration tool.

{% hint style="warning" %}
#### Note

The Docker Plugin is currently available only on Linux-based machines \(host\) that run the Docker daemon.
{% endhint %}

### Step \#1: Install the authz-docker-plugin

**Create a folder for the configuration:**

```text
$ mkdir -p /etc/docker
```

**Create the config file:  
\*** /etc/docker/pdp\_config.json with the following content:

```text
{
  "pdp_addr": "http://localhost:8181/v1/data/docker/authz",
  "allow_on_failure": true
}
```

Note that the Docker Engine expects a PDP to be deployed on `localhost`, listening on port `8181` and with a specific policy answering to `/docker/authz`.  
Also note the `allow_on_failure` flag which you might want to set to `false` when going to production.

**Install the Docker Plugin:**

```text
docker plugin install buildsecurity/pdp-docker-authz:v0.3 pdp-args="-config-file /pdp/pdp_config.json -debug false"
```

**Add the configuration for the Docker Plugin:**

```text
$ cat > /etc/docker/daemon.json <<EOF
{
    "authorization-plugins": ["buildsecurity/pdp-docker-authz:v0.3"]
}
EOF
```

**Signal the Docker daemon to reload the config:**

```text
$ kill -HUP $(pidof dockerd)
```

### Step \#2: Install a PDP using the build.security control plane

See instructions here: [Creating a New PDP Configuration](policy-decision-points-pdp/creating-a-new-pdp-configuration.md)  
Make sure to run the PDP on the same host that is running the plugged Docker Engine.

### Step \#3: Create a Docker authorization policy

Create a new policy and select Docker authorization policy  
Our recommended and predefined rules for Docker authorization are:

* Check if docker image has latest tag else - DENY
* Check official Docker Hub image else - ALLOW
* Check if docker image has no tag else - DENY

You can change the rule behavior or create a new rule and adjust it for your needs

![Docker authorization policy](https://files.readme.io/0178448-Screen_Shot_2021-02-16_at_20.43.04.png)

{% hint style="info" %}
#### Remember

* The policy package name must be `docker.authz`
* The Policy default behavior is `DENY` - change it in the upper policy bar if you like to.
{% endhint %}

### Step \#4: Publish the Policy

Mark the new policy as "ready" and publish it to the PDP from the previous step using the Publish button \(upper right corner\)

For more information on- [Publish process](projects/publish-project-configuration.md)

### Step \#5: That's it!

Open a terminal, try running the following commands:

```text
docker ps
docker run python:3.8
docker run python:latest
```

The first two commands \(line 1 and line 2\) will be executed, while the third command \(line 3\) will be denied with an appropriate message:

![](https://files.readme.io/4166c2f-docker_latest.png)

You can also view the decision logs screen. There you will see more information about the input, output and more details into why a certain decision was made:

![](https://files.readme.io/95420e7-logs.png)

