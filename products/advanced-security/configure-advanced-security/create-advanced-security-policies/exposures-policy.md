# Exposures Policy

1. Navigate to **Application** > **Xray** > **Watches & Policies**.
2. In the **Policies** tab, click **New Policy**.
3. Enter a **Policy Name**.
4. (Optional) Add a **Description** explaining the policy's purpose.
5. Under **Select Policy Type**, select **Security,** and hit **Next.**\
   The **Create New Policy Rule** window opens.
6. Enter a **Rule Name**.
7. Under **Rule Type**, select **Exposures**.
8. Under **Select at least one category**, select one or more exposure categories to be detected by the policy:

* **Secrets** - Detects exposed credentials, tokens, and other sensitive data across source and binary scans. Supports ignoring specific findings to manage known safe secrets and minimize false positives.
* **Services** - Identifies configuration issues or weak settings in common services and frameworks.
* **Applications** - Detects misconfigurations and insecure library use within application logic.
* **IaC** - Scans Infrastructure-as-Code files (Terraform) to identify security misconfigurations before deployment.

9. From the **Select minimal severity** menu, select the severity level to trigger the policy violation.
10. Under **Then**, define the policy actions, select **Save Rule**, and hit **Next**.
11. Under **Apply on Scope**, select one or more policy watches and hit **Save Policy**.&#x20;
