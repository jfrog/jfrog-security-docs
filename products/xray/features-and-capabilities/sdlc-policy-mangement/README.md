---
description: Enforcing Security and Compliance Throughout the Software Development Lifecyle
---

# SDLC Policies in JFrog Xray

In modern software development, security and compliance must be integrated **at every stage** of the **Software Development Lifecycle (SDLC)**. JFrog Xray enables organizations to define **SDLC policies** that enforce security, legal compliance, and operational governance **from development to deployment**. These policies help prevent vulnerabilities, manage open-source licenses, and ensure software quality **before code reaches production**.

***

### **Understanding SDLC Policies in Xray**

SDLC policies in Xray are **configurable rules** that dictate **how software artifacts and dependencies** are assessed for security and compliance at different **SDLC phases**.

Xray’s policies focus on:\
✔ **Security** – Identifying vulnerabilities and threats in software components.\
✔ **Compliance** – Enforcing open-source license policies and regulatory standards.\
✔ **Operational Risk** – Managing outdated, deprecated, or unmaintained dependencies.

These policies **automate decision-making** by triggering **violations, alerts, and preventive actions** whenever a policy rule is met.

***

### **How SDLC Policies Work in Xray**

#### **1. Define Policies**

Organizations create policies based on **security, compliance, and risk requirements**. Policies include:

* **Rules** – Conditions that trigger violations (e.g., CVE severity, banned licenses).
* **Actions** – Automated responses when a rule is met (e.g., block downloads, send alerts).

#### **2. Apply Policies to Watches**

A **Watch** is a security scope that monitors:

* **Repositories** (e.g., scanning all artifacts in a Maven repository).
* **Builds** (e.g., ensuring CI/CD builds are free of vulnerabilities).
* **Release Bundles** (e.g., verifying security before software distribution).

Policies are **linked to Watches** to enforce security at specific stages of the **SDLC**.

#### **3. Automated Enforcement**

When an artifact **matches a policy rule**, Xray automatically:\
🚨 **Creates a violation** – Flags a security, compliance, or risk issue.\
❌ **Blocks artifact downloads** – Prevents vulnerable components from entering production.\
🔔 **Triggers alerts** – Notifies developers and security teams via email, Jira, or Slack.\
🚀 **Fails builds** – Stops deployments that don’t meet security standards.

***

### **Types of SDLC Policies in Xray**

Xray provides three primary **policy types**, each serving a **different aspect of software security**:

#### **1. Security Policies**

Security policies help teams detect and **prevent vulnerabilities from entering software** by scanning artifacts and dependencies.\
**Common Security Rules:**\
✔ Block artifacts with **critical CVEs** (Common Vulnerabilities and Exposures).\
✔ Prevent downloads of **malicious packages**.\
✔ Require a **fix version** before deployment.\
✔ Enforce **Exploitability Awareness** _(available in JFrog Advanced Security)_ – ensuring only exploitable vulnerabilities are flagged.

**Example:**\
A developer attempts to pull a **Docker image** with a **high-risk CVE** → Xray **blocks the download** and notifies security teams.

***

#### **2. Compliance Policies**

Compliance policies enforce **open-source licensing regulations** and **corporate software usage policies**.\
**Common Compliance Rules:**\
✔ **Banned License Enforcement** – Prevents the use of **GPL-licensed** components in proprietary software.\
✔ **License Allowlist** – Restricts usage to **approved open-source licenses**.\
✔ **Multi-license Handling** – Defines policies when a package has **multiple licenses**.

**Example:**\
A CI/CD pipeline builds a **Python package** that includes a **GPL-licensed dependency** → Xray **fails the build** to prevent a legal risk.

***

#### **3. Operational Risk Policies**

Operational risk policies **assess the reliability and maintainability** of software components.\
**Common Operational Risk Rules:**\
✔ **End-of-Life Detection** – Alerts when a dependency is **no longer maintained**.\
✔ **Deprecated Package Monitoring** – Prevents the use of packages that are **no longer supported**.\
✔ **Unmaintained Library Warnings** – Flags components with **no updates in over 12 months**.

**Example:**\
A team includes a **Java library** in a new project → Xray detects the **library is no longer maintained** and **suggests an alternative**.

***

### **SDLC Stages Where Xray Policies Are Applied**

SDLC policies are enforced **throughout the software lifecycle**:

| **SDLC Phase**                       | **How Xray Applies Policies**                              | **Example Use Case**                                                              |
| ------------------------------------ | ---------------------------------------------------------- | --------------------------------------------------------------------------------- |
| **Builds**                           | Xray scans dependencies in Builds, blocking bad builds.    | A **build fails** due to a **critical CVE** in an npm package.                    |
| **Artifact Storage (Repositories)**  | Prevents risky artifacts from being stored in Artifactory. | A **Maven package with a banned license** is **blocked from upload**.             |
| **Pre-Deployment (Release Bundles)** | Ensures software is secure before deployment.              | A **Docker image** with a **vulnerable base layer** is **rejected from staging**. |
| **Production Monitoring**            | Detects emerging security threats in deployed software.    | A deployed component becomes vulnerable due to a **newly discovered CVE**.        |

***

### **Best Practices for Implementing SDLC Policies in Xray**

\
✔ **Automate CI/CD Enforcement** – Use Xray to **fail builds** that introduce security risks.\
✔ **Define Policy Scopes Carefully** – Assign policies **to relevant repositories and builds**.\
✔ **Enable Continuous Monitoring** – Keep policies **updated with the latest threat intelligence**.\
✔ **Use Advanced Security Features** – Utilize **Exploitability Awareness and Applicability Scanning** _(available in JFrog Advanced Security)_ to **reduce false positives**.

***

### **Conclusion**

JFrog Xray’s SDLC policies provide a **proactive and automated approach** to **securing software** throughout the **development lifecycle**. By enforcing **security, compliance, and operational risk policies**, Xray ensures that **only safe and compliant software components** make it to **production.**

\


O
