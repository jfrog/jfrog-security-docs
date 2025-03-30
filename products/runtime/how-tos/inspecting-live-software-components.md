# Inspecting Live Software Components

This guide provides instructions on inspecting live software components using the Runtime **Live Assessment** capability. This enables you to view and search live runtime information, identify potential security risks, and monitor the health of your runtime environments.&#x20;

### Before You Begin&#x20;

• Data in the Live Assessment is retained for 10 days before deletion.&#x20;

### Risks Runtime Alerts Against

• **Malicious Packages**: Detects harmful code within software components.&#x20;

• **Untrusted Images**: Identifies images from unverified registries.&#x20;

• **Critical Applicable CVEs**: Highlights critical vulnerabilities identified through contextual analysis.&#x20;

• **Integrity Violations**: Flags discrepancies between Artifactory images and running cluster binaries.&#x20;

### Active Components Runtime Inspects

| Runtime Component                                                                    | Description                                                                                                                             |
| ------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------- |
| [Images ](inspecting-live-software-components.md#inspecting-images-in-runtime)       | Packaged files containing code and configurations needed to run applications, traceable to their source in JFrog Artifactory.           |
| [Workloads](inspecting-live-software-components.md#inspecting-workloads-in-runtime)  | Applications and services actively running in Kubernetes clusters, managed by resources like Deployments, StatefulSets, or DaemonSets.  |
|  [Processes](inspecting-live-software-components.md#inspecting-processes-in-runtime) | Individual executable instances within workloads, detailed with vulnerability data for monitoring and risk management.                  |

### Inspecting Images in Runtime&#x20;

Gain comprehensive visibility into runtime images by tracing them back to their JFrog Artifactory source, evaluating usage, and identifying security risks. Quickly spot untrusted sources, integrity violations, and critical CVEs, with key details like the highest risk level, total vulnerabilities, and tag-specific insights to prioritize remediation. By detecting discrepancies between Artifactory images and running binaries, you can proactively mitigate risks and strengthen your runtime security.&#x20;

#### Accessing Image Information&#x20;

Image information includes a number of associated workloads, cluster and namespace details, image path in Artifactory, associated deployer information, and a list of vulnerabilities&#x20;

1\. From the JFrog Platform, under **Runtime**, select **Live Assessment**.&#x20;

2\. Select the **Images** tab to view all detected images.&#x20;

3\. Select an image.&#x20;

4\. Click on the desired image tag from the Images tab.&#x20;

### Inspecting Workloads in Runtime&#x20;

Inspect workloads in your runtime environment with Runtime Live Assessment to monitor active applications, identify security risks, and gain infrastructure-wide insights. Workloads, managed by Kubernetes resources like Deployments, StatefulSets, DaemonSets, or Jobs, consist of containers linked to images and running processes. The Workloads Table highlights risks such as integrity violations, untrusted registries, critical CVEs, and malicious packages, along with total vulnerabilities, workload status, and location details across clusters, nodes, and namespaces to help you quickly detect and address security issues.&#x20;

#### Accessing Workloads in Runtime Live Assessment&#x20;

1\. From the JFrog Platform, under **Runtime**, select **Live Assessment**.&#x20;

2\. Select the **Workloads** tab to view all detected workloads.&#x20;

3\. Select a workload.&#x20;

4\. Click on a specific process to see detailed information.&#x20;

### Inspecting Processes in Runtime&#x20;

Before You Begin:

• It is essential you have Runtime Impact (Controller + Sensors)&#x20;

1\. From the JFrog Platform, under **Runtime**, select **Live Assessment**.&#x20;

2\. Select the **Processes** tab to view all detected workloads.&#x20;

3\. Review the Processes Table.&#x20;

4\. (Optional) Apply filters to narrow down processes based on specific criteria.
