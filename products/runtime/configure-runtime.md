---
description: >-
  This workflow sets up the JFrog Runtime Security system and ensures it’s
  configured correctly.
---

# Configure

## Prepare the Environment

1. Ensure `kubectl` and `helm` are configured for your Kubernetes cluster.
2. Set up an ingress controller with TLS (Nginx is recommended).
3. Verify that Artifactory and Xray are installed on the JFrog Platform.

## Install Runtime Service

1. Add the JFrog Helm repository:

```
helm repo add jfrog https://charts.jfrog.io --force-update
```

2. Create a `runtime-values.yaml` file with your environment details (e.g., ingress domain and database configuration).
3. Deploy the Runtime Service:

```
helm upgrade --install runtime -f runtime-values.yaml
```

## **Install Sensors (for Runtime Impact Mode)**

1. Go to **Sensor Management** in the JFrog Platform UI.
2. Click **Install Runtime**, select a cluster, and configure the namespace.
3. Copy and run the installation snippet on your jump server:

```
kubectl apply -f <installation-snippet>
```

## **Verify Installation**

1. Check the Sensor Management tab to ensure all clusters and nodes report correctly.
2. Ensure runtime data is flowing into the JFrog Platform for analysis.
