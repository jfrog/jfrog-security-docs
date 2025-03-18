# Create Watches

This is a Step-by-Step Guide to Creating a Watch in Xray. To learn more about Watches, click [here](../features-and-capabilities/sdlc-policy-mangement/watches.md).&#x20;

1. Navigate to **Xray → Watches & Policies**.
2. Click **New Watch**.
3. In the **New Watch** window, enter a **unique name** for the Watch (e.g., "Critical Security Watch").
4. (Optional) Add a **description** to specify the Watch’s purpose.
5. Click **Add Resources**.
6. Select one or more of the following:
   * **Repositories** &#x20;
   * **Builds**&#x20;
   * **Release Bundles**&#x20;
   * **Projects**&#x20;
7. Click **Apply**.

#### **Attach Policies to the Watch**

A Watch must be linked to **one or more policies** that define security and compliance rules. For more information, see [Create Policies](../../curation/configure-curation/create-policies/).&#x20;

### **Best Practices for Watches in Xray**

* **Use Separate Watches for Different Environments** – Apply different policies for development, staging, and production.
* **Limit Watches to Critical Resources** – Avoid excessive monitoring on temporary or non-production repositories.
* **Integrate with CI/CD Pipelines** – Automatically fail builds that violate security policies.
* **Regularly Review and Update Watches** – Keep Watch configurations aligned with evolving security and compliance needs.
