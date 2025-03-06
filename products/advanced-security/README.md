# Advanced Security

_Advanced Security is available with the **Enterprise X** or **Enterprise+** license, along with the **Advanced Security Add-on**._



**JFrog Advanced Security** provides advanced scanning for both **source code and binaries**, powered by **proprietary engines** developed by JFrog's **Security Research** team. Recognized for their industry-leading accuracy and speed, these engines help organizations identify and address critical security risks across the software development lifecycle (SDLC).

Advanced Security examines all pillars of the software supply chain, including first-party code, third-party packages, secrets, misconfigurations, and vulnerabilities in infrastructure-as-code (IaC), ensuring comprehensive coverage and faster remediation.

### 1st Party Code – JFrog SAST (Static Application Security Testing)

**JFrog’s proprietary SAST engine** scans your first-party code to identify vulnerabilities, including zero-day threats. It performs **fast, accurate, cross-file analysis and runs locally (without sending your code to a server)** for secure, efficient scanning. The engine focuses on critical areas such as database queries, outgoing connections, OS commands, and other operations that could be exploited by attackers if not properly sanitized. By scanning your code early and providing actionable remediation advice, **JFrog SAST** helps eliminate risks in development before they reach production.

### 3rd Party CVEs & Contextual Analysis

**JFrog Advanced Security** enhances the results from **JFrog Xray** by performing **contextual analysis** on third-party dependencies. This engine determines whether detected **CVEs** are relevant to your specific **first-party code**, helping you focus on vulnerabilities that matter most. With continuous updates from JFrog’s **Security Research team**, it filters out irrelevant issues, reducing noise and prioritizing critical threats.

**As a JFrog Advanced Security customer, you can directly request JFrog Research to investigate a specific CVE for enhanced information or even ask for a new contextual analysis scanner if one does not already exist.** Read all about our research team [here](https://research.jfrog.com/).

### Secrets & Misconfiguration Detection

Advanced Security helps prevent accidental exposure of secrets such as API keys, passwords, and tokens through its secrets detection capabilities. In addition, it scans for misconfigurations across applications, services, and Infrastructure as Code (IaC). By identifying weak security practices and insecure configurations early, JFrog Advanced Security prevents these risks from becoming exploitable vulnerabilities in production.
