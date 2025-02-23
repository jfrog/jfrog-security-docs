# Enhance Xray Policies with Advanced Security

Security policies define rules based on security criteria, triggering automatic actions when the conditions are met. These policies are enforced when applied to [Xray Watches](../../xray/features-and-capabilities/sdlc-policy-mangement/watches.md). To ensure effective security management, it is recommended to create policies that focus on specific types of violations based on your security requirements.&#x20;

Advanced Security allows you to enhance existing and newly created [Xray policies](../../xray/features-and-capabilities/sdlc-policy-mangement/) with **Exposures** detection and **contextual analysis** rules.

Violations can be viewed in:

* The **Scans List**
* The **Watch Violations** page

## Creating a Contextual Analysis Policy

1. Navigate to **Application** > **Xray** > **Watches & Policies**.
2. In the **Policies** tab, click **New Policy**.
3. Enter a **Policy Name**.
4. (Optional) Add a **Description** explaining the policy's purpose.
5. Under **Select Policy Type**, select **Security,** and hit **Next.**\
   The **Create New Policy Rule** window opens.
6. Enter a **Rule Name**.
7. Under **Rule Type**, select **CVEs**.
8. Define **Rule category** and **Add CVE IDs**.
9. Check the **Skip Not Applicable CVEs** option. \
   This ensures that the policy does not issue violations for CVEs found **not applicable** by the Contextual Analysis Scanners, and thus will not impact your environment.
10. Under **Then**, define the policy actions, select **Save Rule**, and hit **Next**.
11. Under **Apply on Scope**, select one or more policy watches and hit **Save Policy**.&#x20;

## Creating an Exposures Policy

1. Navigate to **Application** > **Xray** > **Watches & Policies**.
2. In the **Policies** tab, click **New Policy**.
3. Enter a **Policy Name**.
4. (Optional) Add a **Description** explaining the policy's purpose.
5. Under **Select Policy Type**, select **Security,** and hit **Next.**\
   The **Create New Policy Rule** window opens.
6. Enter a **Rule Name**.
7. Under **Rule Type**, select **Exposures**.
8. Under **Select at least one category**, select one or more exposure categories to be detected by the policy:

* Secrets
* Services
* Applications
* IaC

9. From the **Select minimal severity** menu, select the severity level to trigger the policy violation.
10. Under **Then**, define the policy actions, select **Save Rule**, and hit **Next**.
11. Under **Apply on Scope**, select one or more policy watches and hit **Save Policy**.&#x20;
