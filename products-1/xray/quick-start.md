# Quick Start

### **Prerequisites**

To quickly get started with JFrog Xray, ensure you have the following:\
✅ **Xray Installed**\
✅ **"Manage Xray Data" Permission**

***

### **1️⃣ Add Resources to Xray for Automatic Scanning**

Once Xray is set up, you need to add resources for continuous scanning.

#### **Steps:**

1. Navigate to the **Scans List** page in Xray.
2. Click the **"Add/Remove to Xray"** button.
3. Select the **resource type** you want to scan (e.g., repository, build, release bundle).

✅ **Done!** From now on, every new artifact added to the selected resource will be **automatically scanned** by Xray.

***

### **🔹 Alternative: Scan Existing Artifacts in JFrog Artifactory**

If you want to scan an artifact that is **already stored in Artifactory**, follow these steps:

1. Navigate to the **selected artifact** in **Artifactory**.
2. Click on the **Xray Tab**.
3. Press **"Scan Now"** to manually trigger a scan.

✅ **Done!** The artifact is now scanned, and any security issues will be displayed.

***

### **2️⃣ View Artifact Vulnerabilities**

After scanning, you can view detected security issues for your artifacts.

#### **Steps:**

1. Navigate to the **Scans List Page**.
2. Click on the **scanned artifact** you want to inspect.
3. Go to the **"Security Issues"** section.
4. Click the **"Vulnerabilities"** tab to view detailed security findings.

✅ **Done!** You can now see all vulnerabilities affecting your artifact.

***

### **3️⃣ Export Scan Findings to an SBOM File (Including VEX Data)**

Once your artifact is scanned, you may want to **generate an SBOM report** containing the **entire scan results**, including **VEX (Vulnerability Exploitability Exchange)** information. This allows you to **share security insights outside the JFrog Platform**.

#### **Steps to Export an SBOM Report:**

1. On the **"Scan Results"** page, click the **\[…] (More Options) button**.
2. Select **"Export Scan Data"**.
3. Choose the **"CycloneDX"** format.
4. Toggle the **"Vulnerabilities (VEX)"** option to **include vulnerability data** in the report.
5. Click **"Export"**.

✅ **Done!** The SBOM report (including VEX data) is now downloaded to your computer.

***

### **Summary: Xray Quick Start**

✔ **Enable automatic scanning for new artifacts**\
✔ **Manually scan existing artifacts in Artifactory**\
✔ **View detected vulnerabilities for artifacts**\
✔ **Export scan results as an SBOM report with VEX**

&#x20;**Now you’re ready to secure your software supply chain with JFrog Xray!**









