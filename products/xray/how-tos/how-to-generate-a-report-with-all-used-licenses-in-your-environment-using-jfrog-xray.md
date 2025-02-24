# How to Generate a Report with All Used Licenses in Your Environment Using JFrog Xray

This use case describes how to configure **Xray** to scan an environment and generate a **detailed license report**, helping teams ensure compliance, manage risks, and support legal audits.

***

### &#x20;**Involved**

* **Compliance Officer**: Reviews license usage to ensure legal and contractual adherence.
* **Security Engineer**: Configures Xray policies for license compliance monitoring.
* **DevOps Engineer**: Ensures CI/CD workflows respect license policies.

***

### **Trigger Event**

The organization requires an **up-to-date license report** covering all artifacts, dependencies, and distributed software to ensure compliance with internal and external policies.

***

### **Preconditions**

* JFrog Xray is **enabled** and scanning repositories and builds.
* Artifacts and dependencies **contain license metadata**.
* The organization has defined **license compliance policies**.

***

### **Flow of Events**

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

***

#### **Step 2: Attach the Policy to a Watch**

📌 **Goal:** Apply the policy to repositories, builds, and distributed software.

1. Navigate to **Xray** → **Security & Compliance** → **Watches**.
2. Click **"Create Watch"**.
3. Define the **Scope**:
   * **Repositories**: Select all repositories containing artifacts (e.g., `maven-central`, `npm-registry`).
   * **Builds**: Select all builds to track dependencies.
   * **Packages**: Apply to all components.
4. Attach the `License Compliance Policy`.
5. Save and activate the Watch.

***

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

***

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

***

### **Postconditions**

* A **detailed license report is generated** covering all artifacts and dependencies.
* The compliance team **reviews license usage** and ensures regulatory adherence.
* Builds using **non-compliant licenses are flagged or blocked** before deployment.

***

### **Alternative Flows & Considerations**

* **Scheduled Reports**: Set up **automated daily or weekly reports** for continuous monitoring.
* **Integration with Legal Tools**: Export reports to **compliance management platforms**.
* **Custom Severity Handling**:
  * Block builds for **GPL-3.0 but allow LGPL-2.1**.
  * Allow **non-standard licenses with legal approval**.

***

### **Business Impact**

🔹 **Ensures legal compliance** by identifying all software licenses in use.\
🔹 **Reduces legal risks** by preventing non-compliant software distribution.\
🔹 **Supports security audits** by providing a centralized license report.
