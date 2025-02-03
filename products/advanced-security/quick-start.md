# Quick Start

This guide provides a step-by-step approach to quickly setting up and enabling **JFrog Advanced Security** to scan artifacts for vulnerabilities and enforce security policies.

## **Prerequisites**

Before enabling **JFrog Advanced Security**, ensure the following requirements are met:

**JFrog Platform Installed** – You must have a **JFrog Artifactory and Xray** instance running (Enterprise X or Enterprise+ license with the **Advanced Security Add-on**).\
**Admin Permissions** – You need administrative access to configure **Xray settings** and security policies.\
**Repositories Indexed by Xray** – The repositories you want to scan must be indexed by Xray for analysis.

### **Enable Advanced Scans**

Advanced scans allow JAS to analyze artifacts for vulnerabilities, exposures, and contextual risks.

1. **Navigate to Administration**:
   * In **Classic Navigation**, go to **Administration Module** → **Xray Settings** → **General** → Click **Indexed Resources**.
   * In **New Navigation**, go to **Administration Module** → **Xray Settings** → Click **Indexed Resources**.
2. **Select the Repository or Build** you want to enable advanced scans for.
3. **Click "Configure"** and choose the scanning categories you want to enable:
   * **Vulnerability Contextual Analysis** (for reducing false positives)
   * **Exposures Scanning** (for detecting misconfigurations, weak authentication, etc.)
   * **Secrets Scanning** (for finding exposed credentials and API keys)
4. **Save the Configuration**.

## **Create a Security Policy with Advanced Scan Rules**

Security policies help define rules for detecting vulnerabilities and enforcing compliance.

**A. Creating an Exposures Policy**

1. **Navigate to Administration** → **Xray** → **Watches & Policies**.
2. **Go to the "Policies" tab** and click **New Policy**.
3. **Select "Security" as the policy type**.
4. **Click "New Rule"**, then:
   * Select **"Exposures"** as the rule type.
   * Define the **Minimal JFrog Severity** level (e.g., Critical, High, Medium).
   * Choose **Exposure Categories** to specify the risks you want to detect.
   * Configure **automatic actions** (e.g., fail a build, notify admins, block an artifact).
5. **Save the Policy**.

**B. Creating a Contextual Analysis Policy**

1. **Follow Steps 1-3 above**.
2. **Click "New Rule"**, then:
   * Select **"Contextual Analysis"** as the rule type.
   * Enable **"Skip Not Applicable CVEs"** (this prevents violations for non-exploitable vulnerabilities).
3. **Save the Policy**.

### **Next Steps**

* **Run an Advanced Scan on an Artifact**: Navigate to **Scans List** → Select an artifact → **Run Contextual Analysis or Exposure Scan**.
* **Monitor Security Violations**: Review violations under **Scans List** → **Policy Violations Tab**.
* **Integrate with CI/CD Pipelines**: Automate security scanning using **JFrog Advanced Security REST APIs**.
