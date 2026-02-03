# Runtime Impact

### Version 1.2

#### Support in OpenShift

Added [support for OpenShift](../supported-technologies/) containers in Self-Hosted and Cloud environments.

### Version 1.3

#### Workload Automation Service

Create event-driven [Workers to automate responses to workload](../configure-runtime/workload-automation-service.md) changes.\
Workers provide a serverless execution environment, triggered by real-time platform events like image updates and security insights.

#### Mapping Vulnerable Images to Clusters and Workloads

Quickly [identify where risks exist in your environment by mapping vulnerable images](../how-tos/inspecting-live-software-components.md#identifying-risk-locations-in-runtime-by-mapping-vulnerable-images-to-clusters-and-workloads) to affected clusters and workloads.\
Use the Live Assessment view to identify and remediate image-based vulnerabilities across workloads and clusters more efficiently.

### Version 1.4

#### AWS Fargate Support&#x20;

JFrog Runtime now supports [AWS Fargate](../supported-technologies/), enabling serverless container execution without managing infrastructure.

#### Installation options for non-gRPC environments

Added support for configuring the Runtime Service with alternative ingress controllers and REST fallback, along with improved sensor [installation options for non-gRPC environments](https://jfrog.com/help/r/jfrog-installation-setup-documentation/installing-jfrog-runtime-security) and self-signed certificates.

### Version 1.7

#### **Live Assessment Enhancements**

* Introducing clearer vulnerability segmentation, including **Critical & High CVEs**, **Applicable CVEs** (validated via Contextual Analysis), and **Running CVEs** for active workloads.
* Previously combined CVE categories are now broken out to provide more actionable, severity-based insights.
* Image details now include richer context such as associated workloads, cluster and namespace details, registry name, repository path, providers, deployer information, and **Owners Info** (application owners).

#### **Automatic Security Scanning for Runtime-Detected Images**

Runtime now [automatically scans any container image detected](../manage-runtime.md#automatic-security-scanning) in a Kubernetes cluster. If a runtime-observed image lacks security data, the system automatically indexes and scans it using SCA and Advanced Security scanners. This ensures full, consistent security coverage across all cluster-running images with simple configuration

### Version 1.8

#### Runtime Role-Based Access Control (RBAC)

JFrog Runtime Security now enforces project-scoped [Role-Based Access Control ](../features-and-capabilities.md#access-control)(RBAC) for all runtime-detected container images.

Every image observed at runtime is associated with one or more JFrog Projects based on repository assignment or administrative configuration.

This ensures:

* **Platform Admins** maintain full visibility across all runtime assets and projects
* **Project Admins** control access to runtime assets within their assigned projects
* **Project Members** view only images and runtime data related to their project scope

RBAC significantly reduces cross-team data exposure, enforces least-privilege access, and aligns runtime visibility with organizational ownership boundaries.

#### AWS ECS Fargate Runtime Scanning Enhancements

JFrog Runtime Security expands its [AWS Fargate integration](../configure-runtime/configure-aws-ecs-fargate.md) to support secure discovery and runtime scanning of ECS workloads running on both Fargate and EC2 launch types.

Runtime now connects to AWS using dedicated IAM credentials to automatically:

* Discover ECS clusters and running tasks
* Analyze runtime workloads for vulnerabilities and security exposures
* Present centralized visibility across all Fargate-based environments

This enhancement extends runtime security coverage into fully serverless container environments while maintaining least-privilege cloud access and centralized governance.

### Version 1.9

#### Runtime Token Expirtion

Token expiration has been extended from **1 year to 2 years**, reducing renewal frequency and improving user experience, with corresponding updates to token validation logic.

#### gRPC Gateway

Enable gRPC gateway by default.

#### Helm Charts

Helm Chart Published to the JFrog GitHub Repository.

#### Automatic Registration Token Updates Without Manual Restarts

Registration tokens mounted from Kubernetes secrets are now refreshed automatically across sensors and controller when the secret changes, eliminating the need for manual restarts.

### 1.10

#### Support for Custom Self-Signed Certificates in runtime-service

Added Helm support for custom self-signed CA certificates in the runtime-service. Certificates from a Kubernetes Secret are appended to the system CA bundle and `SSL_CERT_FILE` is set so outbound TLS trusts internal CAs.

#### Helm Chart Distribution Path Updated

Updated the runtime Helm chart distribution URL from `https://charts.jfrog.io/runtime/` to the root `https://charts.jfrog.io/` repository.

#### Token Expiration Alerts in Cluster Management

Added token expiration alerts to the Cluster Management page, including:

* **Pre-expiration warning** – displayed 3 months before a cluster token expires, giving users time to rotate credentials.
* **Post-expiration alert** – displayed after the token has expired, indicating that the cluster is no longer authenticated and may stop functioning correctly.
