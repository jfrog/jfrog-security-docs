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

## **Inspecting Images in Runtime**

You can trace images back to their source in JFrog Artifactory, evaluate their usage, and identify associated security risks.

#### **Accessing Image Information**

1. **Navigate to the Runtime Menu:**
   * Open the JFrog Platform.
   * Select **Live Assessment** under the **Runtime** menu.
2. **Access the Images Tab:**
   * In the Live Assessment screen, click on the **Images** tab to view all detected images.

#### **Key Image Details**

* **Risk Column:** Displays the highest risk level detected among all image tags. If image tags vary by architecture, the riskiest tag will determine the displayed risk.
* **Vulnerabilities Column:** Shows the total number of vulnerabilities associated with the riskiest image tag.
* **Image Tags:** Provides granular information on each image tag, helping identify risks and vulnerabilities at a more detailed level.

#### **Viewing Image Tags Detailed View**

1. **Select an Image Tag:**
   * Click on the desired image tag from the Images tab.
2. **Review Tag-Specific Data:**
   * View detailed information, including:
     * Number of associated workloads
     * Cluster and namespace details
     * Image path in Artifactory
     * Associated deployer information
     * List of vulnerabilities

#### **Risk Assessment for Images**

* **Untrusted Images:** Identifies images sourced from unverified registries.
* **Integrity Violations:** Highlights discrepancies between Artifactory images and running cluster binaries.
* **Critical Applicable CVEs:** Flags critical vulnerabilities identified through contextual analysis.

#### **Using Image Data for Security Management**

* **Traceability:** Easily track images back to their Artifactory source.
* **Vulnerability Insights:** Identify and prioritize vulnerabilities for remediation.
* **Risk Mitigation:** Take proactive steps to address security risks, ensuring the integrity and safety of your runtime environment.

## **Inspecting Workloads in Runtime**

This guide helps you inspect workloads in your runtime environment using the Runtime Live Assessment capability in JFrog. You can monitor active applications and services, identify security risks, and gain insights into workloads running across your infrastructure.

#### **Accessing Workloads in Runtime Live Assessment**

1. **Navigate to the Runtime Menu:**
   * Open the JFrog Platform.
   * Select **Live Assessment** under the **Runtime** menu.
2. **Access the Workloads Tab:**
   * In the Live Assessment section, click on the **Workloads** tab to view all detected workloads.

#### **Understanding Workloads**

* **Definition:** A workload consists of one or more containers or applications running in your environment. Workloads can be managed by Kubernetes resources like Deployments, StatefulSets, DaemonSets, or Jobs.
* **Components:** Each workload is linked to an image and has associated running processes.

#### **Viewing the Workloads List**

1. **Review Detected Workloads:**
   * The Workloads List displays all workloads currently active in your runtime environment.
2. **Key Data in the Workloads Table:**
   * **Risk Column:** Shows risks such as Integrity Violations, Untrusted Registries, Critical CVEs, and Malicious Packages.
   * **Vulnerability Column:** Displays the total number of vulnerabilities linked to each workload.
   * **Status Column:** Indicates whether the workload is running or stopped.
   * **Cluster, Node, and Namespace Columns:** Help you locate where issues exist within your environment.

#### **Inspecting Workload's Process Group Details** _(Controller + Sensors Mode Only)_

1. **Expand the Workload:**
   * Click on the workload to expand and view its process groups.
2. **View Process Details:**
   * Click on a specific process to see detailed information, including vulnerabilities and its link to the associated image in Artifactory.

#### **Managing Risks in Workloads**

* **Integrity Violations:** Identifies discrepancies between stored and running images.
* **Untrusted Registries:** Flags workloads sourced from registries without verified trust.
* **Critical Applicable CVEs:** Highlights critical vulnerabilities within the workload.
* **Malicious Packages:** Detects harmful code within running processes.

#### **Processes**_(Runtime Impact: Controller + Sensors)_

* **Process Grouping:** Based on executable, location, command arguments, image, and workload.
* **Key Data Fields:** Process name, risks, vulnerabilities, status, arguments, path, and identifiers.
* **Filtering Options:** Apply filters to focus on specific processes or vulnerabilities.



