# How to Block Malicious or Vulnerable Packages from Entering the Repository

**Use Case:**

A security team wants to prevent developers from downloading packages containing known vulnerabilities (CVEs) or malicious components from public repositories.

**Workflow Steps:**

1. **Enable Curation on the Target Repository**
   * Navigate to **Administration > Curation > Curated Repositories**.
   * Select the repository where packages are downloaded (e.g., npm, Maven, PyPI).
   * Toggle the switch to **Enable Curation** for this repository.
2. **Create a Security-Based Curation Policy**
   * Go to **Administration > Curation > Policies Management** and click **Create Policy**.
   * Name the policy: e.g., **Block Malicious or  Vulnerable Packages**.
   * Under **Policy Scope**, select the repository or choose **All Curated** to apply it universally.
3. **Define a Security Condition**
   * In the **Policy Condition** step, choose one of the following conditions:
     * **Malicious Package**: Blocks packages flagged by JFrog Security as malicious.
     * **CVE with CVSS Score**: Blocks packages with known vulnerabilities above a certain CVSS threshold.
     * **Package Vulnerable to CVE**: Prevents usage of specific CVEs affecting dependencies.
   * Configure relaxation parameters (e.g., allow if no fixed version exists).
4. **Select an Action & Notifications**
   * Choose **Block** to prevent downloads.
   * Enable **Email notifications** to alert the package requester and security team when a package is blocked.
   * Click **Save Policy**.
5. **Test and Validate**
   * Attempt to download a package with a known CVE.
   * Confirm that the request is blocked and notifications are triggered.
   * Check audit logs under **Curation > Audit Events > Blocked/Approved Events**.
