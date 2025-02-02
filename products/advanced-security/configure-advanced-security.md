# Configure Advanced Security

## Enable Advanced Scans

Advanced Scans are configured per repository. The repository must be indexed by Xray. For more information, see **Indexing Resources**. Advanced Scans are applied only to newly scanned artifacts, not existing indexed artifacts. You can also run **Contextual Analysis** and **Exposures Scans** on an existing artifact.

To enable scanning categories, follow these steps:

1. **Classic Navigation:** Navigate to **Administration Module** > **Xray Settings** > **General**, then click **Indexed Resources**.
2. **New Navigation:** Navigate to **Administration Module** > **Xray Settings**, then click **Indexed Resources**.
3. Select the **repository or build** and click **Configure**.
4. Choose the **categories** you want to enable.

## Create a Security Policy with Advanced Scan Rules

Policies allow you to define security rules with corresponding automatic actions. Policies are enforced by applying them to **Xray Watches**. For more details on creating policies, see **Creating Xray Policies and Rules**.

We recommend creating policies to generate a **focused list of violations** based on your security criteria.

**Creating an Exposures Policy**

1. Navigate to **Administration Module** > **Xray** > **Watches & Policies**.
2. In the **Policies** tab, click **New Policy**.
3. Select the **policy rule type** as **Security**.
4. Click **New Rule**, then select **Exposures** from the **Type** drop-down menu.
5. Set the **Minimal JFrog Severity**, which is determined by the **JFrog Security Research Team** after a manual CVE analysis. A violation is issued only if the selected severity is met.
6. Select one or more **Exposure Categories** to specify when a violation should be issued.
7. Define **Automatic Actions** to determine the system’s response to policy violations. For further details, refer to **Creating Xray Policies and Rules**.

**Creating a Contextual Analysis Policy**

1. Navigate to **Administration Module** > **Xray** > **Watches & Policies**.
2. In the **Policies** tab, click **New Policy**.
3. Select the **policy rule type** as **Security**.
4. Check the **Skip Not Applicable CVEs** option. This ensures that the policy does not issue violations for CVEs found **not applicable** by the **Contextual Analysis Scanners**.
