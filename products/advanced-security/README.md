# Advanced Security

_Advanced Security is available with the **Enterprise X** or **Enterprise+** license, along with the **Advanced Security Add-on**._

***

JFrog **Advanced Security** provides advanced scanning for both source code and binaries, powered by proprietary engines developed by JFrog's **Security Research** team. Recognized for their industry-leading accuracy and speed, these engines help organizations identify and address critical security risks across the software development lifecycle (SDLC).

Advanced Security examines all pillars of the software supply chain, including first-party code, third-party packages, secrets, misconfigurations, and vulnerabilities in infrastructure-as-code (IaC), ensuring comprehensive coverage and faster remediation.

#### First-Party Code: JFrog Static Application Security Testing

JFrog’s proprietary **Static Application Security Testing (SAST)** engine scans your first-party code to identify vulnerabilities, including zero-day threats. It performs fast, accurate, cross-file analysis and runs locally (without sending your code to a server) for secure, efficient scanning. The engine focuses on critical areas such as database queries, outgoing connections, OS commands, and other operations that could be exploited by attackers if not properly sanitized. By scanning your code early and providing actionable remediation advice, JFrog SAST helps eliminate risks in development before they reach production.

#### Third-Party CVEs and Contextual Analysis

JFrog Advanced Security enhances the results from JFrog Xray by performing **contextual analysis** on third-party dependencies. This engine determines whether detected **CVEs** are relevant to your specific first-party code, helping you focus on vulnerabilities that matter most. With continuous updates from JFrog’s Security Research team, it filters out irrelevant issues, reducing noise and prioritizing critical threats.

You can directly request JFrog Research to investigate a specific CVE for enhanced information or even ask for a new contextual analysis scanner if one does not already exist. Read all about our research team [here](https://research.jfrog.com/).

#### Secrets and Misconfiguration Detection

Advanced Security helps prevent accidental exposure of **Secrets** such as API keys, passwords, and tokens through its secrets detection capabilities. In addition, it scans for **misconfigurations** across applications, services, and Infrastructure as Code (IaC). By identifying weak security practices and insecure configurations early, JFrog Advanced Security prevents these risks from becoming exploitable vulnerabilities in production.

### Where Advanced Security Fits in the JFrog Security Timeline

| Stage                                                  | Advanced Security's Role                                                                                                                                          |
| ------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Code Development (Developers)                          | Scans dependencies in IDEs & CLI before committing code                                                                                                           |
| Code Merge (SCM)                                       | Scans dependencies using Frogbot to make sure pull requests do not introduce new security issues. It can also create Pull requests to auto-fix risky dependencies |
| Build & Package (CI/CD Security)                       | Scans builds in CI/CD pipelines to detect vulnerabilities                                                                                                         |
| Artifact Management (Repository Security)              | Continuously scans Artifactory repositories for security, compliance, and operational risks                                                                       |
| Release Validation (Pre-Deployment Security)           | Scans release bundles before promotion or distribution to ensure compliance and security.                                                                         |
| Production & Runtime Security (Requires JFrog Runtime) | Monitors for newly discovered vulnerabilities in already deployed artifacts                                                                                       |



* When? During software development, as code is built into artifacts and images.
* Purpose? Ensure security at the source and container levels.
* Key Actions:
* Identify exposed secrets, misconfigurations, and malware.
* Harden software against exploits before deployment.
* Use JFrog Catalog insights to flag high-risk dependencies.

### Business Needs

* **Business Needs for JFrog Advanced Security**\
  As security threats become more sophisticated, organizations require deeper, more contextual security insights beyond traditional vulnerability scanning. JFrog Advanced Security provides a holistic approach to protecting the software supply chain by detecting critical risks across source code, binaries, infrastructure-as-code (IaC), and runtime environments. Key concerns include:
* **Context-Aware Vulnerability Detection**\
  Traditional vulnerability scanners generate excessive noise, overwhelming teams with irrelevant results. JFrog Advanced Security’s **Contextual Analysis** prioritizes risks by analyzing whether a detected CVE is truly exploitable based on how dependencies are used within first-party code. This reduces false positives and ensures teams focus on the vulnerabilities that matter most.
* **Secrets and Misconfiguration Protection**\
  Leaked credentials and misconfigurations are leading causes of security breaches. Advanced Security scans for **hardcoded secrets, API keys, and misconfigurations** across applications, containers, and infrastructure, preventing unintended data exposure and reducing compliance risks.
* **Proactive Supply Chain Security**\
  Software supply chain attacks are on the rise, targeting third-party dependencies and build environments. Advanced Security detects **malicious packages, typosquatting attacks, and package impersonation**, ensuring organizations don’t unknowingly introduce compromised components into their software.
* **Deep Binary and Code Security Analysis**\
  Beyond dependency scanning, Advanced Security performs **Static Application Security Testing (SAST)** for first-party code, identifying vulnerabilities like SQL injection, insecure authentication, and command execution risks. It also analyzes compiled binaries for additional security flaws undetectable in source code alone.
* **Automated Compliance and Policy Enforcement**\
  Meeting regulatory requirements like SOC 2, ISO 27001, and NIST can be challenging. Advanced Security automates **policy enforcement and security monitoring**, integrating with existing workflows (JIRA, webhooks) to ensure compliance without slowing down development.
* **Reducing Security Team Overhead**\
  With security shifting left, developers need tools that enhance security without disrupting workflows. JFrog Advanced Security integrates into **IDEs, CI/CD pipelines, and repositories**, automating remediation suggestions and enabling teams to fix issues early, minimizing manual effort and increasing efficiency.

