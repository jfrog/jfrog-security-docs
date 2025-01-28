# Curation

### **Introduction**

In today's software development landscape, organizations rely heavily on open-source and third-party packages to accelerate development. However, this introduces risks such as security vulnerabilities, license compliance issues, and supply chain attacks. JFrog Curation addresses these concerns by providing an automated, policy-driven approach to controlling software package usage.

***

#### **Business Needs for JFrog Curation**

Organizations face increasing challenges in managing the security and compliance of their software supply chain. These include:

* **Preventing Supply Chain Attacks**: Attackers increasingly target public package repositories to inject malicious software. JFrog Curation prevents the download of risky or compromised packages before they enter the development environment.
* **Managing Open-Source Risks**: Open-source software (OSS) dependencies come with security vulnerabilities, license restrictions, and potential legal risks. Organizations need a systematic way to control which packages can be used.
* **Regulatory Compliance & Governance**: Compliance frameworks (e.g., GDPR, HIPAA, SOC 2) require organizations to ensure that external dependencies meet security and licensing standards.
* **Reducing Security Overhead**: Security teams often struggle with manual reviews of dependencies. Automated package curation reduces this burden and ensures continuous compliance.
* **Enhancing Development Efficiency**: Developers lose productivity when they unknowingly introduce non-compliant or vulnerable packages and must later rework their code. Curation proactively prevents these issues.

***

#### &#x20;**Purpose of JFrog Curation**

JFrog Curation is designed to:\
✔ **Ensure software packages are vetted before they enter your development pipeline**\
✔ **Prevent the use of insecure, outdated, or non-compliant third-party dependencies**\
✔ **Automate governance through predefined and custom policies**\
✔ **Provide real-time decision-making at the repository level**\
✔ **Seamlessly integrate with JFrog Artifactory and Xray for a complete security solution**

***

#### **Key Issues JFrog Curation Resolves**

| **Issue**                        | **How JFrog Curation Solves It**                                                                  |
| -------------------------------- | ------------------------------------------------------------------------------------------------- |
| **Malicious Package Downloads**  | Blocks known malicious or compromised packages before they reach developers.                      |
| **Security Vulnerabilities**     | Uses real-time metadata from the JFrog Catalog to prevent the use of packages with critical CVEs. |
| **License Compliance Risks**     | Automatically blocks packages that violate corporate legal policies.                              |
| **Unapproved Open-Source Usage** | Allows only pre-approved or vendor-certified packages using allowlist policies.                   |
| **Aging and Abandoned Packages** | Prevents the use of outdated, unmaintained, or deprecated dependencies.                           |
| **Operational Instability**      | Ensures that only stable and secure package versions are used in production.                      |

***

#### **Benefits of Using JFrog Curation**

✅ **Stronger Security Posture**: Blocks known security risks, reducing the attack surface for software supply chain threats.\
✅ **Automated Compliance**: Ensures only license-compliant packages enter the repository, reducing legal risks.\
✅ **Efficiency for Security & DevOps Teams**: Eliminates the need for manual reviews and package approvals.\
✅ **Developer-Friendly Workflow**: Provides instant feedback on package approval status, reducing project delays.\
✅ **Seamless Integration with JFrog Platform**: Works alongside Artifactory and Xray for complete software supply chain protection.\
✅ **Auditability & Reporting**: Logs all package decisions for security audits and compliance tracking.

***

#### **How JFrog Curation Works**

1️⃣ **Enable Curation**: Activate curation at the repository level in the JFrog Platform.\
2️⃣ **Define Policies**: Configure security, licensing, and operational rules that determine package approval.\
3️⃣ **Enforce Governance**: Automatically approve or block packages based on predefined conditions.\
4️⃣ **Monitor & Audit**: Track package decisions, view audit logs, and refine policies as needed.
