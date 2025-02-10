# Self-Hosted

### Prepare the JFrog Platform

#### Before Installing

Ensure you have the following details ready:

* **JFrog platform join key:** `<join-key>`
* **JFrog platform domain name:** `<add-your-public-domain-here>`
* **Artifactory Kubernetes service name (used for installing Xray):** `<artifactory-service-url>`

#### Add and Update JFrog Helm Chart Repository

Run the following command to add and update the JFrog Helm chart repository in your local configuration:

```
helm repo add jfrog https://charts.jfrog.io --force-update
```

#### Configure Artifactory for Ingress Controller

If your platform is not yet configured to work with an ingress controller, update your Artifactory configuration. Modify the Helm chart values by setting the following parameters in a `values.yaml` file:

```
# Standalone nginx server (not ingress-controller)
nginx:
  enabled: false

ingress:
  enabled: true
  defaultBackend:
    enabled: true
  hosts:
    - <add-your-public-domain-here>
  routerPath: /
  disableRouterBypass: true
  artifactoryPath: /artifactory/
  className: "nginx"
  annotations:
    nginx.ingress.kubernetes.io/proxy-read-timeout: "600"
    nginx.ingress.kubernetes.io/proxy-send-timeout: "600"
    nginx.ingress.kubernetes.io/proxy-body-size: "0"
    nginx.ingress.kubernetes.io/rewrite-target: "/"
  tls:
    - secretName: artifactory-tls-secret
      hosts:
        - <add-your-public-domain-here>
```

### Step 2: Install the Runtime Service (SH)

#### Create a Configuration File

Create a new file named `runtime-values.yaml` with the following content:

```
global:
  deployEnv: onprem
  jfrogUrl: <add-your-public-domain-here>

postgresql:
  enabled: true

# Use external database if needed
# database:
#   url: postgres://<host>:5432/runtime
#   user: runtime
#   password: <password>

ingress:
  grpc:
    tlsSecretName: runtime-tls-secret
    securedBackendProtocol: false

router:
  jfrogUrl: <artifactory-service-url> # Example: http://artifactory:8082

runtime:
  joinKey: <join-key> # Same join key from Artifactory
  image:
    registry: releases-docker.jfrog.io
```

#### Install JFrog Runtime Service

Run the following command to install the runtime service:

```
helm upgrade --install runtime -f runtime-values.yaml
```

### Step 3: Install Runtime Sensors (SaaS + SH)

The JFrog Runtime has two installation options depending on what you have purchased:

* **Runtime Integrity:** Default option with Runtime Controller only.
* **Runtime Impact:** Includes Runtime Controller and Runtime Sensors.

#### Installing Runtime Sensors

To install a runtime sensor on a cluster:

1. Navigate to **Administration > Runtime > Sensor Management**.
2. Click **Install Runtime** to open the installation wizard.
3. Provide the environment details:
   * **Cluster name:** Used as the cluster name in management.
   * **Namespace:** Specify where the JFrog Runtime component will run.
4. Select the installation type: Controller only or Controller and Sensors.
5. Copy and execute the provided command in your terminal.
6. The status of controllers and sensors can be monitored in **Sensor Management**.

#### Installation for OpenShift Users

If using OpenShift, grant necessary permissions after sensor installation:

```
oc adm policy add-scc-to-user privileged system:serviceaccount:jfrog-runtime:jf-sensors-sensors-service-account
```

This ensures the Runtime Sensor has the required security context in OpenShift.

This preserves historical monitoring data and merges it with new data.

#### Bypassing Certificate Verification (Optional)

If using a self-signed certificate, modify the installation snippet:

```
--set tlsInsecureSkipVerify=true
```

**Note:** Carefully assess this option for production environments.
