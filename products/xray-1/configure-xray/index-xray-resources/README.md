# Index Xray Resources

### **What Does "Indexing Resources" Mean in Xray?**

In JFrog Xray, indexing resources refers to the process of analyzing, mapping, and storing metadata about software components to enable deep security scanning and compliance monitoring.

Indexing is a prerequisite for scanning—Xray does not automatically scan all repositories, builds, or artifacts unless they are explicitly indexed. By indexing a resource, Xray can track dependencies, vulnerabilities, licenses, operational risks, and violations effectively.

### **Why is Indexing Important?**

* Enables vulnerability and compliance scanning – Xray can only scan components that are indexed.
* **Provides dependency visibility** – Helps track direct and transitive dependencies in artifacts, builds, and release bundles.
* **Improves scan performance** – Indexed resources are analyzed more efficiently, reducing scan times.
* **Allows impact analysis** – Identifies which artifacts are affected by newly discovered vulnerabilities.

**Example:** If a new CVE is discovered, Xray automatically identifies all indexed artifacts (within the defined retention period) that contain the vulnerable package.

### **Types of Indexable Resources in Xray**

Xray supports indexing at three levels:

| **Resource Type**   | **Description**                                             |
| ------------------- | ----------------------------------------------------------- |
| **Repositories**    | Indexes artifacts stored in JFrog Artifactory repositories. |
| **Builds**          | Indexes CI/CD-generated builds, including all dependencies. |
| **Release Bundles** | Indexes software packaged for distribution.                 |

***

### **How Indexing Works in Xray**

#### **1. Indexing Repositories/Builds/ Release Bundles**

* Xray does not automatically index all resources—you must enable indexing for a specific resource.
* Indexed repositories allow Xray to scan artifacts as they are uploaded or modified.

#### **2. Narrow Down Scope (Optional)**

#### **2.  Set a Retention Period (Optional)**

#### 3. Trigger Indexing of Existing Artifacts&#x20;
