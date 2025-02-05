# Install Runtime

## Prerequisites

Before proceeding with the installation, ensure the following requirements are met:

* **Kubernetes Cluster Access:** Ensure your `kubectl` and `helm` clients can access the Kubernetes cluster where you intend to install the Runtime Service.
* **Ingress Controller:** JFrog officially supports the Nginx controller configured with TLS. Other ingress controllers may work if they support GRPC communication.
* **JFrog Platform:** JFrog Runtime Security must be installed on a pre-existing JFrog platform.

### Step 1: Prepare the JFrog Platform

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

### Step 2: Install the Runtime Service

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

### Step 3: Install Runtime Sensors

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

#### Uninstalling Sensors

To uninstall sensors from a cluster, set the `kubectl` context to the desired cluster and run:

```
helm uninstall jf-sensors -n <Namespace>
```

#### Reinstalling Runtime Sensors

To reinstall sensors:

1. Reapply the installation snippet.
2. If updating, the sensors will upgrade automatically.
3. If sensors were uninstalled, reinstalling will generate a new Cluster ID. To preserve data, retrieve the Cluster ID before uninstalling:

```
kubectl -n <NAMESPACE> get configmaps runtime-config-configmap -o custom-columns='clusterId:data.clusterId'
```

**Output Example:**

```
clusterId
225c8bec-1a85-4099-ac8e-144b81ac99e8
```

4. Reinstall the sensors using:

```
--set clusterID=225c8bec-1a85-4099-ac8e-144b81ac99e8
```

This preserves historical monitoring data and merges it with new data.

#### Bypassing Certificate Verification (Optional)

If using a self-signed certificate, modify the installation snippet:

```
--set tlsInsecureSkipVerify=true
```

**Note:** Carefully assess this option for production environments.
