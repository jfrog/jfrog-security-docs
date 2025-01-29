# Create Watches

**This is a Step-by-Step Guide to Creating a Watch in Xray. To learn more about Watches, click** [**here**](../features-and-capabilities/sdlc-policy-mangement/watches.md)**.**&#x20;

#### **Step 1: Access the Watch Configuration**

1. Log in to your **JFrog Platform**.
2. Navigate to **Xray → Watches**.
3. Click **Create New Watch**.

***

#### **Step 2: Define Watch Name and Description**

1. In the **New Watch** window, enter a **unique name** for the Watch (e.g., "Critical Security Watch").
2. (Optional) Add a **description** to specify the Watch’s purpose.

&#x20;**Example:**\
✔ **Watch Name:** `Production Security Watch`\
✔ **Description:** `Monitors all production repositories for critical security vulnerabilities and license violations.`

***

#### **Step 3: Select Resources to Monitor**

A Watch applies to specific **repositories, builds, or release bundles**.

1. Click **Add Resources**.
2. Select one or more of the following:
   * **Repositories** – Monitors artifacts in Artifactory repositories.
   * **Builds** – Monitors CI/CD-generated builds.
   * **Release Bundles** – Ensures software is secure before deployment.
3. Click **Apply**.

&#x20;**Example:**\
✔ Add a **Docker repository** to monitor container images.\
✔ Add a **Jenkins build pipeline** to track vulnerabilities before deployment.

***

#### **Step 4: Attach Policies to the Watch**

A Watch must be linked to **one or more policies** that define security and compliance rules.

1. Click **Add Policy**.
2. Select the policies that should apply to this Watch:
   * **Security Policy** – Detects vulnerabilities in dependencies.
   * **License Compliance Policy** – Ensures all components comply with licensing rules.
   * **Operational Risk Policy** – Identifies deprecated or unmaintained dependencies.
3. Click **Apply**.

&#x20;**Example:**\
✔ Attach a **Security Policy** that **blocks downloads of artifacts with critical vulnerabilities**.\
✔ Attach a **License Policy** that **bans GPL-licensed components** from production.

***

#### **Step 5: Configure Actions for Violations**

Define **what happens when a violation is detected** in the Watch.

1. Set up **notification alerts**:
   * **Email alerts**
   * **Slack notifications**
   * **Jira issue creation**
2. Configure **automatic enforcement actions**:
   * **Block artifact downloads**
   * **Fail CI/CD builds**
   * **Generate security reports**

**Example:**\
✔ **Fail Jenkins builds** if they contain high-risk vulnerabilities.\
✔ **Send Slack alerts** to the security team when a new violation is detected.

***

#### **Step 6: Save and Activate the Watch**

1. Review the Watch configuration.
2. Click **Save & Activate**.
3. Xray will now start **monitoring the selected resources** and enforce the attached policies.

***

### **Verifying Watch Performance**

To check if your Watch is working correctly:

* Navigate to **Xray → Watches → \[Your Watch]**.
* Review detected violations and triggered alerts.
* Modify policies or resources if needed.

***

### **Best Practices for Watches in Xray**

✔ **Use Separate Watches for Different Environments** – Apply different policies for **development, staging, and production**.\
✔ **Limit Watches to Critical Resources** – Avoid excessive monitoring on **temporary or non-production** repositories.\
✔ **Integrate with CI/CD Pipelines** – Automatically **fail builds that violate security policies**.\
✔ **Regularly Review and Update Watches** – Keep Watch configurations **aligned with evolving security and compliance needs**.
