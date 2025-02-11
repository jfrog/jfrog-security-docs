# Overview

In today's software development landscape, organizations rely heavily on open-source and third-party packages to accelerate development. However, this introduces risks such as security vulnerabilities, license compliance issues, and supply chain attacks. JFrog Curation addresses these concerns by providing an automated, policy-driven approach to controlling software package usage.

### **Where JFrog Curation Sits in the Security Timeline**

JFrog Curation is **the first line of defense** in securing an organization’s software supply chain. It operates at the **package acquisition stage**, preventing risky dependencies from entering repositories before they are even used in development, testing, or production.

**JFrog Curation (🔍 Pre-Download OSS Governance)**

* When? **As OSS packages are fetched for use.**
* Purpose? **Automate the enforcement of security and compliance policies.**

***

### **Business Needs for JFrog Curation**

Organizations face increasing challenges in managing the security and compliance of their software supply chain. These include:

* **Preventing Supply Chain Attacks**: Attackers increasingly target public package repositories to inject malicious software. JFrog Curation prevents the download of risky or compromised packages before they enter the development environment.
* **Managing Open-Source Risks**: Open-source software (OSS) dependencies come with security vulnerabilities, license restrictions, and potential legal risks. Organizations need a systematic way to control which packages can be used.
* **Regulatory Compliance & Governance**: Compliance frameworks (e.g., GDPR, HIPAA, SOC 2) require organizations to ensure that external dependencies meet security and licensing standards.
* **Reducing Security Overhead**: Security teams often struggle with manual reviews of dependencies. Automated package curation reduces this burden and ensures continuous compliance.
* **Enhancing Development Efficiency**: Developers lose productivity when they unknowingly introduce non-compliant or vulnerable packages and must later rework their code. Curation proactively prevents these issues.

***

### **Key Issues JFrog Curation Resolves**

| **Issue**                        | **How JFrog Curation Solves It**                                                                  |
| -------------------------------- | ------------------------------------------------------------------------------------------------- |
| **Malicious Package Downloads**  | Blocks known malicious or compromised packages before they reach developers.                      |
| **Security Vulnerabilities**     | Uses real-time metadata from the JFrog Catalog to prevent the use of packages with critical CVEs. |
| **License Compliance Risks**     | Automatically blocks packages that violate corporate legal policies.                              |
| **Unapproved Open-Source Usage** | Allows only pre-approved or vendor-certified packages using allowlist policies.                   |
| **Aging and Abandoned Packages** | Prevents the use of outdated, unmaintained, or deprecated dependencies.                           |
| **Operational Instability**      | Ensures that only stable and secure package versions are used in production.                      |
