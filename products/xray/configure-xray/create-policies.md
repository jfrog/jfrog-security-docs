# Create Policies

### **Step-by-Step Guide to Creating a Policy in Xray**

#### **Step 1: Access the Policy Configuration**

1. Log in to the **JFrog Platform**.
2. Navigate to **Xray → Policies**.
3. Click **New Policy**.

***

#### **Step 2: Define Policy Name and Type**

1. Enter a **Policy Name** (e.g., "Production Security Policy").
2. (Optional) Add a **Description** explaining the policy’s purpose.
3. Choose the **Policy Type**:
   * **Security Policy** – Detects **vulnerabilities** in artifacts.
   * **License Compliance Policy** – Enforces **open-source license rules**.
   * **Operational Risk Policy** – Flags outdated, deprecated, or unmaintained dependencies.

**Example:**\
✔ **Policy Name:** `Critical Security Policy`\
✔ **Policy Type:** `Security Policy`\
✔ **Description:** `Blocks all artifacts with critical CVEs and enforces compliance.`

***

### **Step 3: Add Rules to the Policy**

Each policy consists of **rules** that define the conditions and enforcement actions.

Click **Add Rule** to create a new rule.

#### **Security Policy Rules (For Vulnerability Detection)**

If you selected **Security Policy**, configure the rule as follows:

1. **Define the Severity Threshold**:
   * ✅ **Critical** (Highest risk)
   * ✅ **High**
   * ✅ **Medium**
   * ✅ **Low** (Least severe)
2. **Set the CVSS Score Range** (0-10) to filter vulnerabilities based on severity.
3. **Configure Exposures and Contextual Analysis  (Advanced Security Feature)**
   * Enable **Skip not applicable CVEs**to filter vulnerabilities **that do not impact your environment**.
   *   From **Type** drop-down, select **Exposures**.  Select one or more exposure categories. This specifies that a violation is issued only for the selected categories


4. **Define Enforcement Actions**:
   * **Block downloads** of artifacts with high-risk vulnerabilities.
   * **Fail builds** if vulnerabilities are detected.
   * **Trigger alerts** (Email, Slack, Jira).

&#x20;**Example Security Rule:**\
✔ Block downloads of artifacts with **Critical CVEs**.\
✔ Fail builds if vulnerabilities have a **CVSS score of 9 or higher**.\
✔ Send email **notifications** for newly discovered **High and Critical vulnerabilities**.

***

#### **License Compliance Policy Rules (For Open-Source License Enforcement)**

If you selected **License Compliance Policy**, configure the rule as follows:

1. **Select the License Rule Type**:
   * ✅ **Banned Licenses** – Prevents the use of specific licenses (e.g., GPL-3.0).
   * ✅ **Allowed Licenses** – Ensures artifacts only use **approved** licenses.
2. **Set License Enforcement Actions**:
   * **Block downloads** of artifacts with unapproved licenses.
   * **Fail CI/CD builds** if banned licenses are detected.
   * **Notify legal and compliance teams** about violations.

**Example License Compliance Rule:**\
✔ Block the use of **GPL-3.0 and AGPL** in production.\
✔ Allow only **MIT, Apache 2.0, and BSD** licenses.\
✔ Fail builds if a **banned license is detected**.

***

#### **Operational Risk Policy Rules (For Dependency Lifecycle Management)**

If you selected **Operational Risk Policy**, configure the rule as follows:

1. **Select the Risk Criteria**:
   * ✅ **End-of-Life Software** – Flags dependencies no longer maintained.
   * ✅ **Deprecated Components** – Detects libraries marked as obsolete.
   * ✅ **Unmaintained Open-Source Projects** – Flags packages with no updates in **over 12 months**.
   * ✅ **High-Impact Updates** – Identifies major version changes with breaking updates.
2. **Set Enforcement Actions**:
   * **Fail builds** if deprecated dependencies are used.
   * **Notify teams** about EOL or unmaintained software.
   * **Block downloads** of artifacts flagged for operational risks.

**Example Operational Risk Rule:**\
✔ Alert developers if a **dependency has not been updated in 12+ months**.\
✔ Fail builds if a **package is flagged as end-of-life**.\
✔ Block downloads of **deprecated components**.

***

### **Step 4: Save the Policy**

Once all rules are configured:

1. Click **Save & Apply**.
2. The policy will now be **available for use in Watches**.

***

### **Step 5: Attach the Policy to a Watch**

Policies are **enforced through Watches**, which monitor repositories, builds, and release bundles.

1. Apply on Scope
2. Select an existing Watch.

**Example:**\
✔ Attach the **"Critical Security Policy"** to a **production repository Watch**.\
✔ Attach the **"License Compliance Policy"** to a **release bundle Watch**.

***

### **Verifying Policy Enforcement**

To ensure that your policy is working:

* Go to **Xray → Violations** and check for new alerts.
* Test by **uploading a vulnerable artifact** to see if **violations are triggered**.
* Monitor if **builds fail** when security or compliance issues are detected.

***

### **Best Practices for Policy Configuration in Xray**

✔ **Use Separate Policies for Different Environments** – Apply stricter policies in **production** than in **development**.\
✔ **Customize Severity Thresholds** – Focus on **critical risks first** to avoid false positives.\
✔ **Enable Exposures and Contextual Analysis** – Prioritize vulnerabilities that **pose real-world threats**.\
✔ **Regularly Review and Update Policies** – Keep policies aligned with **new security threats and compliance requirements**.
