# Inspecting Live Software Components

This guide provides instructions on inspecting live software components using the Runtime **Live Assessment** capability. This enables you to view and search live runtime information, identify potential security risks, and monitor the health of your runtime environments.

{% hint style="warning" %}
Data in the Live Assessment is retained for 10 days before deletion.&#x20;
{% endhint %}

### Active Components Runtime Inspects

| Runtime Component | Description                                                                                                                             |
| ----------------- | --------------------------------------------------------------------------------------------------------------------------------------- |
| Images            | Packaged files containing code and configurations needed to run applications, traceable to their source in JFrog Artifactory.           |
| Workloads         | Applications and services actively running in Kubernetes clusters, managed by resources like Deployments, StatefulSets, or DaemonSets.  |
|  Processes        | Individual executable instances within workloads, detailed with vulnerability data for monitoring and risk management.                  |

### Risks Runtime Alerts Against

| Risk                     | Description                                                               |
| ------------------------ | ------------------------------------------------------------------------- |
| **Malicious Packages**   | Detects harmful code within software components.                          |
| **Untrusted Images**     | Identifies images originating from unverified registries.                 |
| **Critical & High CVEs** | Highlights vulnerabilities by severity.                                   |
| **Applicable CVEs**      | Indicates vulnerabilities confirmed as applicable by Contextual Analysis. |
| **Running CVEs**         | Shows vulnerabilities detected in currently active workloads.             |
| **Integrity Violations** | Flags discrepancies between Artifactory images and running binaries.      |

### Inspecting Your Images

Gain comprehensive visibility into runtime images by tracing them back to their JFrog Artifactory source, evaluating usage, and identifying security risks. Quickly spot untrusted sources, integrity violations, and critical CVEs, with key details like the highest risk level, total vulnerabilities, and tag-specific insights to prioritize remediation. By detecting discrepancies between Artifactory images and running binaries, you can proactively mitigate risks and strengthen your runtime security.

Image information includes a number of associated workloads, cluster and namespace details, registry name, repository path, associated providers, and deployer information. The _Owners Info_ section lists the application owners associated with the image.

#### Accessing Image Information&#x20;

1. From the JFrog Platform, under **Runtime**, select **Live Assessment**.
2. Select the **Images** tab to view all detected images.
3. Select an image to open the **Detailed View**.

The detailed view presents risk and vulnerability insights through dedicated widgets and tables:

* **Critical & High CVEs** – Displays the number of critical and high-severity vulnerabilities detected in the image.
* **Running CVEs** – Shows vulnerabilities currently associated with running workloads.
* **Applicable CVEs** – Indicates the subset of critical and high vulnerabilities determined as _applicable_ by Contextual Analysis.

If a malicious package is detected, a red banner appears at the top of the image details panel.

Additional fields provide context on the image, including:

* **Number of clusters**
* **Registry name**
* **Repository path**
* **Providers**
* **Owners Info** (application owners)
* **Build** and **Deployed by** details

### Inspecting Your Workloads&#x20;

Inspect workloads in your runtime environment with Runtime Live Assessment to monitor active applications, identify security risks, and gain infrastructure-wide insights. Workloads, managed by Kubernetes resources like Deployments, StatefulSets, DaemonSets, or Jobs, consist of containers linked to images and running processes. The Workloads Table highlights risks such as integrity violations, untrusted registries, critical CVEs, and malicious packages, along with total vulnerabilities, workload status, and location details across clusters, nodes, and namespaces to help you quickly detect and address security issues.&#x20;

#### Accessing Workloads in Runtime Live Assessment&#x20;

1\. From the JFrog Platform, under **Runtime**, select **Live Assessment**.&#x20;

2\. Select the **Workloads** tab to view all detected workloads.&#x20;

3\. Select a workload.&#x20;

4\. Click on a specific process to see detailed information.&#x20;

### Inspecting Your Processes

Before You Begin:

Process inspection is available only with [Runtime Impact](../#runtime-modes-of-deployment) (Controller + Sensors).

1\. From the JFrog Platform, under **Runtime**, select **Live Assessment**.&#x20;

2\. Select the **Processes** tab to view all detected workloads.&#x20;

3\. Review the Processes Table.&#x20;

4\. (Optional) Apply filters to narrow down processes based on specific criteria.

### Identifying Risk Locations in Runtime by Mapping Vulnerable Images to Clusters and Workloads

1. From the JFrog Platform, under **Runtime**, select **Live Assessment**.&#x20;
2. Under the **Images** tab, select an image with detected risks.
3. Select an image **Tag** with detected risks.\
   The detailed view opens.
4. To view the risks detected in the workloads running on vulnerable images, select the **Workloads** tab.
5. To view the risks detected in the clusters containing workloads running on vulnerable images, select the **Clusters** tab.

