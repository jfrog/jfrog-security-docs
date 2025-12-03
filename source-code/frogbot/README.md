# Frogbot

JFrog Frogbot is a Git-based bot that helps you shift left on security by detecting and fixing security vulnerabilities early in your SDLC (Software Development Lifecycle)—right in your pull requests and commits. It leverages Software Composition Analysis (SCA), Static Application Security Testing (SAST), and Infrastructure as Code (IaC) scanning to catch risks before they reach production.

Frogbot automatically scans your Git repositories for security threats, helping you find and fix issues early.&#x20;

It performs comprehensive checks for:

* **SAST vulnerabilities**
* **SCA findings**
* **Secrets exposure**
* **CVE Contextual Analysis**

When new vulnerabilities are found in pull requests, Frogbot comments with detailed alerts, helping you understand which issues were introduced by the change. Frogbot can also run a full repository scan to detect all existing vulnerabilities in the latest commit of the branch, and when fixable issues are found, it can automatically open an autofix pull request that aggregates all relevant dependency upgrades. In addition, Frogbot performs a pull request scan that compares the state of the project before and after the proposed change, showing only the _new_ issues introduced by the pull request. This distinction ensures that the pull request decoration highlights what changed, while the full repository scan and autofix PR focus on remediating broader issues already present in the codebase.

In addition to scan behavior in pull requests, Frogbot supports [centrally configuring](../git-repository-scans-and-results/git-repository-configuration.md) which Git repositories and folders are scanned, including which scanners are applied. This configuration reflects your SCM hierarchy and allows settings to be inherited for future repositories and structures.

By integrating Frogbot into your development workflow, you can enforce security policies from the start.

### Before You Begin

* It is essential that you meet the [system requirements](/broken/pages/98lIXYCabSW7C3cDKznj)
* Frogbot does not require any special permissions&#x20;
