# How to Generate a Report with All Used Licenses in Your Environment Using JFrog Xray

This use case describes how to configure **Xray** to scan an environment and generate a **detailed license report**, helping teams ensure compliance, manage risks, and support legal audits..



#### **Step 1: Define a License Policy in Xray**

📌 **Goal:** Ensure all artifacts and dependencies comply with legal and internal policies.

1. Navigate to **JFrog Platform** → **Xray**.
2. Go to **Security & Compliance** → **Policies**.
3. Click **"Create Policy"**, selecting **"License"** as the policy type.
4. Configure the policy:
   * **Name**: `License Compliance Policy`
   * **Description**: Identifies all software licenses used in the environment.
   * **Allowed Licenses**: Select approved licenses (e.g., MIT, Apache-2.0, BSD).
   * **Restricted Licenses**: Select licenses that violate company policy (e.g., GPL-3.0, AGPL-3.0).
   * **Actions**:
     * ✅ **Generate Report** (Creates a full license report).
     * ✅ **Fail Build** (Blocks CI/CD if non-compliant licenses are detected).
     * ✅ **Notify Compliance Team** (Email/Slack alerts for restricted licenses).
5. Click **Save**.

#### **Step 3: Generate a License Report**

📌 **Goal:** Run a scan and create a report listing all licenses used in the environment.

1. Navigate to **Xray** → **Reports**.
2. Click **"Generate Report"** → **"License Report"**.
3. Select **Scope**:
   * ✅ **Repositories**: Choose all relevant repositories.
   * ✅ **Builds**: Include all software builds.
   * ✅ **Packages**: Scan all dependency types.
4. Define **Filters**:
   * ✅ **Include all licenses** (Allowed, Restricted, Unknown).
   * ✅ **Export as CSV or JSON for external analysis**.
5. Click **"Generate"** to create the report.

#### **Step 4: Review and Analyze the Report**

📌 **Goal:** Examine license usage and identify any compliance risks.

**Example Report Output (CSV/JSON)**

| Package Name | Version | License         | Compliance Status | Risk Level |
| ------------ | ------- | --------------- | ----------------- | ---------- |
| log4j        | 2.14.1  | Apache-2.0      | ✅ Compliant       | Low        |
| express      | 4.17.1  | MIT             | ✅ Compliant       | Low        |
| openssl      | 1.0.1   | OpenSSL License | ⚠️ Restricted     | Medium     |
| my-library   | 1.2.3   | GPL-3.0         | ❌ Non-Compliant   | High       |

✅ **Compliance Actions Based on Report Findings:**

* **If Only Allowed Licenses Are Found**: Approve software for deployment.
* **If Restricted Licenses Exist**: Evaluate and obtain legal approval.
* **If Non-Compliant Licenses Exist**: Block deployment and seek alternatives.

***

#### **Step 5: Automate Report Generation in CI/CD**

📌 **Goal:** Ensure license reports are automatically generated in the build pipeline.

**Jenkins Pipeline Example (Xray API Call for License Report Generation)**

```sh
shCopyEditcurl -u user:password -X POST "https://artifactory.example.com/xray/api/v1/reports" \
  -H "Content-Type: application/json" \
  -d '{
        "name": "License Compliance Report",
        "resources": {
          "type": "repository",
          "names": ["maven-central", "npm-registry"]
        },
        "filters": {
          "licenses": ["ALL"]
        },
        "output": {
          "format": "csv",
          "destination": "artifactory://reports"
        }
      }'
```

✅ **Expected Outcome:**

* A **license compliance report is generated** for all scanned artifacts.
* The report is **stored in Artifactory** for review.
* If **non-compliant licenses** are found, the build **fails**, and the compliance team is notified.
