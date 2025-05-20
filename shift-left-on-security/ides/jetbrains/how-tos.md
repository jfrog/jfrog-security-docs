# How-Tos

### **Software Composition Analysis (SCA)**

Each descriptor file (e.g., `pom.xml` for Maven, `go.mod` for Go) contains vulnerable dependencies.

1. Right-click a dependency to:
   * Jump to its declaration in the descriptor file.
   * Upgrade it to a fixed version (if available).
   * Create an **Ignore Rule** in Xray (_requires a JFrog Project or Watch_).
2. To view the details of a vulnerability, select one from the list.

Vulnerability details include:

* Vulnerable component information.
* Fixed versions.
* Impact paths and more.

**CVEs Contextual Analysis**

_Requires Xray 3.66.5+ and an Enterprise X/Enterprise+ subscription with Advanced DevSecOps._

* Automatically validates high-impact vulnerabilities.
* Provides contextual analysis data, including:
  * **Status** – Indicates whether a CVE is applicable.
  * **Breakdown** – Explains why a CVE is applicable or not.
  * **Remediation** – Offers mitigation steps from JFrog's research team.

**Secrets Detection**

Detects secrets exposed in the code to prevent leaks of internal tokens or credentials.

_Requires Xray 3.66.5+ and an Enterprise X/Enterprise+ subscription with Advanced DevSecOps._

1.  To ignore detected secrets, add a comment above the line with the secret:

    ```plaintext
    plaintextCopyEdit// jfrog-ignore
    ```

**Infrastructure as Code (IaC) Scanning**

_Requires Xray 3.66.5+ and an Enterprise X/Enterprise+ subscription with Advanced DevSecOps._

* Scans Terraform files for cloud and infrastructure misconfigurations.
