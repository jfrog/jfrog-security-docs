# Self-Hosted Installation

## Before You Begin

* It is essential you have:
  * Artifactory version 7.77.20
  * Xray version 3.104.08
* Ensure your `kubectl` and `helm` clients can access the Kubernetes cluster where you intend to install the Runtime Service.
* JFrog officially supports the Nginx controller configured with TLS. Other ingress controllers may work if they support GRPC communication.
* JFrog Runtime Security must be installed on a pre-existing JFrog platform.

## System Requirements

|                      |                                   |                   |
| -------------------- | --------------------------------- | ----------------- |
| **Component**        | **Supported**                     | **Not Supported** |
| Container technology | Kubernetes 1.21+, OpenShift 1.21+ |                   |
| Kernel OS            | Linux Kernel 4.18+                | Windows Kernel    |
| Database             | Postgres 16                       |                   |

### CPU and Memory <a href="#cpu-and-memory" id="cpu-and-memory"></a>

Nodes are considered to run an average of 100 pods.

<table><thead><tr><th width="261"></th><th width="369.3333333333333"></th><th></th></tr></thead><tbody><tr><td><strong>Number of Running Nodes</strong></td><td><strong>CPU</strong></td><td><strong>Memory</strong></td></tr><tr><td>100 or below</td><td>6 Cores</td><td>16 GiB</td></tr><tr><td>500 or below</td><td>30 Cores</td><td>16 GiB</td></tr><tr><td>1000 or below</td><td>Contact JFrog Support for sizing requirements.</td><td></td></tr></tbody></table>

<table><thead><tr><th width="205">Monitored Nodes</th><th width="200">vCPUs</th><th>Memory (GiB)</th><th>Storage Type</th><th>Network Performance</th></tr></thead><tbody><tr><td>Runtime Integrity (controller only setup) or 100 nodes and below</td><td>2</td><td>10</td><td><p>SSD</p><p>20 GiB<br>IOps: 600<br>Throughput:500MBps</p></td><td>4750 Mbps</td></tr><tr><td>500 nodes and below</td><td>10</td><td>32</td><td><p>SSD</p><p>100 GiB</p><p>IOps: 3000</p><p>Throughput:500MBps</p></td><td>4750 Mbps</td></tr><tr><td>1000 nodes and below</td><td>Contact JFrog Support for sizing requirements.</td><td></td><td></td><td></td></tr></tbody></table>

## Prepare the JFrog Platform

It is essential that you have:

* JFrog platform join key: `<join-key>`
* JFrog platform domain name: `<add-your-public-domain-here>`
* Artifactory Kubernetes service name (used for installing Xray): `<artifactory-service-url>`

### Add and Update JFrog Helm Chart Repository

Run the following command to add and update the JFrog Helm chart repository in your local configuration:

```
helm repo add jfrog https://charts.jfrog.io --force-update
```

### Configure Artifactory for Ingress Controller

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

## Install the Runtime Service

### Create a Configuration File

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

### Install JFrog Runtime Service

Run the following command to install the runtime service:

```
helm upgrade --install runtime -f runtime-values.yaml
```

## Install Runtime Sensors

The JFrog Runtime has two installation options depending on what you have purchased:

* Runtime **Integrity:** Default option with Runtime Controller only.
* Runtime **Impact:** Includes Runtime Controller and Runtime Sensors.

### Installing Runtime Sensors

1. Navigate to **Administration > Runtime > Sensor Management**.
2. Click **Install Runtime** to open the installation wizard.
3. Provide the environment details:
   * **Cluster name:** Used as the cluster name in management.
   * **Namespace:** Specify where the JFrog Runtime component will run.
4. Select the installation type: Controller only or Controller and Sensors.
5. Copy and execute the provided command in your terminal.
6. The status of controllers and sensors can be monitored in **Sensor Management**.

## Installation for OpenShift Users

If using OpenShift, grant necessary permissions after sensor installation:

```
oc adm policy add-scc-to-user privileged system:serviceaccount:jfrog-runtime:jf-sensors-sensors-service-account
```

This ensures the Runtime Sensor has the required security context in OpenShift.

This preserves historical monitoring data and merges it with new data.

## Bypassing Certificate Verification (Optional)

{% hint style="warning" %}
Carefully assess this option for production environments.
{% endhint %}

If using a self-signed certificate, modify the installation snippet:

```
--set tlsInsecureSkipVerify=true
```
