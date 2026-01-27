# Runtime

#### Standard Installation (REST/HTTP1)

**Recommended for most environments**

This method provides reliable communication over standard Kubernetes ingress using REST/HTTP1 and works in virtually all environments.

Choose this option unless you have very high event volume or a specific need for gRPC.

#### Install the Runtime Service (REST)

Create `runtime-values.yaml`:

```yaml
global:
  deployEnv: onprem
  jfrogUrl: <add-your-public-domain-here>

postgresql:
  enabled: true
  # For external DB:
  # database:
  #   url: postgres://<host>:5432/runtime
  #   user: runtime
  #   password: <password>

router:
  jfrogUrl: <artifactory-service-url>
  # Example: http://artifactory:8082

runtime:
  joinKey: <join-key>
  image:
    registry: releases-docker.jfrog.io
```

Run:

```bash
helm upgrade --install runtime -f runtime-values.yaml
```

### Install Sensors

1. In the JFrog Platform, go to\
   **Administration → Runtime Settings → Cluster Management**
2. Click **Install Runtime** to open the sensor installation wizard.
3. Copy the generated installation snippet.
4. For on-prem REST installations, add:

```bash
--set serviceCommunicationType=rest
```

#### Self-Signed Certificates (Sensors)

If the platform is configured with a self-signed certificate, add:

```bash
--set tlsInsecureSkipVerify=true
```

## High-Volume Installation (gRPC)

**For large-scale and high-throughput clusters only**

This method is intended for environments with high scan volume or high event throughput. gRPC provides more efficient, low-latency communication but requires additional ingress configuration and gRPC-capable networking.

### Preparing Your JFrog Platform

This guide assumes you are installing Runtime Security on an existing JFrog Platform.

### Artifactory Update (gRPC only)

If your platform is not already configured to use an ingress controller, you must update the Artifactory Helm configuration.

Replace `<add-your-public-domain-here>` in `ingress.hosts` and `tls.hosts` with your actual domain.

```yaml
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

### Install the Runtime Service (gRPC)

Create `runtime-values.yaml`:

```yaml
global:
  deployEnv: onprem
  jfrogUrl: <add-your-public-domain-here>

postgresql:
  enabled: true
  # For external DB:
  # database:
  #   url: postgres://<host>:5432/runtime
  #   user: runtime
  #   password: <password>

router:
  jfrogUrl: <artifactory-service-url>
  # Example: http://artifactory:8082

runtime:
  joinKey: <join-key>
  image:
    registry: releases-docker.jfrog.io

ingress:
  grpc:
    tlsSecretName: runtime-tls-secret
    securedBackendProtocol: false
```

Run:

```bash
helm upgrade --install runtime -f runtime-values.yaml
```

### Install Runtime Sensors (gRPC)

1. In the JFrog Platform, go to\
   **Administration → Runtime Settings → Cluster Management**
2. Click **Install Runtime**.
3. Copy and run the generated installation snippet.

#### Bypassing Certificate Verification

> Skipping TLS verification should be carefully considered in production environments.

If you are using a self-signed certificate, add:

```bash
--set tlsInsecureSkipVerify=true
```

## Self-Signed Certificates (Runtime Service)

Runtime Service supports self-signed certificates by adding your CA to the trusted certificate bundle.

### Create a Secret

```bash
kubectl create secret generic runtime-custom-certs \
  --from-file=ca.crt=/path/to/ca.crt \
  --from-file=intermediate.crt=/path/to/intermediate.crt
```

### Enable in `runtime-values.yaml`

**Global configuration:**

```yaml
global:
  customCertificates:
    enabled: true
    certificateSecretName: runtime-custom-certs
```

**Runtime-only configuration:**

```yaml
runtime:
  customCertificates:
    enabled: true
    certificateSecretName: runtime-custom-certs
```

### Install / Upgrade

```bash
helm upgrade --install runtime -f runtime-values.yaml
```
