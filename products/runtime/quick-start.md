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

## Detecting Active Artifacts in Runtime

Detect artifacts in Artifactory that are currently running in runtime, assess their security status, and take necessary actions to mitigate potential risks.

1. Navigate to the **Artifactory** Artifacts Tree.

If an artifact from the selected repository is actively running in runtime, a **detection button** will appear in the upper right corner of the page.

The button will also indicate whether any detected artifacts have vulnerabilities.

2. Click the **detection button** to view more information about the artifact.

You will be redirected to the **Runtime Live Assessment** page.

3. Examine details such as the artifact's location, where it is currently running, and any associated security risks.

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

Gain comprehensive visibility into runtime images by tracing them back to their JFrog Artifactory source, evaluating usage, and identifying security risks. Quickly spot untrusted sources, integrity violations, and critical CVEs, with key details like the highest risk level, total vulnerabilities, and tag-specific insights to prioritize remediation. By detecting discrepancies between Artifactory images and running binaries, you can proactively mitigate risks and strengthen your runtime security.

#### **Accessing Image Information**

1. From the JFrog Platform, under Runtime, select **Live Assessment**.
2. In the Live **Assessment** screen, click on the **Images** tab to view all detected images.

#### **Viewing Image Tags Detailed View**

1. Click on the desired image tag from the Images tab.
2. View detailed information, including:
   * Number of associated workloads
   * Cluster and namespace details
   * Image path in Artifactory
   * Associated deployer information
   * List of vulnerabilities

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



