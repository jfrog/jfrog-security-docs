# Quick Start

## **Enabling and Disabling Runtime Sensors**

Sensors are deployed as a DaemonSet and installed by default on each cluster’s nodes. After installation using Helm, runtime sensors can be disabled on demand.

| **Value**             | **Description** | **Example**                                                        |
| --------------------- | --------------- | ------------------------------------------------------------------ |
| <`node_name>`         | A single node   | `kubectl label nodes my_node disable_jfrog_runtime=true`           |
| <`node1 node2 node3>` | A list of nodes | `kubectl label nodes node1 node2 node3 disable_jfrog_runtime=true` |
| `--all`               | All nodes       | `kubectl label nodes --all disable_jfrog_runtime=true`             |

**Disable Runtime Sensors**&#x20;

&#x20;To disable runtime sensors, run the following command:

```
kubectl label nodes <nodes> disable_jfrog_runtime=true
```

**Enable Runtime Sensors**

To enable runtime sensors that were previously disabled, run:

```
kubectl label nodes <nodes> disable_jfrog_runtime-
```

## Inspecting Live Software Components

**Before You Begin:**

* Data in the Live Assessment is retained for 10 days before deletion.

This guide provides instructions on how to inspect live software components using the Runtime **Live Assessment** capability. This feature enables you to view and search live runtime information, identify potential security risks, and monitor the health of their runtime environments.

#### **Risk Runtime Alerts Against:**&#x20;

* **Malicious Packages:** Detects harmful code within software components.
* **Untrusted Images:** Identifies images from unverified registries.
* **Critical Applicable CVEs:** Highlights critical vulnerabilities identified through contextual analysis.
* **Integrity Violations:** Flags discrepancies between Artifactory images and running cluster binaries.

**Active Components Runtime Inspects:**

|                       |                                                                                                                                        |
| --------------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| **Runtime Component** | **Description**                                                                                                                        |
| **Workloads**         | Applications and services actively running in Kubernetes clusters, managed by resources like Deployments, StatefulSets, or DaemonSets. |
| **Processes**         | Individual executable instances within workloads, detailed with vulnerability data for monitoring and risk management.                 |
| **Images**            | Packaged files containing code and configurations needed to run applications, traceable to their source in JFrog Artifactory.          |

#### **Images**

* **Image Details:** Trace images back to their source, view risks, and identify vulnerabilities.
* **Risk and Vulnerability Data:** Highlighted for the riskiest image tags.

#### **Image Tags Detailed View**

1. **Select an Image Tag:**
   * Click on the image tag to view detailed information.
2. **Review Tag-Specific Data:**
   * Includes workload count, cluster details, image path, deployer, and related vulnerabilities.

#### **Workloads**

1. **Access Workloads Tab:**
   * Open the **Live Assessment** screen to view detected workloads.
2. **Review Workload Details:**
   * Examine risks, vulnerabilities, and operational status.
   * Information includes cluster, node, and namespace data for issue localization.

#### **Workload's Process Group Detailed View** _(Controller + Sensors Mode Only)_

1. **Expand Desired Workload:**
   * In the Workloads tab, click to expand the workload.
2. **View Process Details:**
   * Click on a process to access comprehensive information, including vulnerabilities and Artifactory linkage.

#### **Processes**_(Runtime Impact: Controller + Sensors)_

* **Process Grouping:** Based on executable, location, command arguments, image, and workload.
* **Key Data Fields:** Process name, risks, vulnerabilities, status, arguments, path, and identifiers.
* **Filtering Options:** Apply filters to focus on specific processes or vulnerabilities.



