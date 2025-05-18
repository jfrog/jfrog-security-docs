# Frogbot

**JFrog Frogbot** is a Git-based bot that helps you shift left by detecting and fixing security vulnerabilities early in the software development lifecycle (SDLC)—right in your pull requests. It leverages **Software Composition Analysis (SCA)**, **Static Application Security Testing (SAST)**, and **Infrastructure as Code (IaC)** scanning to catch risks before they reach production.

Frogbot automatically scans your Git repositories for security threats, helping you find and fix issues early. It performs comprehensive checks for:

* **SAST vulnerabilities**
* **SCA findings**
* **Secrets exposure**
* **CVE Contextual Analysis**

When new vulnerabilities are found in pull requests, Frogbot comments with detailed alerts and can even open pull requests with suggested fixes for SCA issues. This automates remediation and ensures your dependencies stay secure and compliant.

By integrating Frogbot into your development workflow, you can enforce security policies from the start. For added protection, developers are encouraged to run scans in their IDEs before committing code, strengthening security at every stage.

### Before You Begin

It is essential that you meet the [system requirements](../)
