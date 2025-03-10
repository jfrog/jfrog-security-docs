# How to Identify and Mitigate Vulnerable OSS Packages in Your Repository

&#x20;**Use Case:** A security team wants to ensure that no vulnerable open-source software (OSS) is used in their development pipeline.

**Steps:**

1. **Search for Vulnerable Packages**
   * Navigate to the **JFrog Catalog Search**.
   * Enter a package name or version (e.g., `log4j`).
   * Filter by package type (e.g., Maven, npm, PyPI) to refine results.
   * Review the **Vulnerabilities tab** to see CVE details.
2. **Assess Security Risks**
   * Check whether the CVEs are **transitive (from dependencies)** or **non-transitive (direct vulnerabilities)**.
   * Click on a CVE to view **JFrog Security Research insights** on mitigation strategies.
3. **Find a Secure Alternative**
   * Use the **Package Compare feature** to evaluate **different versions** or **alternative packages**.
   * Check for a version with **no critical vulnerabilities**.
4. **Implement Remediation**
   * If an alternative version is available, update your build system to use the secure version.
   * If no secure alternative exists, apply security patches as suggested by JFrog Security.

