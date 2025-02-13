# VS Code

The JFrog Extension for Visual Studio Code empowers developers with robust security scanning and vulnerability remediation directly within their IDE. By integrating JFrog Xray, the extension helps identify and fix security issues early in the development lifecycle, reducing remediation costs and ensuring secure code from the outset.

## Key Security Capabilities

### **Software Composition Analysis (SCA)**

* Scan project dependencies for security vulnerabilities.
* Access enriched CVE data provided by the JFrog Security Research team. Learn more.

### **Advanced Security**

_Requires JFrog Xray version 3.66.5 or higher and an Enterprise X / Enterprise+ subscription with Advanced Security._

* **Contextual Analysis**: Identify the applicability of CVEs in your application and analyze third-party package usage.
* **Automated Validation**: Reduce false positives and noise by automatically verifying high-impact vulnerabilities with specific exploit prerequisites. Learn more.

### **Infrastructure as Code (IaC) Scanning**

* Analyze IaC files (e.g., Terraform) for vulnerabilities and misconfigurations before cloud deployment.
* Gain actionable insights to secure IaC configurations.

### **Secrets Detection**

* Detect and prevent the inclusion of sensitive data, such as credentials and API keys, in your codebase.

#### Additional Benefits

* Inline visibility of security issues directly in your code.
* Contextual insights, impact assessments, and remediation guidance.
* Centralized security issue tracking in the JFrog tab.
* One-click upgrade to fixed versions for resolvable security issues.
* Continuous tracking of code security across the CI/CD pipeline.
* Built-in JFrog File Spec JSON schema support for specific file patterns (`**/filespecs/*.json`, `filespec.json`, `.filespec`). Learn more.
