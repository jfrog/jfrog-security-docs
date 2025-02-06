# Manage Runtime

## Manage **Sensors**

The Runtime Sensor Management enables users to install Runtime Controller and Sensors on their clusters, view the clusters that have been installed, and access detailed information about the clusters, nodes, and sensors that monitor them. This capability also provides users with the health status of their sensors and allows them to determine if their environment is being monitored correctly and easily. To access Sensor Management, navigate to the "Sensor Management" section under the "Runtime" menu.

**Installation Options**

JFrog Runtime has two installation options, depending on the purchased plan:

* **Runtime Integrity**: Default option with Runtime Controller only.
* **Runtime Impact**: An additional option that includes both the Runtime Controller and Runtime Sensors.

The Sensor Management capability includes a convenient feature that allows users to install sensors on their clusters easily.

#### To install a runtime sensor on a cluster:

1. Click on the **Install Runtime** button in Sensor Management.
2. Follow the installation wizard, which contains the necessary commands to install the sensor.
3. Name your cluster; this will be used under cluster management as the identifier for the deployed cluster.
4. Specify the namespace where the JFrog Runtime component will run. For consistency, use the same name across all clusters.
5. Copy and execute the provided snippet from a jump server where the `kubectl` context is set to the required cluster.
6. Once the sensor is deployed successfully, a new entry indicating the sensor deployment will appear under Sensor Management.

## **View Cluster Status**

The Runtime Sensor Management **Cluster Inventory** allows users to view the status of clusters monitored by JFrog Runtime.

#### To access the Cluster Inventory:

1. Navigate to the **Sensor Management** section under the **Runtime** menu.
2. Once the Controller has been installed, view the list displaying the monitored clusters and their status.
3. Use this information to track cluster health and take proactive steps to address any potential issues.

## **Inspect Cluster**

The **Cluster Detailed View** in the Runtime Sensor Management feature provides detailed information about the selected cluster and its monitored nodes.

#### To access the Cluster Detailed View:

1. Click on a cluster in the **Cluster Inventory** pane.
2. View detailed information, including the list of nodes running under the cluster and their corresponding Runtime Sensor statuses.
   * In **Controller Only** mode, node-level sensor details will not be available.
3. Use this capability to track the health of sensors and quickly identify any potential problems or issues with the cluster infrastructure.
