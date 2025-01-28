# How to Ensure Only Open-Source Packages with Approved Licenses Are Used

**Use Case:**

A legal and compliance team wants to restrict developers from using open-source software with non-compliant licenses (e.g., GPL, AGPL) while allowing permissive licenses (MIT, Apache 2.0).

**Workflow Steps:**

1. **Enable Curation for Open-Source Package Repositories**
   * Navigate to **Curation > Curated Repositories**.
   * Enable curation for repositories containing open-source packages (e.g., npm, Maven, PyPI).
2. **Create a License Compliance Policy**
   * Go to **Curation > Policies Management** and create a new policy: **Restrict Non-Compliant Licenses**.
   * Under **Policy Scope**, apply the policy to all open-source repositories.
3. **Define a License-Based Condition**
   * In the **Policy Condition** step, select:
     * **Block List by License**: Specify prohibited licenses (e.g., GPL, AGPL, SSPL).
     * **Allow List by License**: Specify approved licenses (e.g., MIT, Apache 2.0, BSD).
4. **Select an Action & Notifications**
   * Choose **Block** to prevent package downloads.
   * Enable **Email notifications** for legal and compliance teams.
5. **Test Compliance**
   * Try downloading a package with a prohibited license.
   * Confirm the request is blocked and an alert is sent.
   * View blocked package details under **Audit Logs**.
