# Install Runtime

## Installation Guide for JFrog Runtime Security

### Prerequisites

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

```sh
helm repo add jfrog https://charts.jfrog.io --force-update
```

#### Configure Artifactory for Ingress Controller

If your platform is not yet configured to work with an ingress controller, update your Artifactory configuration. Modify the Helm chart values by setting the following parameters in a `values.yaml` file:

```yaml
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

```yaml
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

```sh
helm upgrade --install runtime -f runtime-values.yaml
```

### Step 3: Install Runtime Sensors

To install Runtime Sensors:

1. Navigate to **Sensor Management** under the **Runtime** section in the JFrog Platform Administration tab.
2. Click the **Install Runtime** button to open the Sensor Installation Wizard.
3. Follow the provided instructions to generate an installation snippet and apply it to your Kubernetes cluster.

#### Bypassing Certificate Verification (Optional)

If you are using a self-signed certificate, modify the sensor installation snippet to bypass certificate verification:

```sh
--set tlsInsecureSkipVerify=true
```

**Note:** This setup should be carefully considered in production environments based on your organization's security policies.
