# Runtime

JFrog Runtime provides in-depth security and operational insights for Kubernetes cluster environments. It detects vulnerabilities, integrity violations, and untrusted registries in real time. By continuously monitoring the runtime state of workloads and containers, it enables security and DevOps teams to identify and mitigate threats dynamically. The platform integrates with JFrog Artifactory and Xray, allowing for a comprehensive security posture that spans both pre-deployment and live runtime environments.

## **Before You Begin**

It is essential you have:

* Artifactory version 7.77.20
* Xray version 3.104.08

## **How JFrog Runtime Collects Information**

JFrog Runtime acquires its data through two primary mechanisms: the JFrog Platform and dedicated sensors deployed within customer clusters.

### **JFrog Platform Integration**

JFrog Runtime integrates with the broader JFrog Platform, which includes Artifactory and Xray. This integration allows it to:

* Correlate runtime artifacts with their sources in Artifactory.
* Enrich runtime data with security insights from Xray, identifying vulnerabilities and malicious packages.
* Aggregate and analyze data for security triaging and prioritization.

### **Runtime Sensors Installed in Customer Clusters**

Within Kubernetes environments, JFrog Runtime deploys specialized sensors to collect real-time runtime data. These sensors:

* Monitor running processes, file access, and kernel activity using eBPF technology.
* Detect security threats and integrity violations in real time.
* Transmit collected data securely to the Runtime Service within the JFrog Platform for further analysis.

## **Runtime Modes of Deployment**

JFrog Runtime offers two modes of deployment, each designed for different levels of security coverage and cost considerations.

### **Runtime Integrity** (Controller-only)

**Runtime Integrity** is installed once per cluster as a Kubernetes Deployment. It tracks Kubernetes cluster activity, including resource execution and orchestration, and collects data on Nodes, Workloads, Pods, and Containers.

Runtime Integrity provides foundational security insights:

* Includes a single sensor (the Runtime Controller) per monitored cluster.
* Focuses on monitoring Kubernetes cluster resources such as Nodes, Workloads, Pods, and Containers.
* Included in the base license without additional cost.

### **Runtime Impact** (Controller + Sensors)

**Runtime Impact** is installed on each node within a Kubernetes cluster and captures detailed runtime behavior at the process and file level using eBPF. It sends collected data to the Runtime Service for security analysis and is deployed via Kubernetes DaemonSets with host privileges.

Runtime Impact delivers a granular and comprehensive runtime security assessment:

* Deploys a sensor on every cluster node for deeper visibility.
* Monitors container runtime behavior, process executions, and file interactions.
* Sensors are purchased separately and account for most of the cost.
