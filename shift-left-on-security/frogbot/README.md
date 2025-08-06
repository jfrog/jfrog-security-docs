# Frogbot

**JFrog Frogbot** is a Git-based bot that helps you shift left on security by detecting and fixing security vulnerabilities early in your SDLC (Software Development Lifecycle)—right in your pull requests and commits. It leverages **Software Composition Analysis (SCA)**, **Static Application Security Testing (SAST)**, and **Infrastructure as Code (IaC)** scanning to catch risks before they reach production.

Frogbot automatically scans your Git repositories for security threats, helping you find and fix issues early.&#x20;

It performs comprehensive checks for:

* **SAST vulnerabilities**
* **SCA findings**
* **Secrets exposure**
* **CVE Contextual Analysis**

When new vulnerabilities are found in pull requests, Frogbot comments with detailed alerts. In addition, Frogbot can automatically open pull requests with suggested fixes for vulnerable dependencies (autofix), helping you remediate issues with minimal manual effort.

{% hint style="info" %}
**Note:** Autofix pull requests are only created during full repository scans—not during pull request scans.
{% endhint %}

By integrating Frogbot into your development workflow, you can enforce security policies from the start.

### Before You Begin

It is essential that you meet the [system requirements](../)
