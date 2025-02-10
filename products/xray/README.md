# Xray

JFrog Xray is a **universal software composition analysis (SCA) and security solution** that provides **deep security, compliance, and operational risk insights** across the **entire software development lifecycle (SDLC)**. Integrated seamlessly with **JFrog Artifactory**, Xray enables organizations to **proactively detect vulnerabilities, enforce compliance policies, and manage software supply chain risks** before applications reach production.

Xray is a **core component of the JFrog Security Suite**, playing a **critical role in DevSecOps** by helping developers, security teams, and compliance officers identify and mitigate security issues **as early as possible in the development pipeline**.

***

### **Where Xray Fits in the JFrog Security Timeline**

Security in the software development process must be **continuous**, spanning from **code development to deployment and beyond**. JFrog Xray integrates into multiple stages of the software lifecycle, ensuring that security is **proactive rather than reactive**.

#### **JFrog Security Timeline: Key Stages & Xray’s Role**

| **Stage**                                        | **What Happens Here?**                                                      | **Xray's Role**                                                                                    |
| ------------------------------------------------ | --------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------- |
| **Code Development (Shift Left)**                | Developers write and commit code, often using **open-source dependencies**. | ✅ **Scans dependencies in IDEs & CLI** before committing code.                                     |
| **Build & Package (CI/CD Security)**             | CI/CD pipelines generate builds, pulling in libraries and dependencies.     | ✅ **Scans builds in CI/CD pipelines** to detect vulnerabilities before artifacts are stored.       |
| **Artifact Management (Repository Security)**    | Software components are stored in JFrog Artifactory.                        | ✅ **Continuously scans Artifactory repositories** for security, compliance, and operational risks. |
| **Release Validation (Pre-Deployment Security)** | Release bundles are created and prepared for deployment.                    | ✅ **Scans release bundles** before distribution to ensure compliance and security.                 |
| **Production & Runtime Security**                | Software is deployed to production environments.                            | ✅ **Monitors for newly discovered vulnerabilities** in already deployed artifacts.                 |

### **Business Needs for JFrog Xray**

Organizations face increasing challenges in securing their software supply chain. Key concerns include:

#### **🔹 Preventing Supply Chain Attacks**

* Attackers exploit **open-source registries** to distribute **malicious packages**.
* Xray detects and blocks **compromised components** before they enter the development pipeline.

#### **🔹 Managing Open-Source Risks**

* Dependencies introduce **security vulnerabilities, license restrictions, and operational risks**.
* Organizations require **automated scanning and policy enforcement** to control third-party software usage.

#### **🔹 Ensuring Regulatory Compliance & Governance**

* Security regulations (e.g., **NIST, GDPR, HIPAA, SOC 2**) demand strict control over software dependencies.
* Xray ensures **only compliant and secure components** enter production environments.

#### **🔹 Reducing Security Overhead**

* Security teams struggle with **manual dependency reviews** and **reactive fixes**.
* Xray automates security checks, **freeing teams to focus on high-priority threats**.

#### **🔹 Improving Development Efficiency**

* Developers unknowingly introduce **vulnerable or non-compliant dependencies**.
* Xray **proactively prevents risky components** from entering projects, reducing costly rework.

***

### **Purpose of JFrog Xray**

JFrog Xray is designed to:

✔ **Continuously scan software artifacts** for vulnerabilities and compliance issues\
✔ **Block insecure, outdated, or non-compliant dependencies** before they are used\
✔ **Automate governance** using predefined and custom security policies\
✔ **Provide real-time risk analysis** at the repository, build, and release levels\
✔ **Seamlessly integrate with JFrog Artifactory and CI/CD pipelines** for end-to-end security

***

### Main Features

#### General

* **Flexible Deployment Options** : Available as self-hosted, cloud, hybrid, or multi-cloud solutions on AWS, Google Cloud, and Microsoft Azure.
* **Native Integration with Artifactory** : Provides enhanced analysis through integration with JFrog Artifactory, leveraging shared metadata.
* **On-Demand Binary Scan** : Enables instant vulnerability reports for specific binaries through local file system scans.
* **Aggregated Reporting Features** : Xray provides an integrated view of findings from JFrog Security products, enabling organizations to generate customizable reports that encompass vulnerabilities, licensing compliance, policy violations, and operational risks. Each report allows users to define specific scopes and apply advanced filters for tailored insights, ensuring a comprehensive understanding of security and compliance across artifacts, builds, and release bundles. All reports are accessible through the JFrog Platform and REST API, facilitating easy integration into existing workflows.
* **JIRA Integration**: Seamlessly integrates with Jira to streamline issue tracking and resolution processes, allowing security vulnerabilities and policy violations detected by Xray to be automatically logged as JIRA tickets. This integration facilitates collaboration between development and security teams, ensuring timely remediation and enhanced project management.

#### SBOM

* **Vulnerability Detection -** Identifies security vulnerabilities inside your binaries - enriched by world-class database of OSS vulnerabilities from multiple sources, facilitating informed risk management.
* **License Detection and Management - Identify software licenses //TODO**
* **Operational Risk Insights** : Assesses OSS components to provide insights into their risk levels for informed decision-making.
* **Dependency Detection -** Understand dependency relationship between software components in your binaries - facilitating direct-source fixes and better contextual understanding of your software.
* **SBOM Standards Compliant Reports** : Generates Software Bill of Materials (SBOM) reports that comply with industry standards and are available in CycloneDX and SPDX formats. These reports can also incorporate Vulnerability Exploitability eXchange (VEX) information to provide detailed insights into the exploitability of identified vulnerabilities.

#### SDLC Policy Management

* **Comprehensive Rule-based Policy** : Implements customizable, rule-based policies to enforce security and compliance standards throughout the software development lifecycle, ensuring that builds meet organizational guidelines before deployment.
* **Extensible Policy Scoping (Watches)** : Allows users to define granular policy scopes, known as "Watches," that can monitor specific artifacts , repositories, builds and release bundles, enabling a tailored approach to policy enforcement based on organizational needs.
* **Intricate Waiver Mechanism (Ignore Rules)** : Provides a sophisticated waiver mechanism allowing teams to temporarily ignore certain policy violations under specific conditions, facilitating flexibility while maintaining overall compliance and security objectives.
