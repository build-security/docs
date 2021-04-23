# Kubernetes with Helm Chart

### Deploying pdp as a standalone service via Helm

1.Add the build security repo to your Helm repositories :

```bash
$ helm repo add build-security https://build-security.github.io/pdp-helm/
```

2. Download the [values-tmpl.yaml](https://github.com/build-security/pdp-helm/blob/master/values-tmpl.yaml) .

3. Add your desired variables into the values template files as specified in the [README.md](https://github.com/build-security/pdp-helm/blob/master/README.md) file.

{% hint style="info" %}
 You need to generate the api key & secret from the console before proceeding
{% endhint %}

3.Deploy the chart using the following command:

```bash
$ helm install --name-template build-security-pdp build-security/build-security-pdp -f values-tmpl.yaml
```

4.Run kubectl to verify helm installed and the pods were started successfully:

```bash
kubectl get deploy | grep build-security-pdp 
```

### Deploying PDP as a sidecar for your application / microservice

In order to deploy pdp as a sidecar we must specify an additional container in your deployment configuration template & add the necessary parameters to the relevant deployment's configmap, secret & service templates.

1.Example of a deployment template:

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

2.Verify your application container can access the pdp via curl on port 8181:

```bash
curl http://<service-name>:8181/v1/data/
```

{% hint style="info" %}
Deployment must have outbound access to the internet for the pdp to communicate with the control plane
{% endhint %}

### 

