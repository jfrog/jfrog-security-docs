---
description: Enforcing Security and Compliance Throughout the Software Development Lifecyle
---

# Policies in JFrog Xray

In modern software development, security and compliance must be integrated at every stage of the Software Development Lifecycle (SDLC). JFrog Xray enables organizations to define policies that enforce security, legal compliance, and operational governance. These policies help prevent vulnerabilities, manage open-source licenses, and ensure software quality.&#x20;

### **Understanding Policies in Xray**

Policies in Xray are configurable rules that dictate how software artifacts and dependencies are assessed for security and compliance at different SDLC phases.

Xray’s policies focus on:

* **Security** – Identifying vulnerabilities and threats in software components.
* **Compliance** – Enforcing open-source license policies and regulatory standards.
* **Operational Risk** – Managing outdated, deprecated, or unmaintained dependencies.

These policies **automate decision-making** by triggering **violations, alerts, and preventive actions** (e.g. blocking actions) whenever a policy rule is met.

### **How Policies Work in Xray**

#### **1. Define Policies**

Organizations create policies based on **security, compliance, and risk requirements**. Policies include:

* **Rules** – Conditions that trigger violations (e.g. CVE severity, banned licenses).
* **Actions** – Automated responses when a rule is met (e.g. block downloads, send alerts).

#### **2. Apply Policies to Watches**

A **Watch** is a security scope that monitors:

* **Repositories**&#x20;
* **Builds**&#x20;
* **Release Bundles**
* **Projects**&#x20;

Policies are **linked to Watches** to enforce rules at specific stages of the **SDLC**.

#### **3. Automated Enforcement**

When an artifact **matches a policy rule**, Xray automatically:

* **Creates a violation** – Flags a security, compliance, or risk issue.
* **Trigger actions** –  e.g. notify developers and security teams via email or Jira.

### **Types of Policies in Xray**

Xray provides three primary **policy types**, each serving a **different aspect of software security**:

#### **1. Security Policies**

A Security Rule allows you to create a set of rules around security vulnerabilities \
**Common Security Rules:**

* Block artifacts with critical CVEs (Common Vulnerabilities and Exposures).
* Prevent downloads of malicious packages.
* Require a fix version before deployment.
* Enforce Exploitability Awareness _(available in JFrog Advanced Security)_ – ensuring only exploitable vulnerabilities are flagged.

#### **2. Compliance Policies**

A license Rule allows you to create a set of rules around license compliance. There are three possible criteria\
**Common Compliance Rules:**

* **Banned License Enforcement** – Prevents the use of GPL-licensed components in proprietary software.
* **License Allowlist** – Restricts usage to approved open-source licenses.
* **Multi-license Handling** – Defines policies when a package has multiple licenses.

#### **3. Operational Risk Policies**

Operational risk policies **assess the reliability and maintainability** of software components.\
**Common Operational Risk Rules:**

* **End-of-Life Detection** – Alerts when a dependency is no longer maintained.
* **Deprecated Package Monitoring** – Prevents the use of packages that are no longer supported.
* **Unmaintained Library Warnings** – Flags components with no updates in over 12 months.

### **SDLC Stages Where Xray Policies Are Applied**

Policies are enforced **throughout the software lifecycle**:

| SDLC Phase                           | Example Use Case                                                                                                |
| ------------------------------------ | --------------------------------------------------------------------------------------------------------------- |
| **Artifact Storage (Repositories)**  | A **Maven package with a banned license** is **blocked from upload**.                                           |
| **Builds**                           | A **build fails** due to a **critical CVE** in an npm package.                                                  |
| **Pre-Deployment (Release Bundles)** | A **Docker image within a Release Bundle** with a **vulnerable base layer** will be blocked from distribution.  |

### **Best Practices for Implementing Policies in Xray**

* **Automate CI/CD Enforcement** – Use Xray to fail builds that introduce security risks.
* **Define Policy Scopes Carefully** – Assign policies to relevant repositories, builds and release bundles.&#x20;
* **Block Promotion/Distribution of Release Bundles**&#x20;
* **Enable Continuous Monitoring** – Keep policies updated with the latest threat intelligence.
* **Use Advanced Security Features** – Utilize Exploitability Awareness and Applicability Scanning _(available in JFrog Advanced Security)_ to reduce false positives.

Would you like a **step-by-step guide on creating a Policy** in Xray? See [Create Policies.](../../configure-xray/create-policies.md)&#x20;
