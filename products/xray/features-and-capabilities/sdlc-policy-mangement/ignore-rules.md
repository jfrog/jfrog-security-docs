# Ignoring Violations in JFrog Xray: Understanding Ignore Rules

In security and compliance management, **not all violations require immediate action**. Some policy violations may be **low risk**, **false positives**, or **already mitigated** through alternative security controls.

JFrog Xray provides **Ignore Rules**, a feature that allows teams to **temporarily or permanently** suppress specific violations. This ensures that development teams can **focus on critical issues** while maintaining compliance and security standards.

***

### **What Are Ignore Rules in Xray?**

Ignore Rules are **configurable exceptions** that allow users to **suppress violations** under certain conditions. These rules prevent violations from **blocking builds, failing deployments, or triggering alerts**, while still keeping them **logged for reference**.

Ignoring a violation **does not remove it from the database**—it simply **hides the violation from triggering alerts and enforcement actions** for a defined period.

#### **Why Use Ignore Rules?**

**Reduce Noise** – Suppress **non-actionable** violations.\
**Improve Efficiency** – Allow teams to **focus on high-risk issues**.\
**Avoid False Positives** – Ignore violations **that do not apply** to the specific environment.

***

### **How Ignore Rules Work**

Ignore Rules can be applied to:

* **Security** - Ignore a vulnerability affecting a component
* **License -** Ignore a specific license violation of a component
* **Operational Risk** - Ignore an operational risk violation&#x20;
* **Watches and Scopes** – Apply the ignore rule on a specific watch, component, artifact, build, or release bundle.

Ignored violations remain **visible in audit logs** but **do not trigger alerts, block actions, or impact CI/CD workflows**.

***

### **Types of Ignore Rules in Xray**

#### **1. Temporary Ignore** _(Set Expiration Date)_

**Use Case:** When a **fix is planned** for a later release.

Suppresses violations for a **defined period** (e.g., **30 days**).\
The violation **automatically reactivates** after the expiration date.

**Example:**\
Useful for vulnerabilities that are **not currently exploitable** but will be addressed in a future update.

***

#### **Permanent Ignore** _(No Expiration)_

&#x20;**Use Case:** When a **violation is a false positive**

**Permanently suppresses** a violation.

**Example:**\
When a **CVE does not affect the actual usage** of the component.\
Can be **manually removed** later if needed.

***

#### **3. Ignore Based on Scope**&#x20;

**Use Case:** When a violation should be ignored **only in a specific context**.

Allows ignoring violations for a specific watch, component, artifact, build, or release bundle.

**Example:**\
When you do not want to block the download of a specific artifact, you can ignore all violations of that artifact.&#x20;

***

### **Best Practices for Using Ignore Rules in Xray**

**Set Expiration Dates for Temporary Ignores** – Ensure violations are **reevaluated periodically**.\
**Use Scope-Based Ignores** – Avoid **suppressing violations globally** unless necessary.\
**Review Ignored Violations Regularly** – Periodically check **which vulnerabilities are ignored** and **reassess risks**.

***

Would you like a **step-by-step guide on creating Ignore Rules** in Xray? See

