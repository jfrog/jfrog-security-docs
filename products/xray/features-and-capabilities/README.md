# Features and Capabilities

JFrog Xray is a **Software Composition Analysis (SCA) and security tool** that enables organizations to secure their software supply chain by detecting vulnerabilities, license compliance issues, and operational risks. Below is an in-depth explanation of its key features.

### &#x20;[**Software Composition Analysis (SCA)**](sca/)

**What it does:**\
Xray performs deep analysis of **artifacts, dependencies, and software components** to identify security vulnerabilities and compliance violations.

**Why it matters:**\
Developers and security teams can proactively identify vulnerabilities in open-source and proprietary code before releasing software.&#x20;

***

### [**Developer Experience & Shift-Left Security with Xray Scanning in IDEs and CLI**](broken-reference)

**What it does:**\
JFrog Xray enables developers to identify and remediate security vulnerabilities **early in the development lifecycle** by integrating directly into IDEs and CLI tools. This **shift-left approach** ensures that security is addressed **before code is committed or built**.

For **developers and DevOps engineers**, JFrog Xray provides CLI-based security scanning through **JFrog CLI**.

***

### **Deep Recursive Scanning**

**What it does:**\
Unlike traditional scanners, Xray **recursively scans all layers** of software artifacts, including **zip, tar, Docker images, and compiled binaries**.

**Key Capabilities:**

* **File-based Analysis:** Extracts and scans all files within an artifact.
* **Recursive Layer Inspection:** Ensures no hidden vulnerabilities exist at any layer.
* **OS and Container Security:** Scans **Docker, OCI, Debian, RPM, and Alpine packages**.

**Why it matters:**\
Provides **greater visibility into software components**, ensuring no vulnerabilities are overlooked.

***

### **Impact Analysis**

**What it does:**\
Analyzes how vulnerabilities impact different components in an organization’s software **dependency graph**.

**Key Capabilities:**

* **Dependency Tracking:** Identifies affected projects based on security issues.
* **Contextual Analysis:** Determines **real-world exploitability** of vulnerabilities. (with [JFrog Advanced Security](../../advanced-security/))
* **Fix Version Detection:** Suggests available security patches for affected components.

**Why it matters:**\
Reduces false positives and **prioritizes vulnerabilities** that pose the most risk.

***

### [**Policy-Based Security Enforcement**](sdlc-policy-mangement/)

**What it does:**\
Allows organizations to define security and compliance policies that enforce governance across software development and deployment.

**Why it matters:**\
Automatically **blocks non-compliant or vulnerable artifacts** before they reach production.

***

### [**Operational Risk Management**](./#operational-risk-management)

**What it does:**\
Detects **risks beyond security vulnerabilities**, such as outdated or deprecated software components.

**Why it matters:**\
Ensures that **unmaintained** software does not introduce security risks.

***

### [**Malicious Package Detection**](./#malicious-package-detection)

**What it does:**\
Identifies and blocks **intentionally harmful** open-source packages and machine-learning models.

**Why it matters:**\
Prevents **supply chain attacks** caused by malicious dependencies.

***

### [**Software Bill of Materials (SBOM)**](sca/export-scan-results.md)

**What it does:**\
Generates an **SBOM (Software Bill of Materials)**, listing all software components and dependencies.

**Why it matters:**\
Provides **full visibility into software supply chains** for compliance and security audits.

***

### [**Advanced Reporting**](reports.md)

**What it does:**\
Generates **detailed security and compliance reports** to track vulnerabilities, license violations, and risk exposure.

**Why it matters:**\
Helps **executives and security teams** track security posture over time.

***

### [**Integration with CI/CD Pipelines**](broken-reference)

**What it does:**\
Seamlessly integrates with **CI/CD tools** to scan software **before deployment**.

**Key Capabilities:**

* **Jenkins, GitHub Actions, GitLab CI, Azure DevOps Integration.**
* **Automated Build Scanning:** Prevents vulnerable builds from being promoted.
* **Fail Fast Mechanisms:** Stops insecure components from entering production.

**Why it matters:**\
Shifts security **left in the development lifecycle**, reducing remediation costs.

***

### [**API & Webhooks for Custom Security Automation**](broken-reference)

**What it does:**\
Provides **extensive APIs and webhook support** for integrating Xray into custom security workflows.

**Key Capabilities:**

* **REST APIs:** Automate scans, generate reports, and retrieve security insights.
* **Custom Webhooks:** Trigger actions on security violations (e.g., Slack notifications, SIEM alerts).
* **Custom Integrations:** Connect with third-party security tools and threat intelligence feeds.

**Why it matters:**\
Enables **automated security monitoring and response**.

