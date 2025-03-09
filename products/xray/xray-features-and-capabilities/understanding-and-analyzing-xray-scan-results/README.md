# Understanding and Analyzing Xray Scan Results

### **Overview**

Xray scans your **artifacts, builds, and Release Bundles** for **vulnerabilities, license compliance issues, and operational risks**. Once a scan is completed, Xray provides a **detailed report** with identified issues, their severity, affected components, and possible remediation steps.

This guide will help you **navigate, interpret, and act upon scan results** effectively.

***

### **Where to Find Xray Scan Results?**

Xray scan results can be accessed in **multiple locations** depending on the scope of the scan:

#### &#x20;**Viewing Scan Results**

* Navigate to **Application -> Xray -> Scan List**.
* Select the **resource (Git Repositories, Repositories, Builds, Release Bundles, Packages)**&#x20;
* Click on the specific resource and select the particular version you want to analyze.

***

### **Understanding Xray Scan Results**

#### **1. Overview of the Scan Summary**

The **Xray Scan Dashboard** provides a high-level summary of issues found in the scanned entity. It includes:\
**General Artifact Data** (Last scan date, downloads, etc.)\
**Total Number of Vulnerabilities** **by Severity** (Critical, High, Medium, Low).\
**Total Number of Policy Violations** **by Severity** (Critical, High, Medium, Low).\
**Type of Policy Violations** (Security, License, or Operational).\
**SBOM Details** (Most common package types, most common licenses, etc.)

***

#### **2. Policy Violations Tab**

This tab displays all detected **violations** affecting your scanned resource.

**Examples of Recommended Actions:**

* If a **fix is available for a security violation**, upgrade the component to the suggested fix version.
* If a **violation is failing your build** and you need a grace period, request an ignore rule with an expiration date from the security team.&#x20;
* If it’s a **false positive**, request an ignore rule from the security team.

***

#### **3. SBOM Tab**

This tab provides a list of **components and licenses** associated with the scanned resource. Identifies the component list, their versions, their licenses, and operational risk data.&#x20;

**Examples of** **Recommended Actions:**

* Identify a risky component in your resource.&#x20;
* **For restricted licenses**: Obtain legal approval or find an alternative package.
* **For missing licenses**: Ensure the package includes a valid license declaration.
* Identify which component is end-of-life and other operational risk information.&#x20;

***

#### **4. Security Issues Tab ( Vulnerabilities and Malicious Packages)**

The Vulnerabilities section displays detected vulnerabilities that affect the scanned resource including additional information on each vulnerability.&#x20;

**Examples of** **Recommended Actions:**

* If a **fix is available for a vulnerability**, upgrade the component to the suggested fix version.
* Use the enriched data provided by the **JFrog Research Team** to understand the exploitability of the vulnerability.&#x20;
* Understand which component version is vulnerable and what is the exact vulnerable path.&#x20;

#### &#x20;**Impact Analysis**&#x20;

The **Impact Analysis** section shows how detected vulnerabilities **affect other components in the software environment**.

**Key Insights:**

* Which **artifacts and builds** are impacted?
* Which **projects or microservices** use the vulnerable component?
* Which **environments** (Dev, Staging, Production) are at risk?

✅ **Recommended Actions:**

* If the issue impacts **multiple projects**, coordinate a cross-team fix.
* Prioritize fixes based on **production vs. development** environments.
* Use **SBOM (Software Bill of Materials)** to track vulnerable dependencies.

***

### **Filtering and Sorting Scan Results for Better Analysis**

Xray provides **filters** to help narrow down scan results for better prioritization.

#### **1. Filter by Severity**

* **Critical & High**: Prioritize immediate remediation.
* **Medium & Low**: Monitor but don’t necessarily block deployment.

#### **2. Filter by Component Name**

Search for vulnerabilities affecting a specific package (e.g., `log4j`).

#### **3. Filter by Policy Violations**

* Show only vulnerabilities that **violate predefined security policies**.

***

### **Taking Action on Scan Results**

#### **1. Fixing Vulnerabilities**

* **Upgrade** vulnerable dependencies if a fix is available.
* **Apply security patches** if upgrading is not feasible.
* **Request an exception** for false positives or justified risks.

#### **2. Handling License Issues**

* Replace **restricted licenses** with compliant alternatives.
* Obtain **legal approvals** for specific cases.

#### **3. Exporting and Sharing Reports**

* Click **"Export Report"** → Select format **CSV, JSON, or PDF**.
* Share with **security, DevOps, and compliance teams** for risk assessment.

***

### **Automating Scan Analysis in CI/CD Pipelines**

📌 **Goal:** Automatically fail builds with critical security issues.

#### **1. Configure Xray Scans in Jenkins**

Modify Jenkinsfile to trigger Xray scans:

```sh
shCopyEditjfrog rt build-scan my-app-build 42
```

✅ **Expected Outcome:**

* **Build fails** if Critical vulnerabilities are detected.
* **Scan report is logged** in the CI/CD pipeline output.

#### **2. Sending Security Alerts for Critical Issues**

Configure real-time notifications for security teams:

```sh
shCopyEditcurl -X POST "https://artifactory.example.com/api/xray/notifications" \
     -H "Content-Type: application/json" \
     -d '{
           "watch_name": "Critical Vulnerabilities",
           "notify": "security-team@example.com"
         }'
```

✅ **Expected Outcome:**

* **Email and Slack alerts** sent for critical vulnerabilities.
* **Security team can act immediately** to mitigate risks.

***

### **Postconditions**

* Security and license violations **are reviewed and mitigated**.
* CI/CD pipelines **enforce security policies automatically**.
* Compliance teams **receive reports for audits and legal review**.

***

### **Alternative Flows & Considerations**

* **Historical Scan Data**: View previous scans to identify trends.
* **Custom Policy Rules**: Adjust Xray policies based on business needs.
* **SBOM Tracking**: Maintain a Software Bill of Materials (SBOM) for transparency.

***

### **Business Impact**

🔹 **Prevents security vulnerabilities from reaching production**.\
🔹 **Ensures legal compliance with licensing policies**.\
🔹 **Reduces risk exposure by proactively fixing issues**.

