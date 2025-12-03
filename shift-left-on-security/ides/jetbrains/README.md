# JetBrains

The JFrog Plugin enables developers to identify and resolve security vulnerabilities in their projects. By continuously scanning locally with JFrog Security, developers gain insights into their code's security status.

## Key Security Capabilities

### **Basic Features**

* **Software Composition Analysis (SCA)**: Scans project dependencies for security issues and highlights vulnerable components. If a fix is available, you can upgrade to the secure version with a single click.
* **CVE Research and Enrichment**: Provides enhanced CVE data from the JFrog Security Research team, helping you prioritize vulnerabilities based on:
  * **JFrog Severity**: Custom severity rating based on real-world exploitability.
  * **Research Summary**: Detailed technical analysis explaining vulnerability conditions.
  * **Remediation**: Fixes and mitigation strategies recommended by JFrog experts.
* **Stay Informed**: Follow JFrog’s research team for updates on newly discovered security issues at [JFrog Security Research](https://research.jfrog.com/).

### **Advanced Features**&#x20;

_Requires Xray 3.66.5+ and Enterprise X / Enterprise+ with Advanced DevSecOps_

* **CVE Contextual Analysis**: Reduces false positives by assessing whether a vulnerability is applicable based on the code context. Supported for Python, Java, and JavaScript.
* **Secrets Detection**: Identifies exposed keys and credentials in source code to prevent accidental leaks.
* **Infrastructure as Code (IaC) Scan**: Secures Terraform files by detecting misconfigurations that could compromise cloud infrastructure.

### **Additional Benefits**

* Security issues are marked inline for easy identification.
* Contextualized security reports display issue severity, impact, and recommended fixes.
* Consolidated security insights available in the JFrog tab within JetBrains IDEs.
* Quick-fix functionality enables seamless dependency upgrades when fixes are available.
* Track build status, testing results, and security scans during CI/CD workflows.

#### **Supported JetBrains IDEs**

The JFrog Plugin is compatible with the following JetBrains IDEs:

* **IntelliJ IDEA**
* **WebStorm**
* **PyCharm**
* **Android Studio**
* **GoLand**
* **Rider**
* **CLion**
