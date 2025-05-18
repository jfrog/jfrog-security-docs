# Features and Capabilities

The Frogbot seamlessly integrates JFrog Xray and JFrog Advanced Security by automatically scanning source code stored in SCMs. Frogbot acts as a security gate, as it scans Pull Requests before the merge, decorating it with only the newly added security issues. It can be configured to block the merge until the issues are resolved or marked by the security administrator as ones that can be ignored.

In addition, Frogbot can automatically remediate CVEs by creating Pull Requests with Autofix for vulnerable packages.

### Key Security Capabilities

* Software Composition Analysis (SCA) with Contextual Analysis, including Autofix
* Secrets Detection and Token Validation
* Infrastructure as Code (IaC) Scanning
* Static Application Security Testing (SAST)
* Ability to fail the Pull Request job in case of security violations
* Presentation of the security results in [Xray Scans List](../../products/xray/features-and-capabilities/sca/understanding-and-analyzing-xray-scan-results/)

Integrating Frogbot into your development lifecycle allows you to proactively enforce security policies, thereby protecting your project from the outset. While Frogbot plays a critical role in maintaining security at the repository level, it is advisable for developers to also scan their code within their IDEs before committing changes. This complementary approach enables teams to identify and address vulnerabilities early, leading to a more robust security posture.
