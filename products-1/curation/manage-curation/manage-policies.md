# Manage Policies

The Policies Management window enables administrators to view the details of each curation policy, as well as edit and delete policies.

### **Access Policies Management**

1. **Navigate to Policies Management**:
   * Log in to the JFrog Platform.
   * Click on the **Application** tab.
   * Select **Curation** > **Policies Management**.

In the **Policies Management** window, policies are organized into two tabs:

* **Active**: Displays policies currently applied to one or more remote repositories.
* **Inactive**: Lists policies not assigned to any repositories.

Each policy entry includes the following details:

* **Policy Name**: The designated name of the policy.
* **Repositories**: The repositories to which the policy applies (visible in the Active tab).
* **Policy Condition**: The specific criteria or conditions defined in the policy.
* **Policy Action**: The action taken when the policy's conditions are met (e.g., Block or Dry Run).

### **Editing an Existing Policy**

1. **Locate the Policy**:
   * In the **Policies Management** window, find the policy you wish to edit.
2. **Edit the Policy**:
   * Click on the actions menu (three dots) next to the policy.
   * Select **Edit Policy**.
   * Make the necessary changes following the steps outlined in the policy creation process.

### **Deleting a Policy**

1. **Identify the Policy to Delete**:
   * In the **Policies Management** window, locate the policy you intend to remove.
2. **Delete the Policy**:
   * Click on the actions menu (three dots) adjacent to the policy.
   * Select **Delete Policy**.
   * Confirm the deletion when prompted.

### **Disabling Policies by Disconnecting Repositories**

If a remote repository should no longer be curated, disconnecting it will disable all associated policies:

1. Navigate to **Curated Repositories**.
2. Toggle off curation for the desired repository.
3. Confirm the action.
4. The repository will no longer be subject to curation rules, and related policies will become inactive if they were only applied to that repository.
