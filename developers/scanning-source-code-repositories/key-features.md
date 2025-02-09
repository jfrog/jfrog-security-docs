# Key Features

## Key Features of JFrog Frogbot

1. **Software Composition Analysis (SCA)**: Frogbot scans project dependencies for security issues, leveraging JFrog's expansive vulnerabilities database. It enhances CVE data with insights from the JFrog Security Research team to provide up-to-date, detailed vulnerability information.
2. **Validate Dependency Licenses**: Ensure the licenses of the project's dependencies are compliant with a predefined list of approved licenses, helping to manage legal risk.
3. **Static Application Security Testing (SAST)**: With fast and accurate engines, Frogbot identifies zero-day vulnerabilities in your source code's sensitive operations while minimizing false positives.
4. **CVE Vulnerability Contextual Analysis**: Frogbot uses the context of your code to avoid false positives related to vulnerable dependencies that are not applicable to your project. For vulnerabilities that do apply, Frogbot creates pull request comments on relevant lines of code, offering detailed descriptions of the security issues caused by the CVE. Supported for Python, JavaScript, and Java code.
5. **Secrets Detection**: Frogbot scans your code for exposed secrets, such as tokens or credentials, preventing accidental leaks of sensitive information.
6. **Infrastructure as Code (IaC) Scans**: Frogbot scans Terraform files for early detection of cloud and infrastructure misconfigurations, helping you avoid potential security risks in your infrastructure.
