# Create a Git Repository Policy

This is a step-by-step guide to creating a Git Repository Policy in Xray. To learn more about Policies, click [here](https://jfrog.com/help/r/_SD6R0PIfl9UZ1cNTXRYqw/WI2fDnZnwCEv49GKXl40Pg).

{% hint style="info" %}
For self-hosted, available from version 3.111 and above.
{% endhint %}

1. Navigate to **Xray → Watches & Policies**.
2. Click **New Policy**.
3. Enter a **Policy Name** (e.g., "Production Security Policy").
4. (Optional) Add a **Description** explaining the policy’s purpose.
5. Choose the **Policy Type**:
   * **Security Policy** – Detects vulnerabilities in Git repositories.
   * **Licences Policy**
6. Under the Policy Rules List tab, click on **Create New Rule**.\
   The **Create New Policy Rule** window opens.
7. Enter a **Rule Name**.
8. From the **Rule type** dropdown, select:

* **SAST**
* **CVEs**
* **Exposures (Secrets only)**

9. From the **Select minimal severity** dropdown, select the severity level to trigger the rule.
10. Click **Save Rule** to create a new rule.
11. To attach the Policy to a Watch (that is already assigned to a Git Repository), select the **Apply on Scope** tab. \
    Policies are **enforced through Watches**, which monitor Git repositories.
12. Select an existing Watch.
13. Click **Save & Apply**.
