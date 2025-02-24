# How to View and Analyze Scan Results

This use case outlines how to **access, interpret, and act on Xray scan results**, helping teams resolve issues efficiently.

***

### &#x20;**Involved**

* **Security Engineer**: Reviews scan results and ensures security policies are met.
* **DevOps Engineer**: Ensures CI/CD pipelines integrate with Xray scan reports.
* **Developers**: Take corrective action on detected vulnerabilities and license issues.

***

### **Trigger Event**

A **security scan is completed** in JFrog Xray, and the team needs to **view and analyze** the results for security and compliance evaluation.

***

### **Preconditions**

* JFrog Xray is **enabled** and scanning repositories, builds, or artifacts.
* Security policies for **vulnerabilities and license compliance** are defined.
* The team has appropriate **permissions** to access Xray scan reports.

***

### **Flow of Events**

#### **Step 1: Access Xray Scan Results**

📌 **Goal:** Navigate to Xray and locate scan results for artifacts, builds, or repositories.

1. Log in to the **JFrog Platform**.
2. Go to **Xray** → **Security & Compliance**.
3. Choose where to view scan results:
   * **For a Specific Artifact**:
     * Navigate to **Artifactory** → Select an artifact → Click **Xray Data** tab.
   * **For a Build Scan**:
     * Go to **Builds** → Select a build → Click **Xray Violations** tab.
   * **For a Repository Scan**:
     * Go to **Xray** → **Scans** → **Repositories** → Select a repository.

***

#### **Step 2: Analyze Scan Results**

📌 **Goal:** Interpret scan results and determine next actions.

**2.1 Understanding the Scan Results Dashboard**

Once in the **Xray Scan Report**, review:

* **Violations Summary**: Displays detected vulnerabilities and their severity.
* **License Compliance Issues**: Shows any non-compliant licenses.
* **Security Violations Tab**:
  * **CVE ID** (e.g., `CVE-2023-XXXXX`)
  * **Severity** (Critical, High, Medium, Low)
  * **Impacted Components** (e.g., `log4j-2.14.1.jar`)
  * **Fix Available** (Upgrade recommendation)

**2.2 Filtering Results for Better Insights**

Use **filters** to refine results:

* **Severity Level**: Focus on Critical/High issues first.
* **Component Name**: Search for a specific package (e.g., `openssl`).
* **Policy Violations**: View only security violations flagged by policies.

***

#### **Step 3: Take Action on Scan Results**

📌 **Goal:** Mitigate vulnerabilities and ensure compliance.

**3.1 Handling Vulnerabilities**

1. Click on a **CVE** to view detailed information.
2. Check if an **upgrade is available** (e.g., `log4j-2.14.1 → log4j-2.17.1`).
3. If the vulnerability is false-positive or low-impact, request **an exception**.
4. Communicate with the development team to **fix dependencies** before the next build.

**3.2 Addressing License Compliance Issues**

1. Identify **restricted or unknown licenses** in the scan results.
2. If using a **restricted license**, consult with the legal/compliance team.
3. Find an **alternative open-source library** with a permissible license.

**3.3 Exporting Reports for Documentation**

1. Click **"Export Report"** → Choose **CSV, JSON, or PDF**.
2. Share the report with **security, DevOps, or compliance teams**.

***

#### **Step 4: Automate Analysis in CI/CD Pipelines**

📌 **Goal:** Integrate Xray scanning into CI/CD workflows for automated security analysis.

**4.1 Running Xray Scans in Jenkins**

Add an Xray scan step in the Jenkins pipeline:

```sh
shCopyEditjfrog rt build-scan my-app-build 42
```

✅ **Expected Result:**

* If vulnerabilities exist, the build **fails** and **Xray violations** are displayed.
* If no issues are found, the build **continues successfully**.

**4.2 Automating Notifications for Violations**

Configure alerts for security violations:

```sh
shCopyEditcurl -X POST "https://artifactory.example.com/api/xray/notifications" \
     -H "Content-Type: application/json" \
     -d '{
           "watch_name": "Critical Vulnerabilities",
           "notify": "security-team@example.com"
         }'
```

✅ **Expected Outcome:**

* The security team receives **real-time alerts** when critical issues are detected.

***

### **Postconditions**

* **Xray scan results are reviewed**, and actionable insights are obtained.
* Vulnerabilities and license issues are **mitigated before deployment**.
* Security and compliance teams **receive reports for auditing**.

***

### **Alternative Flows & Considerations**

* **Viewing Scan History**: Access previous scans to track security trends over time.
* **Custom Policy Rules**: Modify Xray security policies based on business needs.
* **SBOM Analysis**: Use **Software Bill of Materials (SBOM)** to track dependencies.

***

### **Business Impact**

🔹 **Enhances security visibility** across software artifacts and dependencies.\
🔹 **Reduces production risks** by proactively fixing vulnerabilities.\
🔹 **Ensures regulatory compliance** with licensing policies.
