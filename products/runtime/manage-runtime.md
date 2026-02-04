# Manage Runtime

## Sensors

The Runtime Cluster Management enables users to install Runtime Sensors on their clusters, view the clusters that have been installed, and access detailed information about the clusters, nodes, and sensors that monitor them. This capability also provides users with the health status of their sensors and allows them to determine if their environment is being monitored correctly and easily. To access Cluster Management, navigate to the "Cluster Management" section under the "Runtime" menu.

### Enabling and Disabling Runtime Sensors

Sensors are deployed as a DaemonSet and installed by default on each cluster’s nodes. After installation using Helm, runtime sensors can be disabled on demand.

| Value                 | Description     | Example                                                            |
| --------------------- | --------------- | ------------------------------------------------------------------ |
| <`node_name>`         | A single node   | `kubectl label nodes my_node disable_jfrog_runtime=true`           |
| <`node1 node2 node3>` | A list of nodes | `kubectl label nodes node1 node2 node3 disable_jfrog_runtime=true` |
| `--all`               | All nodes       | `kubectl label nodes --all disable_jfrog_runtime=true`             |

## Clusters

### View Cluster Status

The Runtime Cluster Management **Cluster Inventory** allows you to view the status of clusters monitored by JFrog Runtime.

1. Navigate to the **Cluster Management** section under the **Runtime** menu.
2. Once the Controller has been installed, view the list displaying the monitored clusters and their status.
3. Use this information to track cluster health and proactively address any potential issues.

### Inspect Cluster

The Cluster Detailed View in the Runtime Cluster Management offers in-depth insights into the selected cluster and its monitored nodes, enabling you to track sensor health and swiftly detect potential infrastructure issues..

1. Click on a cluster in the **Cluster Inventory** pane.
2.  View detailed information, including the list of nodes running under the cluster and their corresponding Runtime Sensor statuses.

    In **Controller Only** mode, node-level sensor details will not be available.

### Automatic Security Scanning

Enable automatic security scanning for any container image detected through Runtime Visibility. When a cluster is configured for this capability, the system checks whether each runtime-observed image has corresponding security data. If not, it automatically triggers indexing and scanning based on repository characteristics.

1. In the platform, under **Administration**, go to **Runtime > Cluster Management**.
2. Under **Clusters**, hover over the cluster you wish to configure.
3. From the cluster menu, select **Configure**.
4. The **Scan Configuration** window opens.
5. In the Scan Configuration window, select the scanners you want to enable for the cluster, including **SCA** and any **Advanced Security** scanners such as Vulnerabilities Contextual Analysis, Secrets, Applications, Services, or IaC.
6. Click **Apply** to save the configuration.

### Runtime Scope

Runtime Scope ensures that every image detected by Runtime sensors in your Kubernetes, OpenShift, or Fargate environments is automatically scanned by Xray and Advanced Security.

This configuration eliminates manual steps and guarantees that all running images are systematically evaluated for vulnerabilities, secrets, and exposures as soon as they are observed in your clusters.

#### Configure Runtime Scope for a Cluster

1. Navigate to **Administration** > **Runtime** > **Cluster Management**.
2. In the **Cluster Inventory table**, locate the cluster you want to configure.
3. From the menu, select **Configure**.\
   The **Scan Configurations** window opens.
4. Select which security scans to enable (SCA, Secrets, Contextual Analysis, Exposures, etc.) and set retention.
5. Click **Apply**.

#### Batch Configuration

1. In **Cluster Management**, select multiple clusters.
2. Click **Batch Configure** and apply scanners/retention settings to all selected clusters.

A coverage summary appears in the **Clusters Configuration Security Coverage** panel, showing how many clusters are configured with each type of scanner.
