# How to Generate a Report with All Vulnerabilities in a Distributed Bundle

This use case outlines how to configure **Xray** to scan a **distributed bundle** and generate a detailed **vulnerability report** for compliance, risk assessment, and security auditing.



#### **Step 1: Define a Security Policy for Distributed Bundles**

📌 **Goal:** Ensure Xray scans distributed bundles for vulnerabilities.

1. Navigate to **JFrog Platform** → **Xray**.
2. Go to **Security & Compliance** → **Policies**.
3. Click **"Create Policy"**, selecting **"Security"** as the policy type.
4. Configure the policy:
   * **Name**: `Distributed Bundle Vulnerability Policy`
   * **Description**: Scans all distributed bundles for vulnerabilities.
   * **Severity Levels**: Select **Critical, High, Medium, Low** (based on security standards).
   * **Actions**:
     * ✅ **Generate Report** (Creates a vulnerability report).
     * ✅ **Notify Security Team** (Email/Slack alerts if issues are found).
     * ✅ **Fail Deployment** (Optional: Blocks distribution if critical vulnerabilities exist).
5. Click **Save**.

#### **Step 2: Generate a Vulnerability Report for a Distributed Bundle**

📌 **Goal:** Run a security scan and generate a vulnerability report.

1. Navigate to **Xray** → **Reports**.
2. Click **"Generate Report"** → **"Security Report"**.
3. Select **Scope**:
   * **Choose "Distributed Bundle"** as the target.
   * **Select the specific bundle version** (e.g., `my-app-bundle:1.0.0`).
4. Define **Filters**:
   * ✅ **Include all severities (Critical, High, Medium, Low)**.
   * ✅ **Include dependency vulnerabilities** (transitive dependencies).
   * ✅ **Export as CSV or JSON for further analysis**.
5. Click **"Generate"** to create the report.

***

#### **Step 3: Review and Analyze the Report**

📌 **Goal:** Examine vulnerabilities and plan remediation before distribution.

**Example Report Output (CSV/JSON)**

| Package Name | Version | CVE ID         | Severity | Description                         | Fix Available |
| ------------ | ------- | -------------- | -------- | ----------------------------------- | ------------- |
| log4j        | 2.14.1  | CVE-2021-44228 | Critical | Remote code execution vulnerability | Yes (2.17.1)  |
| openssl      | 1.0.1   | CVE-2023-12345 | High     | TLS handshake vulnerability         | Yes (1.1.1)   |
| my-library   | 1.2.3   | CVE-2022-56789 | Medium   | Memory leak issue                   | No            |

✅ **Security Actions Based on Report Findings:**

* **If Critical Vulnerabilities Exist**: Block deployment and request fixes.
* **If High/Medium Vulnerabilities Exist**: Evaluate risk and decide on patches.
* **If No Issues Are Found**: Approve distribution of the bundle.

***

#### **Step 4: Automate Report Generation in CI/CD**

📌 **Goal:** Ensure security reports are automatically generated during build pipelines.

**Jenkins Pipeline Example (Xray Report Generation API Call)**

```sh
shCopyEditcurl -u user:password -X POST "https://artifactory.example.com/xray/api/v1/reports" \
  -H "Content-Type: application/json" \
  -d '{
        "name": "Distributed Bundle Security Report",
        "resources": {
          "type": "release_bundle",
          "names": ["my-app-bundle:1.0.0"]
        },
        "filters": {
          "severities": ["Critical", "High", "Medium", "Low"]
        },
        "output": {
          "format": "csv",
          "destination": "artifactory://reports"
        }
      }'
```

✅ **Expected Outcome:**

* A **vulnerability report is generated** for the distributed bundle.
* The report is **stored in Artifactory** for review.
* If vulnerabilities are found, **CI/CD fails** and notifies the security team.
