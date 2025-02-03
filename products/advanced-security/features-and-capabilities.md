# Features and Capabilities

JFrog Advanced Security provides **comprehensive protection** for software supply chains by **detecting vulnerabilities, exposures, secrets, and misconfigurations** across repositories, builds, and artifacts.

## **Advanced Scanning & Analysis**

**Contextual Analysis**

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

#### **Exposures Scanning**

* **What it does:** Detects security misconfigurations, weak authentication, excessive privileges, and other non-code vulnerabilities.
* **Why it matters:** Secures applications beyond just code vulnerabilities by covering security risks in configurations and infrastructure.

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

#### **Secrets Scanning**

* **What it does:** Identifies exposed secrets such as API keys, credentials, and private keys within artifacts.
* **Why it matters:** Prevents accidental exposure of sensitive information, reducing the risk of credential leaks and unauthorized access.

#### **Token Validation**

* **What it does:** Differentiates between active and inactive access tokens using provider validation.
* **Why it matters:** Prevents unnecessary alerts for expired credentials while highlighting actively exploitable secrets.

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

