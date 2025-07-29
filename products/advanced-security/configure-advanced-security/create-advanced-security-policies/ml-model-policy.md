# ML Model Policy

Create a security policy for ML Model package types by defining rules based on package versions. Use this to enforce security standards, detect risks in ML models, and automate responses such as blocking usage or triggering alerts when unapproved model versions are detected.

1. Navigate to **Application** > **Xray** > **Watches & Policies**.
2. In the **Policies** tab, click **New Policy**.
3. Enter a **Policy Name**.
4. (Optional) Add a **Description** explaining the policy's purpose.
5. Under **Select Policy Type**, select **Security,** and hit **Next.** \
   The **Create New Policy Rule** window opens.
6. Enter a **Rule Name**.
7. Under **Rule Type**, select **Package Version**.
8. From the **Select package type** menu, select **ML Model**.
9. Add a package name and select a version.
10. Under **Then**, define the policy actions, select **Save Rule**, and hit **Next**.
11. Under **Apply on Scope**, select one or more policy watches and hit **Save Policy**.
