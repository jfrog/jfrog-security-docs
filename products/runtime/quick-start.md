# Quick Start

## **Enabling and Disabling Runtime Sensors**

| **Value**             | **Description** | **Example**                                                        |
| --------------------- | --------------- | ------------------------------------------------------------------ |
| <`node_name>`         | A single node   | `kubectl label nodes my_node disable_jfrog_runtime=true`           |
| <`node1 node2 node3>` | A list of nodes | `kubectl label nodes node1 node2 node3 disable_jfrog_runtime=true` |
| `--all`               | All nodes       | `kubectl label nodes --all disable_jfrog_runtime=true`             |

**Enable Runtime Sensors**

To enable runtime sensors that were previously disabled, run:

```
kubectl label nodes <nodes> disable_jfrog_runtime-
```

Replace `<nodes>` with one of the following:

* A single node, e.g., `kubectl label nodes my_node disable_jfrog_runtime-`
* A list of nodes, e.g., `kubectl label nodes node1 node2 node3 disable_jfrog_runtime-`
* All nodes, e.g., `kubectl label nodes --all disable_jfrog_runtime-`

**Disable Runtime Sensors**&#x20;

Sensors are deployed as a DaemonSet and installed by default on each of the cluster’s nodes. After installation using Helm, runtime sensors can be disabled on demand. To disable runtime sensors, run the following command:

```
kubectl label nodes <nodes> disable_jfrog_runtime=true
```

Replace `<nodes>` with one of the following:

* A single node, e.g., `kubectl label nodes my_node disable_jfrog_runtime=true`
* A list of nodes, e.g., `kubectl label nodes node1 node2 node3 disable_jfrog_runtime=true`
* All nodes, e.g., `kubectl label nodes --all disable_jfrog_runtime=true`

