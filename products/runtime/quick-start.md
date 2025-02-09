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
| **Images**            | Packaged files containing code and configurations needed to run applications, traceable to their source in JFrog Artifactory.          |
| **Workloads**         | Applications and services actively running in Kubernetes clusters, managed by resources like Deployments, StatefulSets, or DaemonSets. |
| **Processes**         | Individual executable instances within workloads, detailed with vulnerability data for monitoring and risk management.                 |

## **Inspecting Images in Runtime**

Gain comprehensive visibility into runtime images by tracing them back to their JFrog Artifactory source, evaluating usage, and identifying security risks. Quickly spot untrusted sources, integrity violations, and critical CVEs, with key details like the highest risk level, total vulnerabilities, and tag-specific insights to prioritize remediation. By detecting discrepancies between Artifactory images and running binaries, you can proactively mitigate risks and strengthen your runtime security.

#### **Accessing Image Information**

Image information includes number of associated workloads, cluster and namespace details, image path in Artifactory, associated deployer information, and list of vulnerabilities

1. From the JFrog Platform, under **Runtime**, select **Live Assessment**.
2. In the **Live Assessment** screen, click on the **Images** tab to view all detected images.
3. Select an image.
4. Click on the desired image tag from the Images tab.

## **Inspecting Workloads in Runtime**

Inspect workloads in your runtime environment with Runtime Live Assessment to monitor active applications, identify security risks, and gain infrastructure-wide insights. Workloads, managed by Kubernetes resources like Deployments, StatefulSets, DaemonSets, or Jobs, consist of containers linked to images and running processes. The Workloads Table highlights risks such as integrity violations, untrusted registries, critical CVEs, and malicious packages, along with total vulnerabilities, workload status, and location details across clusters, nodes, and namespaces to help you quickly detect and address security issues.

#### **Accessing Workloads in Runtime Live Assessment**

1. From the JFrog Platform, under **Runtime**, select **Live Assessment**.
2. In the **Live Assessment** screen, click on the **Workloads** tab to view all detected workloads.
3. Select a workload.
4. Click on a specific process to see detailed information.

## **Inspecting Processes in Runtime**

**Before You Begin:**

* It is essential you have Runtime Impact (Controller + Sensors)

1. From the JFrog Platform, under **Runtime**, select **Live Assessment**.
2. In the **Live Assessment** screen, click on the **Processes** tab to view all detected workloads.
3. Review the **Processes** Table.
4. Apply filters to narrow down processes based on specific criteria (e.g., risk level, vulnerabilities).



