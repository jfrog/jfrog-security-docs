# Contextual Analysis Policy

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
