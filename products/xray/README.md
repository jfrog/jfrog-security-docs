# Xray

JFrog Xray is a Software Composition Analysis (SCA) tool that scans source code and binaries to detect vulnerabilities, malicious packages, license risks, and operational issues in many programming languages and LLM Models scanning. Powered by JFrog Security Research, Xray provides advanced threat information based on the group's enriched CVE information.

Xray integrates natively with JFrog Artifactory, enabling binary scanning with a single checkbox. For source code, Frogbot and IDE plugins provide immediate feedback and autofixes, while build-info scanning analyzes builds to catch risks introduced during the build process.

Xray’s policies and watches help enforce security and compliance thresholds by flagging risky components. With continuous monitoring, it tracks emerging threats and alerts teams to new vulnerabilities in existing components.

#### Comprehensive Security Coverage

Combining source code and binary scanning, Xray delivers shift-left security for early detection and binary-level validation for final artifact safety. This ensures end-to-end protection across the entire software development lifecycle.

**Where Xray Fits in the JFrog Security Timeline**

Security in the software development process must be continuous, spanning from code development to deployment and beyond. JFrog Xray integrates into multiple stages of the software lifecycle, ensuring that security is proactive rather than reactive.

#### **JFrog Security Timeline: Key Stages & Xray’s Role**

| Stage                                                      | Xray's Role                                                                                                                                                              |
| ---------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Code Development (Developers)**                          | ✅ **Scans dependencies in IDEs & CLI** before committing code.                                                                                                           |
| **Code Merge (SCM)**                                       | ✅ **Scans dependencies using Frogbot** to make sure Pull requests do not introduce new security issues. It can also create Pull requests to auto-fix risky dependencies/ |
| **Build & Package (CI/CD Security)**                       | ✅ **Scans builds in CI/CD pipelines** to detect vulnerabilities.                                                                                                         |
| **Artifact Management (Repository Security)**              | ✅ **Continuously scans Artifactory repositories** for security, compliance, and operational risks.                                                                       |
| **Release Validation (Pre-Deployment Security)**           | ✅ **Scans release bundles** before promotion or distribution to ensure compliance and security.                                                                          |
| **Production & Runtime Security (Requires JFrog Runtime)** | ✅ **Monitors for newly discovered vulnerabilities** in already deployed artifacts.                                                                                       |

**Install Xray**

The Xray installation instructions can be found [here](https://jfrog.com/help/r/jfrog-installation-setup-documentation/installing-xray).&#x20;

### **Business Needs for JFrog Xray**

Organizations face increasing challenges in securing their software supply chain. Key concerns include:

* **Managing SBOM (Software Bill of Materials)**\
  Xray supports ingesting and exporting SBOMs, including CycloneDX, to provide visibility into your software components. This ensures transparency and helps track dependencies across the software supply chain.
* **Policy Enforcement & Integrations**\
  Xray enforces security policies through integrations with systems like JIRA and Webhooks. Automated alerts and effective alerting workflows ensure teams are quickly informed about vulnerabilities, keeping security issues in check across the development lifecycle.
* **Detecting Malicious Components**\
  Xray scans dependencies for known vulnerabilities and malicious packages, alerting teams to compromised components before they can affect the development process or enter production, helping reduce the risk of supply chain attacks.
* **Reducing Security Overhead**\
  Xray automates vulnerability detection and policy enforcement, while Frogbot offers autofix capabilities. This reduces manual effort, allowing security teams to focus on critical tasks while ensuring continuous security monitoring.
* **Improving Development Efficiency**\
  Xray helps developers catch vulnerable or non-compliant dependencies early using Frogbot and IDE plugins. This reduces rework, speeds up development, and maintains security throughout the process.
