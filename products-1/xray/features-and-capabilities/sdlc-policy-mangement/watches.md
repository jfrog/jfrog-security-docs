---
description: Monitoring Security and Compliance Across Your Software Artifacts
---

# Watches in JFrog Xray

Security and compliance in modern software development require **continuous monitoring** of dependencies, builds, and repositories. JFrog Xray uses **Watches** as a powerful mechanism to **track, analyze, and enforce policies** on software artifacts throughout the development lifecycle.

By configuring Watches, organizations can **proactively detect security vulnerabilities, enforce compliance policies, and manage operational risks** across their entire **software supply chain**.

***

### **What Are Watches in Xray?**

A **Watch** in JFrog Xray is a **customizable security and compliance monitoring entity** that allows teams to track **specific repositories, builds, and release bundles**.

Watches enable:\
✔ **Targeted Monitoring** – Focus on **specific artifacts, repositories, builds, or projects**.\
✔ **Automated Security & Compliance** – Apply **predefined policies** to trigger violations.\
✔ **Policy-Driven Governance** – Enforce **security, legal compliance, and operational risk policies**.\
✔ **Proactive Threat Detection** – Identify **vulnerabilities, misconfigurations, and unapproved licenses** before they become a risk.

Instead of scanning **all artifacts globally**, Watches allow users to **define what to monitor and how to respond**.

***

### **How Watches Work in Xray**

#### **1. Define a Watch Scope**

Watches let you specify **which components to monitor** by selecting:

* **Repositories** – Scan artifacts stored in a specific Artifactory repository.
* **Builds** – Monitor artifacts produced by a specific CI/CD pipeline.
* **Release Bundles** – Track security and compliance of software **before distribution**.

This enables teams to apply different policies to different stages of the **Software Development Lifecycle (SDLC)**.

***

#### **2. Apply Policies to the Watch**

Watches enforce **custom policies** based on organizational security and compliance needs.

**Common Policy Types Applied to Watches**

✔ **Security Policies** – Detect and block **vulnerabilities** in open-source components.\
✔ **Compliance Policies** – Ensure software components comply with **license requirements**.\
✔ **Operational Risk Policies** – Identify outdated, deprecated, or unmaintained software components.

**Example:** A Watch is configured on a **production repository** to block downloads of artifacts containing **critical CVEs**.

***

#### **3. Automated Actions & Alerts**

When a Watch detects a **policy violation**, Xray can:\
🚨 **Trigger an Alert** – Notify security teams via **Slack, Jira, or email**.\
❌ **Block Downloads** – Prevent vulnerable components from being used.\
🚀 **Fail  Builds** – Stop insecure builds before deployment.\
🔍 **Generate Reports** – Provide audit-ready compliance documentation.

**Example:** If a **Go package** with a banned license is detected in a **CI/CD pipeline**, the build **automatically fails**.

***

### **Key Use Cases for Watches in Xray**

#### **1. Securing Repositories**

* Monitor **all artifacts** in a **production repository**.
* **Block downloads** of artifacts with **high-risk vulnerabilities**.
* **Detect malicious packages** in open-source dependencies.

**Example:** A Watch is applied to a **Docker repository**, ensuring all images are **scanned before deployment**.

***

#### **2. Protecting CI/CD Pipelines**

* Scan **build artifacts** as part of **CI/CD workflows**.
* Fail builds **if security violations are detected**.
* Ensure software **meets compliance requirements** before promotion.

**Example:** A Watch is applied to a **Jenkins build pipeline**, stopping the deployment of a **Node.js package** with a known security flaw.

***

#### **3. Compliance and License Enforcement**

* Monitor repositories for **unauthorized open-source licenses**.
* Enforce **company-approved licensing policies**.
* Track **multi-license components** to ensure compliance.

**Example:** A Watch ensures **only MIT and Apache 2.0-licensed software** is used, blocking GPL-licensed dependencies.

***

#### **4. Release Validation Before Deployment**

* Scan **release bundles** before software distribution.
* Ensure artifacts are **free from security risks**.
* Validate software components **before production deployment**.

**Example:** A Watch is applied to a **release bundle**, preventing the distribution of a **vulnerable Java package** to customers.

***

### **Best Practices for Using Watches in Xray**

✔ **Apply Different Watches for Different Environments** – Use **strict security policies** for **production** and more **flexible rules** for **development** environments.\
✔ **Regularly Review Watch Configurations** – Update **policies** to adapt to **new security threats** and **compliance changes**.\
✔ **Integrate Watches with CI/CD Pipelines** – Ensure **vulnerable artifacts are caught early** to reduce remediation costs.\
✔ **Use Scoped Watches** – Avoid scanning **all repositories globally**; instead, **target critical projects and environments**.

***

### **Conclusion**

Watches in JFrog Xray enable organizations to **continuously monitor and enforce security, compliance, and operational policies** across **repositories, builds, and release bundles**.

Would you like a **step-by-step guide** on setting up Watches? See
