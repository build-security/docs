# Kubernetes

### Getting started

To deploy a new PDP with Kubernetes, the first step is to create the PDP within build.security - see [Creating a new PDP](../creating-a-new-pdp-configuration.md).

Once this has been created, you can:

* Define the environment variables
* Create the pod
* Create Service Specification
* Create the service

{% hint style="info" %}
**Supported K8S version**

1.14 or higher
{% endhint %}



### Define the Environment Variables

```bash
kubectl create secret generic pdp-secret --from-literal=<API_KEY>='<API_SECRET>'
```

Create a file named `pdp-deployment.yaml` with the content:

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: pdp-deployment
  labels:
    app: pdp
spec:
  replicas: 1
  selector:
    matchLabels:
      app: pdp
  template:
    metadata:
      labels:
        app: pdp
    spec:
      containers:
        - name: pdp
          image: buildsecurity/pdp
          ports:
            - name: pdp-http-port
              containerPort: 8181
            - name: pdp-tcp-port
              containerPort: 9191
          env:
            - name: CONTROL_PLANE_ADDR
              value: https://api.demo.build.security/v1/api/pdp
            - name: API_KEY
              value: <API_KEY>
            - name: API_SECRET
              valueFrom:
                secretKeyRef:
                  name: pdp-secret
                  key: <API_KEY>
          startupProbe:
            httpGet:
              path: /health
              port: pdp-http-port
          readinessProbe:
            httpGet:
              path: /health?bundles
              port: pdp-http-port
            initialDelaySeconds: 5
            periodSeconds: 10
            failureThreshold: 3
```

{% hint style="warning" %}
**Note**

1. The Replica number should change to match your specific needs.
2. Remember to replace the variables placeholders

`<API_KEY>`  
`<API_SECRET>`  
`CONTROL_PLANE_ADDR`

**All of those provided to you in build.security control plane when** [**creating keys to your PDP**](../generating-api-keys-for-a-pdp.md) **configuration.**
{% endhint %}



### Create the pod

```bash
kubectl apply -f pdp-deployment.yaml
```

### Create Service Specification

Create a file named `pdp-service.yaml` with the content:

```yaml
apiVersion: v1
kind: Service
metadata:
  name: pdp-service
spec:
  selector:
    app: pdp
  ports:
    - name: rest
      protocol: TCP
      port: 8000
      targetPort: 8181
    - name: grpc
      protocol: TCP
      port: 9000
      targetPort: 9191
  type: LoadBalancer
```

