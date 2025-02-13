# Features and Capabilities

JFrog Advanced Security provides **comprehensive protection** for software supply chains by **detecting vulnerabilities, exposures, secrets, and misconfigurations** across repositories, builds, and artifacts.

## **Advanced Scanning & Analysis**

### **Contextual Analysis**

Traditional security scanners often generate large lists of vulnerabilities, many of which may not be relevant or exploitable in the specific environment where an artifact is used. **Contextual Analysis** in JFrog Advanced Security takes a more **intelligent approach** by examining how vulnerabilities function **within the context** of an artifact rather than treating all security issues as equal threats.

**What Contextual Analysis Does**

* **Eliminates False Positives**: Instead of flagging every known vulnerability in a package, Contextual Analysis determines **whether the vulnerability is actually exploitable** within the given artifact.
* **Focuses on Real Risks**: It assesses **dependencies, runtime execution paths, and configurations** to determine if a vulnerability can be leveraged by an attacker.
* **Reduces Security Noise**: Developers and security teams can focus on **actual threats** rather than being overwhelmed with irrelevant CVE alerts.
* **Improves Decision-Making**: By identifying which vulnerabilities require **immediate attention**, teams can prioritize fixes more effectively.

**Why Context Matters in Security**

A software artifact may contain a vulnerable dependency, but that **does not automatically mean** the artifact itself is at risk. For example:

* A **vulnerable function** in a package might exist but never be **called or executed** in the application.
* A **CVE may require specific environmental conditions** that do not apply to the artifact (e.g., an exploit requiring user input when the artifact is used in an automated backend process).
* Certain **dependencies may be used in a way that prevents exploitation**, such as being sandboxed or lacking the necessary permissions.

Contextual Analysis **understands these nuances** and ensures that only **relevant, actionable vulnerabilities** are flagged.

**Business & Operational Impact**

* **Accelerates Development**: Developers spend less time investigating false alarms and more time building secure software.
* **Strengthens Security Posture**: Organizations can **enforce risk-based vulnerability management**, focusing resources on critical issues rather than addressing every CVE blindly.
* **Integrates Seamlessly**: Works alongside other JFrog Advanced Security features to provide **comprehensive protection** across repositories, CI/CD pipelines, and runtime environments.

### **Exposures Scans**

Security is more than just identifying known vulnerabilities in software packages. Many breaches occur due to **misconfigurations, weak authentication, excessive privileges, and insecure development practices**—issues that traditional vulnerability scanning tools often overlook. **Exposures Scans** in JFrog Advanced Security fill this critical gap by detecting security flaws in **configurations, infrastructure, and open-source dependencies**, helping organizations **proactively prevent security incidents** before they happen.

**What Exposures Scans Do**

* **Detect Misconfigurations**: Exposures Scans analyze artifact configurations for **insecure settings** that could leave applications vulnerable, such as missing authentication, unencrypted communications, or overly permissive access controls.
* **Identify Security Weaknesses**: They flag **non-CVE-related risks**, such as hardcoded credentials, publicly accessible admin interfaces, or weak cryptographic algorithms.
* **Ensure Secure Open-Source Usage**: Many security risks stem from **improperly implemented** open-source libraries. Exposures Scans detect insecure usage patterns, such as executing untrusted scripts or failing to validate external inputs.
* **Provide Actionable Insights**: Instead of just listing issues, Exposures Scans **categorize risks based on severity** and **provide remediation guidance**, helping teams understand what needs to be fixed and why.

**Why Exposures Scanning Matters**

Security teams often focus on **known vulnerabilities (CVEs)** while overlooking misconfigurations and poor security practices, which account for a **large percentage of breaches**. Some key security risks that Exposures Scans address include:

* **Unsecured Secrets & Credentials**: Detects API keys, access tokens, and passwords embedded in code or configuration files.
* **Weak Authentication & Authorization**: Identifies missing access controls, excessive privileges, and improper authentication mechanisms.
* **Insecure Communication**: Flags improper use of HTTP instead of HTTPS, weak TLS versions, and missing encryption.
* **Exposed Services & Admin Interfaces**: Ensures that web servers, proxies, and databases are **properly configured and secured** against unauthorized access.
* **Improper Use of Open-Source Libraries**: Checks whether commonly used OSS components are being **implemented securely** within applications.

**Business & Operational Impact**

* **Reduces Attack Surface**: By securing configurations and dependencies, organizations **proactively prevent security breaches** rather than just reacting to vulnerabilities.
* **Strengthens Compliance & Governance**: Many regulatory frameworks (e.g., **NIST, ISO 27001, SOC 2**) require securing configurations and access controls—Exposures Scans **help enforce these best practices**.
* **Improves Development Efficiency**: Instead of waiting for penetration tests or audits to uncover misconfigurations, teams get **real-time feedback** on security issues within their repositories and CI/CD pipelines.

#### **On-Demand & Automated Scanning**

* **What it does:** Supports automatic and manual scans for security risks at both the **artifact** and **repository** levels.
* **Why it matters:** Ensures continuous monitoring and quick risk mitigation throughout the software development lifecycle.

## **Security Policy & Compliance**

#### **Custom Security Policies**

* **What it does:** Allows administrators to define security policies based on vulnerability severity, exposure risks, and compliance standards.
* **Why it matters:** Enables automated enforcement of security standards across teams, preventing security breaches.

#### **Xray Watches & Policy Enforcement**

* **What it does:** Monitors specific repositories, artifacts, and builds for security violations, triggering alerts or automatic remediation actions.
* **Why it matters:** Provides **real-time protection** and **automated security enforcement** to prevent unsafe artifacts from being used.

#### **Ignore Rules for Violations**

* **What it does:** Lets users suppress specific violations based on repository, file path, severity, or artifact version.
* **Why it matters:** Reduces noise by filtering out irrelevant violations while maintaining security oversight.

## **Artifact & Repository Security**

#### **Advanced Scans on Existing Artifacts**

* **What it does:** Allows security scans on previously indexed artifacts, not just new ones.
* **Why it matters:** Ensures legacy artifacts are continually assessed for emerging vulnerabilities.

#### **Repository-Wide Scans**

* **What it does:** Enables security scans across all artifacts in a repository based on deployment/download date, patterns, and exposure categories.
* **Why it matters:** Provides a holistic security view across repositories to detect and mitigate risks efficiently.

## **Secret Detection & Compliance**

One of the most overlooked but **high-risk security threats** in software development is the **accidental exposure of secrets**—API keys, authentication tokens, encryption keys, passwords, and other credentials embedded in code or configuration files. A single exposed secret can lead to **unauthorized access, data breaches, and compromised systems**, making secrets management a critical aspect of **software supply chain security**.

JFrog **Secrets Scans** proactively identify and mitigate these risks by **scanning artifacts, source code, and configuration files for exposed secrets** before they reach production.

**What Secrets Scans Do**

* **Detect Hardcoded Secrets**: Identifies API tokens, database credentials, SSH keys, and private certificates embedded in **text files, binaries, and source code**.
* **Validate Detected Secrets**: Goes beyond pattern-based scanning by verifying whether detected secrets are **active and exploitable** using **dynamic token validation** with certain providers (e.g., AWS, GitHub, Slack).
* **Classify & Prioritize Risks**: Flags exposed secrets based on **sensitivity, provider, and validation results**, helping teams **prioritize remediation efforts**.
* **Identify Weak & Expired Certificates**: Detects **self-signed, expired, and weak certificates** that could pose security risks.
* **Enforce Secure Development Practices**: Helps teams **adopt best practices** by providing visibility into insecure credential management.

**Why Secrets Scanning Matters**

* **Prevents Credential Leaks**: Exposed secrets in code repositories, logs, or configuration files can be exploited by attackers, leading to **data breaches and system takeovers**.
* **Minimizes Attack Surface**: Even if a secret is not actively used in an application, it can still be **leveraged for lateral movement** by attackers. Detecting and revoking leaked credentials early significantly reduces security risks.
* **Supports Compliance & Governance**: Many security frameworks (e.g., **SOC 2, ISO 27001, NIST, GDPR**) mandate **strong secrets management**. Secrets Scans help enforce these compliance requirements.
* **Integrates with DevSecOps Workflows**: By embedding **Secrets Scans into CI/CD pipelines and repositories**, teams **prevent security misconfigurations before deployment**.

#### **Business & Operational Impact**

* **Prevents Costly Breaches**: Avoids financial losses, regulatory fines, and reputational damage caused by **exposed credentials**.
* **Reduces Developer Burden**: Instead of relying on **manual security reviews**, Secrets Scans **automate detection** and provide **actionable remediation steps**.
* **Enhances Security Posture**: Ensures that organizations are **proactively securing** sensitive credentials **before attackers can exploit them**.

## **Integration & Automation**

#### **JFrog Advanced Security REST API**

* **What it does:** Provides API endpoints for **triggering scans, retrieving results, creating ignore rules**, and **updating repository configurations**.
* **Why it matters:** Enables security automation and integration with CI/CD pipelines and DevSecOps workflows.

#### **IDE and CLI Security Scanning**

* **What it does:** Integrates with developer tools, allowing **real-time vulnerability detection** within IDEs and command-line interfaces.
* **Why it matters:** Helps developers **fix security issues early** in the development cycle, reducing costly fixes later.

## **Secure Software Supply Chain**

#### **Software Composition Analysis (SCA)**

* **What it does:** Identifies open-source dependencies and their associated vulnerabilities.
* **Why it matters:** Prevents security risks introduced through third-party libraries, ensuring supply chain security.

#### **Infrastructure as Code (IaC) Security Scanning**

* **What it does:** Analyzes Terraform and Kubernetes configurations for security misconfigurations.
* **Why it matters:** Reduces cloud security risks by enforcing best practices in infrastructure configurations.

