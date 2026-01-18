# Features and Capabilities

### [**Software Composition Analysis (SCA)**](sca/)

**What it does:**\
Xray performs deep analysis of **artifacts, builds, and Release Bundles** to identify security issues, license compliance, and operational risk.

**Why it matters:**\
Organizations need to proactively identify vulnerabilities, license compliance, and code quality in their open-source and proprietary code before releasing software.&#x20;

### **Developer Experience & Shift-Left Security with Xray Scanning in IDEs and CLI**

**What it does:**\
JFrog Xray enables developers to identify and remediate security vulnerabilities **early in the development lifecycle** by integrating directly into IDEs and CLI tools. This **shift-left approach** ensures that security is addressed **before code is committed or built**.

For **developers and DevOps engineers**, JFrog Xray provides on-demand CLI-based security scanning through **JFrog CLI:**

* [Source code scanning](../../../developers/cli/scan-your-source-code.md)
* [Binary on-demand scanning](../../../developers/cli/scan-your-binaries/)

### **Deep Recursive Scanning**

**What it does:**\
Unlike traditional scanners, Xray **recursively scans all layers** of software artifacts.

**Key Capabilities:**

* **File-based Analysis:** Extracts and scans all files within an artifact.
* **Recursive Layer Inspection:** Ensures all artifact layers are covered.
* **OS and Container Security:** Scans multiple package types. For the full list, see [Supported Technologies](../supported-technologies.md).&#x20;

**Why it matters:**\
Provides **greater visibility into software components.**

### **Impact Analysis**

**What it does:**\
Analyzes how vulnerabilities impact different components in an organization’s software **dependency graph**.

**Key Capabilities:**

* **Dependency Tracking:** Identifies affected projects based on security issues.
* **Contextual Analysis:** Determines **real-world exploitability** of vulnerabilities. (with [JFrog Advanced Security](../../advanced-security/))
* **Fix Version Detection:** Suggests available security patches for affected components.

**Why it matters:**\
Reduces false positives and **prioritizes vulnerabilities** that pose the most risk.

### Impact Search

**What it does**\
Impact Search enables you to quickly [identify which artifacts in your environment are affected by specific vulnerabilities or contain particular components](../how-tos/how-to-identify-artifacts-affected-by-specific-vulnerabilities.md). The feature provides a centralized way to assess the blast radius of security issues across your software supply chain.

**Key capabilities**

* Search by vulnerability identifier (CVE or XRAY ID).
* Search by package name, type, and version.
* Correlate vulnerabilities to affected artifacts across repositories.
* Support ad-hoc investigations and incident response workflows.
* Provide consistent results aligned with Xray’s New SBOM data model.

**Why it matters**\
When a critical vulnerability is disclosed, security and DevOps teams must rapidly understand where it exists in their estate. Impact Search reduces manual investigation by allowing targeted queries across all Xray-scanned resources, helping teams prioritize remediation and risk mitigation.

### [**Policy-Based Security Enforcement**](sdlc-policy-mangement/)

**What it does:**\
Allows organizations to define security, compliance, and operational risk policies that enforce governance across software development and deployment.

**Why it matters:**\
Trigger automatic actions regarding security issues, compliance, and operational risk before they progress in the SDLC process.&#x20;

### [**Operational Risk Management**](sca/operational-risk.md)

**What it does:**\
Detects **risks beyond security vulnerabilities**, such as outdated or deprecated software components.

**Why it matters:**\
Ensures that **unmaintained** software does not introduce security risks.

### [**Malicious Package Detection**](sca/security/malicious-package-detection.md)

**What it does:**\
Identifies **intentionally harmful** open-source packages and machine-learning models.

**Why it matters:**\
Prevents **supply chain attacks** caused by malicious components.

### [**Software Bill of Materials (SBOM)**](sca/export-scan-results.md)

**What it does:**\
Generates an **SBOM (Software Bill of Materials)**, listing all software components and dependencies.

**Why it matters:**\
Provides **full visibility into software supply chains** for compliance and security audits.

### [**Advanced Reporting**](reports.md)

**What it does:**\
Generates **detailed security, compliance, and operational risk reports** to track vulnerabilities, license violations, and risk exposure.

**Why it matters:**\
Helps **organizations** track security posture over time.

### &#x20;**CI/CD Pipelines Integration**

**What it does:**\
Seamlessly integrates with **CI/CD tools** to scan software **before deployment**.

**Key Capabilities:**

* **Jenkins, GitHub Actions, GitLab CI, Azure DevOps Integration, Bamboo, TeamCity, and the JFrog CLI.**&#x20;
* **Automated Build Scanning:** Prevents vulnerable builds by indicating that the build job should fail.

**Why it matters:**\
Secure the CI/CD Pipeline and reduce remediation costs.&#x20;

