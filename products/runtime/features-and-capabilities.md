# Features and CapabilitiesRBAC

### Core Capabilities

#### Visibility

* **Real-Time Monitoring**: Provides live status updates on images and workloads detected in monitored clusters.
* **Enhanced Visibility (Runtime Impact only)**: Offers deeper insights into running processes within clusters.

#### Trust Assessment

* Confirm whether an image originates from a trusted registry.
* Identifies potential integrity violations in images.

#### Prioritization

* **Cross-Correlation Insights**: Integrates with JFrog Xray and Advanced Security to assess the severity and relevance of detected images and potentially malicious packages.
* **Blast Radius Analysis**: Evaluates the number of workloads using specific images and their locations across clusters, helping to gauge the impact of vulnerabilities.
* **Vulnerability Prioritization (Runtime Impact only)**:
  * Determines if vulnerable code is actively loaded into memory, focusing on real threats.
  * Helps prioritize remediation efforts by identifying vulnerabilities currently in use.

#### Traceability

Enhances traceability by identifying image owners and enabling rapid risk mitigation by locating the build owner and deployer.

#### Real-Time Alerting

Automates security policy enforcement, allowing organizations to apply predefined security rules.

### Access Control

JFrog Runtime Security uses a **Role-Based Access Control (RBAC)** model that limits access to runtime-detected Docker images based on project-level permissions. Runtime Security monitors container environments and reports both trusted and untrusted images, and RBAC ensures that users see only the images associated with the projects they belong to. Admins have full visibility across all runtime data, while project-scoped users view only the images relevant to their assigned projects, reducing unnecessary exposure of sensitive information and keeping visibility aligned with each user’s responsibilities.

#### **Project-Scoped Visibility**

Every Docker image monitored by Runtime Security is associated with one or more **JFrog Projects**, based on repository assignment or admin configuration.\
When users access Runtime Security (UI or API), the system automatically filters the image list according to the projects they belong to and the roles assigned within those projects.

* **Project Members** see only the images associated with their assigned project(s).
* **Project Admins** manage which members can access their project’s runtime assets.
* **Platform Admins** can configure all projects and assign roles globally.
