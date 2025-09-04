# Sensor

## Install Sensors

### Before You Begin

It is essential you have:

* `kubectl` and `helm` clients granted access to the Kubernetes cluster where you want to install the Runtime Service.
* An ingress controller (preferably configured with TLS).\
  JFrog officially supports the Nginx controller, while using other ingress controllers would work if they support GRPC communication.

1. Navigate to **Administration > Runtime > Cluster Management**.
2. Click **Install Runtime** to open the installation wizard.
3. Provide the environment details:
   * **Cluster name:** Used as the cluster name in management.
   * **Namespace:** Specify where the JFrog Runtime component will run.
4. Select the installation type: Controller only or Controller and Sensors.
5. Copy and execute the provided command in your terminal.
6. The status of controllers and sensors can be monitored in Cluster **Management**.

## Uninstalling Sensors

{% hint style="info" %}
If sensors are uninstalled, reinstalling them will generate a new Cluster ID.&#x20;
{% endhint %}

To uninstall sensors from a cluster, set the `kubectl` context to the desired cluster and run:

```
helm uninstall jf-sensors -n <Namespace>
```

## Reinstall Sensors

If sensors are uninstalled, reinstalling them will generate a new Cluster ID. To preserve historical monitoring data and merge it with new data, retrieve the existing Cluster ID before reinstalling the sensor.

{% hint style="info" %}
Sensors are automatically upgraded during system updates.&#x20;
{% endhint %}

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
