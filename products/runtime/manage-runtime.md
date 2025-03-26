# Manage Runtime

## Sensors

The Runtime Sensor Management enables users to install Runtime Sensors on their clusters, view the clusters that have been installed, and access detailed information about the clusters, nodes, and sensors that monitor them. This capability also provides users with the health status of their sensors and allows them to determine if their environment is being monitored correctly and easily. To access Sensor Management, navigate to the "Sensor Management" section under the "Runtime" menu.

### Enabling and Disabling Runtime Sensors

Sensors are deployed as a DaemonSet and installed by default on each cluster’s nodes. After installation using Helm, runtime sensors can be disabled on demand.

| Value                 | Description     | Example                                                            |
| --------------------- | --------------- | ------------------------------------------------------------------ |
| <`node_name>`         | A single node   | `kubectl label nodes my_node disable_jfrog_runtime=true`           |
| <`node1 node2 node3>` | A list of nodes | `kubectl label nodes node1 node2 node3 disable_jfrog_runtime=true` |
| `--all`               | All nodes       | `kubectl label nodes --all disable_jfrog_runtime=true`             |

## Clusters

### View Cluster Status

The Runtime Sensor Management **Cluster Inventory** allows you to view the status of clusters monitored by JFrog Runtime.

1. Navigate to the **Sensor Management** section under the **Runtime** menu.
2. Once the Controller has been installed, view the list displaying the monitored clusters and their status.
3. Use this information to track cluster health and proactively address any potential issues.

### Inspect Cluster

The Cluster Detailed View in the Runtime Sensor Management offers in-depth insights into the selected cluster and its monitored nodes, enabling you to track sensor health and swiftly detect potential infrastructure issues..

1. Click on a cluster in the **Cluster Inventory** pane.
2.  View detailed information, including the list of nodes running under the cluster and their corresponding Runtime Sensor statuses.

    In **Controller Only** mode, node-level sensor details will not be available.
