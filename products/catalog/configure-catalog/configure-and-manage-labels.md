# Configure and Manage Labels

Catalog Labels in JFrog Catalog allow users to organize and manage software packages efficiently. These labels help enforce security and compliance policies, enabling organizations to curate and control the use of third-party packages.

#### **Key Benefits:**

* **Streamline Package Management** – Group and categorize packages for better organization.
* **Enforce Security & Compliance Policies** – Use labels to define allowlists and blocklists.
* **Automate Workflow Integration** – Apply labels programmatically via GraphQL API.

### **Label Management**

#### **Creating a Label**

1. Navigate to **Package/Version > Labels**.
2. Click **Add a Label** and enter a name.
3. (Optional) Provide a description to clarify its purpose.
4. Select whether the label applies to:
   * **Specific Versions** – Assign labels to selected package versions.
   * **All Versions** – Apply labels to all past and future versions.
5. Click **Save Label** to confirm.

#### **Applying an Existing Label**

* Select a package version and click **+ Add Label**.
* Choose from the list of pre-existing labels.
* The label is now applied to the selected package version.

#### **Removing a Label**

* Locate the package version with the label.
* Click the **(X)** next to the label to remove it.
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

