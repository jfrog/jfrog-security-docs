# Configure and Manage Labels

Labels in JFrog Catalog help you organize, manage, and secure your software packages. You can apply one or more labels to any package version, enabling flexible grouping, enforcing security/compliance policies, and integrating into CI/CD workflows via API.

#### **Key Benefits:**

* **Streamline Package Management** – Group and categorize packages for better organization.
* **Enforce Security & Compliance Policies** – Use labels to define allowlists and blocklists.
* **Automate Workflow Integration** – Apply labels programmatically via GraphQL API.

### **Label Management**

#### Dedicated Label Management Page

You can now manage labels directly from a **dedicated Labels page** in the UI. This centralized interface allows you to:

* View all existing labels in one place and all applied labels on a package or version.
* Create new labels with descriptions.&#x20;
* Add packages and versions to a label directly from this page.
* Edit existing labels, including updating their scope.
* Remove labels from specific versions without deleting the label.

#### **Creating a Label**

1. Navigate to **Labels**.
2. Click **Create a New Label** and enter a name.
3. Provide a description to clarify its purpose.
4. Click **Save Label** to confirm. \
   The label is added to the Labels table. You can now proceed to add Packages and Package Versions to the label. &#x20;

**Add Packages to a Label**

1. Select the Label, and click **Add Packages**.&#x20;
2. Select the packages and versions you want to apply this label to. \
   You can add multiple packages.&#x20;

**Manage Packages Associated with a Label**

When you open a label:

* You'll see a **list of packages** currently associated with it.
* Each entry includes:
  * The **package name**
  * The **specific versions** associated with the label
  * Timestamps for when the package was **last edited** and **last updated**

You have full control to manage package associations:

* **Add or remove specific versions** from a label
* **Remove the entire package** from the label if it's no longer relevant

This makes it easy to keep labels accurate, up-to-date, and aligned with your organization’s compliance or policy goals.

#### **Applying an Existing Label to a Package in Explore View**

* Select a package version and click **+ Add Label**.
* Choose from the list of pre-existing labels or create a new one.&#x20;
* The label is now applied to the selected package version.

#### **Removing a Label**

* Locate the package version with the label.
* Click the trash icon next to the label to remove it.
* Note: This action only removes the label from the package, not from the system.

### **Using Labels in Curation Policies**

Labels play a crucial role in **JFrog Curation Policies**, helping enforce package security and compliance.

#### **Blocking Packages**

Organizations can create policies to block packages that carry specific labels, preventing their use.

#### **Allowing Pre-Approved Packages**

Conversely, labels can be used to allow only vetted packages, ensuring only trusted software is used.

#### **Applying Policy Conditions**

Policies can be defined based on label assignments:

* **Blocklist Approach** – Restrict packages assigned to a **banned label**.
* **Allowlist Approach** – Permit only packages associated with an **approved label**.

Once policies are in place, package restrictions are automatically enforced in the JFrog Catalog.

***

### **Automating Label Management with GraphQL API**

Administrators can programmatically manage labels using JFrog's **GraphQL API**. Actions include:

* Creating and deleting labels.
* Assigning and removing labels from packages.
* Querying packages based on label assignments.

By leveraging automation, teams can scale their security and compliance workflows more efficiently.

