# Quick Start

## **Enabling/Disabling Runtime Sensors**

Runtime sensors are deployed as a **DaemonSet** and are installed by default on each cluster node. After installation, they can be enabled or disabled as needed.

| Parameter     | Description                                                                                                                                                                                                                                                                                                          |
| ------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `<node-name>` | <p></p><ul><li>A single node: <code>kubectl label nodes &#x3C;my_node> disable_jfrog_runtime=true</code></li><li>Multiple nodes: <code>kubectl label nodes &#x3C;node1 node2 node3> disable_jfrog_runtime=true</code></li><li>All nodes: <code>kubectl label nodes --all disable_jfrog_runtime=true</code></li></ul> |

*   Disable on specific nodes:

    ```sh
    shCopyEditkubectl label nodes <node-name> disable_jfrog_runtime=true
    ```
*   Enable sensors:

    ```sh
    shCopyEditkubectl label nodes <node-name> disable_jfrog_runtime-
    ```

## **Monitoring & Verification**

* Navigate to **Sensor Management** in the JFrog UI to verify sensor deployment.
* Use **Live Assessment** to check runtime security insights, risks, and workloads.
