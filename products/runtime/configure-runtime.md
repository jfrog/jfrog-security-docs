---
description: >-
  This workflow sets up the JFrog Runtime Security system and ensures it’s
  configured correctly.
---

# Configure Runtime

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

## Uninstalling Sensors

To uninstall sensors from a cluster, set the `kubectl` context to the desired cluster and run:

```
helm uninstall jf-sensors -n <Namespace>
```

## Reinstalling Runtime Sensors

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

Reinstall the sensors using:

```
--set clusterID=225c8bec-1a85-4099-ac8e-144b81ac99e8
```

This preserves historical monitoring data and merges it with new data.

## Bypassing Certificate Verification (Optional)

{% hint style="warning" %}
Carefully assess this option for production environments.
{% endhint %}

If using a self-signed certificate, modify the installation snippet:

```
--set tlsInsecureSkipVerify=true
```

##
