# Supported Technologies

## **Supported Technologies for Contextual Analysis**

| **Repository Type** | **Supported Languages Inside Containers**                                         | **Supported Languages in Source Code Analysis** |
| ------------------- | --------------------------------------------------------------------------------- | ----------------------------------------------- |
| **Docker**          | Java, Go, Python, JavaScript, TypeScript, Rust (Cargo), .NET, C/C++ (ELF), Kotlin | Java, Go, Python, JavaScript, TypeScript        |
| **Maven**           | Java (Uber JAR)                                                                   | Java                                            |
| **Gradle**          | Java                                                                              | Java                                            |

**Notes:**

* **Maven support requires Xray 3.77.4+** (Uber JAR format).
* **Rust binaries require Xray 3.79.x+.**
* **.NET binaries require Xray 3.95.4+.**



***

## **Supported Services for Configuration Security Scanning**

| **Service**    | **Common Security Issues Detected**                              |
| -------------- | ---------------------------------------------------------------- |
| **NGINX**      | Insecure credentials, weak TLS settings, exposed admin interface |
| **Apache**     | Weak authentication, missing HTTPS enforcement                   |
| **Envoy**      | Misconfigured access policies, excessive privileges              |
| **Etcd**       | Unauthenticated access, weak crypto settings                     |
| **Prometheus** | Insecure endpoints, unauthorized access                          |

## **Supported Secret Scanning**

| **Supported Platforms for Secrets Detection**                                                 | **Types of Secrets Detected**                                     |
| --------------------------------------------------------------------------------------------- | ----------------------------------------------------------------- |
| JFrog Platform (Docker, Maven, npm, PyPI, NuGet, Gradle, RPM, Alpine, Go, RubyGems, Generic)  | API Keys, Tokens, Private Keys, High Entropy Secrets, URL Secrets |
| Developer Tools (IDE Plugins, CLI, Git Hooks)                                                 | API Keys, Passwords, Credentials in Source Code                   |
| Cloud Services (AWS, Azure, GCP, GitHub, GitLab, npm, Slack, Terraform, Stripe, Twilio, etc.) | API Keys, Authentication Tokens, OAuth Secrets                    |
