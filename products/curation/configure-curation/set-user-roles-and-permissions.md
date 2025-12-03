# Set User Roles and Permissions

In JFrog Curation, user roles and permissions are integral to managing access and ensuring security within your software supply chain. The platform offers predefined roles, each with specific permissions tailored to different aspects of curation management.

### **Predefined Roles in JFrog Curation**

**Platform Admin**:

* **General Settings**: Turn ON/OFF the Curation service, and manage general notification emails and other general settings.
* **Repositories Management**: Connect and disconnect repositories from Curation.
* **Condition**: Create, edit, and delete custom conditions.
* **Overview**: View Curation coverage and usage statistics.
* **Policies**: Create, edit, and delete policies.
* **Audit**: View blocked/approved actions, dry runs actions, and review user actions.

**Manage Policies**

* **General Settings**: Forbidden
* **Repositories Management**: Forbidden
* **Condition**: Create only
* **Overview**: View Curation coverage and usage statistics.
* **Policies**: Create, edit, and delete policies.
* **Audit**: View blocked/approved actions, dry runs actions, and review user actions.

**Read Policies**

* **General Settings**: Forbidden
* **Repositories Management**: Forbidden
* **Condition**: Forbidden
* **Overview**: View Curation coverage and usage statistics.
* **Policies**: View policies only.
* **Audit**: View blocked/approved actions, dry runs actions, and review user actions.

### **Assigning Roles to Users**

To assign these roles to users within the JFrog Platform:

1. **Access the Administration Module**:
   * Log in to the JFrog Platform.
   * Navigate to the **Administration** section.
2. **Manage Users**:
   * Select **Identity and Access**.
   * Click on **Users** to view the list of platform users.
3. **Assign Roles**:
   * Choose the user to whom you want to assign a role.
   * In the user’s profile, locate the **Roles** section.
   * Click on **Assign Roles**.
   * From the list of available roles, select either **Administer platform** (for all privileges), **Manage policies** (for just policy control), or **Read polices** (for developers), depending on the user's responsibilities.
   * Save the changes to update the user's permissions.
