# Repository/Artifact On-Demand Advanced Scan

Repositories can be configured to automatically scan for **JFrog Advanced Security (JAS)**, as outlined in the **Set Up JFrog Advanced Security** section. Additionally, administrators can run **Contextual Analysis** and **Exposure Scans** on-demand for specific repositories and artifacts.

* **From Xray version 3.66.x and above**, you can run **Contextual Analysis** or **Exposure Scans** on existing artifacts.
* **From Xray version 3.73.x and above**, you can run **Contextual Analysis** and **Exposure Scans** per repository as needed.

This flexibility ensures that both newly added and existing artifacts are continuously evaluated for security risks.

#### **Advanced Scans on an Existing Artifact**

1. Navigate to **Scans List** > **Repositories** tab.
2. Select the repository containing the artifact you want to scan.
3. Locate the artifact, click the **Actions Menu**, and choose either:
   * **Run Contextual Analysis** – to analyze vulnerabilities within the artifact’s context.
   * **Scan for Exposures** – to detect potential security misconfigurations or leaks.

#### **Advanced Scans per Repository**

1. Navigate to **Scans List** > **Repositories** tab.
2. Locate the repository you want to scan.
3. Click the **Actions Menu** and select **Advanced Scan**.
4. In the **Advanced Scan** dialog box, define the scan criteria:
   * **Deployed in** – Scan artifacts deployed to Artifactory within a specified time range.
   * **Downloaded in** – Scan artifacts that were downloaded from Artifactory within a specified time range.
   * **Any time** – Scan all artifacts currently present in the repository.
   * **Pattern** – Specify a repository path (required alongside a date range).
   * **Categories** – Select the **JFrog Advanced Security (JAS)** categories to include in the scan.
5. Click **Next** and follow the **Wizard** instructions to complete the scan setup.

