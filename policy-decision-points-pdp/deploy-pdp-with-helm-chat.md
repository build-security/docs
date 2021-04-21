---
description: >-
  Guide to deploy pdp using a helm chart.Covering two use cases, deploying pdp
  as a seperate deployment or a side car to an existing deployment.
---

# Deploy PDP with Helm chat

### Deploying pdp as a standalone service via helm:



1.Add the pdp-helm repo to your helm repository:

```bash
$ helm repo add build-security https://build-security.github.io/pdp-helm/
```

2. Download the [values-tmpl.yaml](https://github.com/build-security/pdp-helm/blob/master/values-tmpl.yaml) Add your desired variables into the values template files as specified [ ](%20https://github.com/build-security/pdp-helm/blob/master/README.md)in the [README.md](https://github.com/build-security/pdp-helm/blob/master/README.md) file.

{% hint style="info" %}
 Note that you need to generate the api key & secret from the console before proceeding
{% endhint %}

3.Once the values-tmpl file is ready run the following command:

```bash
$ helm install --name-template build-security-pdp build-security/build-security-pdp -f values-tmpl.yaml
```

4.Run kubectl to verify helm installed and the pods were started  successfully:

```bash
kubectl get deploy | grep build-security-pdp 
```



### Deploying PDP as a sidecar for you application or microservice:

In order to deploy pdp as a side car with must specify an additional container in our deployment configuration template & add the necessary parameters to said deployment's configmap,secret & service template.

1.example of a deployment template:

```bash
      containers:
        - name: {{ .Values.deployment.pdp-container-name }}
          ports:
            - containerPort: {{ .Values.deployment.pdp-container-port }}
              protocol: TCP
              name: http
          securityContext:
            {}
          image: {{ .Values.deployment.pdp-container }}
          imagePullPolicy: Always
          envFrom:
            - configMapRef:
                {{- if .Values.configMap.data }}
                name: {{ $cm-name }}
            - secretRef:
                name: {{ $secret-name }}
          livenessProbe:
            httpGet:
              scheme: HTTP
              port: {{ .Values.deployment.pdp-container-port }}
            initialDelaySeconds: 5
            periodSeconds: 5
          readinessProbe:
            httpGet:
              path: /health
              scheme: HTTP
              port: {{ .Values.deployment.pdp-container-port }}
            initialDelaySeconds: 5
            periodSeconds: 5
          resources:
```

2.After deploying Verify your application container can access the pdp via curl on port 8181:

```bash
curl http://<service-name>:8181/v1/data/
```

{% hint style="info" %}
Note that the deployment must have outbound access to the internet for the pdp to communicate with the control plane.
{% endhint %}

