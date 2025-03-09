# Create Watches

**This is a Step-by-Step Guide to Creating a Watch in Xray. To learn more about Watches, click** [**here**](../xray-features-and-capabilities/sdlc-policy-mangement/watches.md)**.**&#x20;

#### **Step 1: Access the Watch Configuration**

1. Log in to your **JFrog Platform**.
2. Navigate to **Xray → Watches & Policies**.
3. Click **New Watch**.

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
   * **Repositories** &#x20;
   * **Builds**&#x20;
   * **Release Bundles**&#x20;
   * **Projects**&#x20;
3. Click **Apply**.

&#x20;**Example:**\
✔ Add a **Docker repository** to monitor container images.\
✔ Add a **Jenkins build pipeline** to track vulnerabilities before deployment.

***

#### **Step 4: Attach Policies to the Watch**

A Watch must be linked to **one or more policies** that define security and compliance rules. For more information, see [Create Policies](../../curation/configure-curation/create-policies/).&#x20;

***

#### **Step 6: Save and Activate the Watch**

1. Review the Watch configuration.
2. Click **Save & Activate**.
3. Xray will now start **monitoring the selected resources** and enforce the attached policies.

***

### **Best Practices for Watches in Xray**

✔ **Use Separate Watches for Different Environments** – Apply different policies for **development, staging, and production**.\
✔ **Limit Watches to Critical Resources** – Avoid excessive monitoring on **temporary or non-production** repositories.\
✔ **Integrate with CI/CD Pipelines** – Automatically **fail builds that violate security policies**.\
✔ **Regularly Review and Update Watches** – Keep Watch configurations **aligned with evolving security and compliance needs**.
