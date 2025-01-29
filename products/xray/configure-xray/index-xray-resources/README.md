# Index Xray Resources

### **What Does "Indexing Resources" Mean in Xray?**

In JFrog Xray, **indexing resources** refers to the process of **analyzing, mapping, and storing metadata** about software components to enable **deep security scanning and compliance monitoring**.

Indexing is **a prerequisite for scanning**—Xray **does not automatically scan all repositories, builds, or artifacts** unless they are explicitly **indexed**. By indexing a resource, Xray can **track dependencies, vulnerabilities, licenses, and operational risks** effectively.

***

### **Why is Indexing Important?**

✔ **Enables vulnerability and compliance scanning** – Xray can only scan components that are **indexed**.\
✔ **Provides dependency visibility** – Helps track **direct and transitive dependencies** in repositories and builds.\
✔ **Improves scan performance** – Indexed resources are analyzed **more efficiently**, reducing scan times.\
✔ **Allows impact analysis** – Identifies which artifacts are affected by **newly discovered vulnerabilities**.

🚀 **Example:** If a new CVE is discovered, Xray **automatically identifies all indexed artifacts** that contain the vulnerable package.

***

### **Types of Indexable Resources in Xray**

Xray supports indexing at **three levels**:

| **Resource Type**   | **Description**                                                 | **Best Use Case**                                                            |
| ------------------- | --------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| **Repositories**    | Indexes artifacts stored in **JFrog Artifactory repositories**. | Continuous monitoring of **stored software components**.                     |
| **Builds**          | Indexes **CI/CD-generated builds**, including all dependencies. | Ensures that **build artifacts are free of vulnerabilities** before release. |
| **Release Bundles** | Indexes software **packaged for distribution**.                 | Ensures **final software releases are secure and compliant**.                |

***

### **How Indexing Works in Xray**

#### **1. Indexing Repositories**

* Xray does **not automatically index all repositories**—you must **enable indexing** for specific repositories.
* Indexed repositories allow Xray to scan artifacts **as they are uploaded or modified**.
* Supports **recursive scanning**, meaning Xray analyzes **all layers and dependencies** inside a package.

**Example:** A team enables indexing on a **Maven repository**. Every new JAR file uploaded is **automatically scanned** for vulnerabilities and compliance risks.

***

#### **2. Indexing Builds**

* Indexing builds allows Xray to scan **both direct and transitive dependencies** of a build.
* Helps in **tracking security risks from build-time dependencies**.
* Ensures that **CI/CD pipelines enforce security and compliance policies**.

**Example:** A **Jenkins build** is indexed in Xray. The build dependencies are scanned, and Xray detects a **critical vulnerability** in a third-party library before deployment.

***

#### **3. Indexing Release Bundles**

* Used to **scan final software packages before distribution**.
* Ensures that software releases are **secure, compliant, and free from operational risks**.
* Helps track **component versions and their security status** over time.

**Example:** A company is about to **release a new version of its software**. Xray indexes the **release bundle**, ensuring it **meets security and licensing requirements** before shipping to customers.
