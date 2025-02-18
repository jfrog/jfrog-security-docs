# Configure Runtime

JFrog Runtime offers two deployment modes based on your subscription:

* **Runtime Integrity** – The default option, which includes only the **Runtime Controller** and requires no additional configuration.
* **Runtime Impact** – An advanced option that includes both the **Runtime Controller** and **Runtime Sensors** for deeper security insights.

This guide applies **only to Runtime Impact** subscriptions, as Runtime Sensors require configuration.

## Sensors

### Installing Sensors

1. Navigate to **Administration > Runtime > Sensor Management**.
2. Click **Install Runtime** to open the installation wizard.
3. Provide the environment details:
   * **Cluster name:** Used as the cluster name in management.
   * **Namespace:** Specify where the JFrog Runtime component will run.
4. Select the installation type: Controller only or Controller and Sensors.
5. Copy and execute the provided command in your terminal.
6. The status of controllers and sensors can be monitored in **Sensor Management**.

### Uninstalling Sensors

{% hint style="warning" %}
If sensors are uninstalled, reinstalling them will generate a new Cluster ID.&#x20;
{% endhint %}

To uninstall sensors from a cluster, set the `kubectl` context to the desired cluster and run:

```
helm uninstall jf-sensors -n <Namespace>
```

### Reinstalling Sensors

If sensors are uninstalled, reinstalling them will generate a new Cluster ID. To preserve historical monitoring data and merge it with new data, retrieve the existing Cluster ID before reinstalling the sensor.

#### Reinstalling Sensor Preserving Data

1.  Before uninstalling the sensor, retrieve the cluster ID :

    ```
    kubectl -n <NAMESPACE> get configmaps runtime-config-configmap -o custom-columns='clusterId:data.clusterId'
    ```

    #### Output Example

    ```
    clusterId
    225c8bec-1a85-4099-ac8e-144b81ac99e8
    ```
2.  Reinstall the sensors using:

    ```
    --set clusterID=225c8bec-1a85-4099-ac8e-144b81ac99e8
    ```

#### Reinstalling Sensor Without Preserving Data

1. Reapply the installation snippet.
2. If updating, the sensors will upgrade automatically.

## Granting OpenShift Security Context Constraints Privileges

In **OpenShift**, **Security Context Constraints (SCCs)** are enforced to restrict the permissions of running containers. By default, OpenShift applies strict security policies that limit container privileges, which can prevent the JFrog Runtime Sensor from collecting essential runtime security data.

Granting the necessary privileged SCC ensures that the Runtime Sensor can:

* **Monitor running workloads effectively** by accessing necessary kernel-level data.
* **Collect real-time security insights** using **eBPF technology** to detect threats, integrity violations, and process activity.
* **Transmit security data** from OpenShift nodes to the JFrog Platform for further analysis.

Without this privilege, the sensor may be unable to access required system resources, leading to incomplete security monitoring and reduced visibility into runtime threats.

To grant SCC privileges, run:

```sh
shCopyEditoc adm policy add-scc-to-user privileged system:serviceaccount:jfrog-runtime:jf-sensors-sensors-service-account
```

## Bypassing Certificate Verification (Optional)

{% hint style="warning" %}
Carefully assess this option for production environments.
{% endhint %}

If using a self-signed certificate, modify the installation snippet:

```
--set tlsInsecureSkipVerify=true
```
