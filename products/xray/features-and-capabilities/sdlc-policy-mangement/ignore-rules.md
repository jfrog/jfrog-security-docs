# Ignoring Violations in JFrog Xray: Understanding Ignore Rules

In security and compliance management, **not all violations require immediate action**. Some vulnerabilities or policy violations may be **low risk**, **false positives**, or **already mitigated** through alternative security controls.

JFrog Xray provides **Ignore Rules**, a feature that allows teams to **temporarily or permanently** suppress specific violations. This ensures that development teams can **focus on critical issues** while maintaining compliance and security standards.

***

### **What Are Ignore Rules in Xray?**

Ignore Rules are **configurable exceptions** that allow users to **suppress violations** under certain conditions. These rules prevent violations from **blocking builds, failing deployments, or triggering alerts**, while still keeping them **logged for reference**.

Ignoring a violation **does not remove it from the database**—it simply **hides the violation from triggering alerts and enforcement actions** for a defined period.

#### **Why Use Ignore Rules?**

✔ **Reduce Noise** – Suppress **non-actionable** vulnerabilities and violations.\
✔ **Improve Efficiency** – Allow teams to **focus on high-risk issues**.\
✔ **Avoid False Positives** – Ignore vulnerabilities **that do not apply** to the specific environment.\
✔ **Mitigated Vulnerabilities** – Suppress CVEs that are **already patched** via **configurations, network controls, or runtime mitigations**.

***

### **How Ignore Rules Work**

Ignore Rules can be applied to:

* **Specific CVEs** – Ignore a vulnerability affecting a component.
* **Components or Artifacts** – Suppress violations on a package or artifact.
* **Policy Violations** – Ignore a violation triggered by security, compliance, or operational policies.
* **Watches and Scopes** – Apply the ignore rule to a specific **repository, build, or release bundle**.

Ignored violations remain **visible in audit logs** but **do not trigger alerts, block actions, or impact CI/CD workflows**.

***

### **Types of Ignore Rules in Xray**

#### **1. Temporary Ignore** _(Set Expiration Date)_

**Use Case:** When a **fix is planned** for a later release.

✔ Suppresses violations for a **defined period** (e.g., **30 days**).\
✔ The violation **automatically reactivates** after the expiration date.\
✔ Useful for vulnerabilities that are **not currently exploitable** but will be addressed in a future update.

**Example:**\
A development team is aware of a **CVE in a library**, but a **patched version will be released in 2 weeks**. They apply an **ignore rule for 14 days** to prevent unnecessary alerts.

***

#### **2. Permanent Ignore** _(No Expiration)_

&#x20;**Use Case:** When a **vulnerability is not applicable** or is already mitigated.

✔ **Permanently suppresses** a violation.\
✔ Useful when a **CVE does not affect the actual usage** of the component.\
✔ Can be **manually removed** later if needed.

**Example:**\
A security vulnerability **only affects a deprecated function** in a library that the team **does not use**. Since the function is never called in production, the violation is **ignored permanently**.

***

#### **3. Ignore Based on Scope (Repository, Build, Release Bundle)**

**Use Case:** When a violation should be ignored **only in a specific context**.

✔ Allows ignoring violations for a **specific repository, project, or build**.\
✔ Prevents unnecessary enforcement actions in **low-risk environments** (e.g., dev/staging).\
✔ Ensures that the **same violation is still enforced elsewhere** (e.g., in production).

**Example:**\
A vulnerability is detected in a **staging environment**, but **does not exist in production**. The team applies an ignore rule **only for the staging repository**, ensuring security policies remain strict in production.

***

### **Best Practices for Using Ignore Rules in Xray**

✔ **Set Expiration Dates for Temporary Ignores** – Ensure violations are **reevaluated periodically**.\
✔ **Document Ignore Reasons** – Maintain transparency for **security audits and compliance**.\
✔ **Use Scope-Based Ignores** – Avoid **suppressing violations globally** unless necessary.\
✔ **Review Ignored Violations Regularly** – Periodically check **which vulnerabilities are ignored** and **reassess risks**.

***

### **Conclusion**

Xray’s **Ignore Rules** provide a **flexible way to manage security and compliance violations** without compromising software security. By allowing teams to **temporarily or permanently suppress violations**, Xray helps reduce noise, streamline workflows, and focus on **genuinely critical threats**.

