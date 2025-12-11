# How to View and Modify Licenses in the SBOM Tab

**Use Case**

View a component’s OSS licenses and modify license entries directly from the SBOM component tree.

This workflow helps you correct inaccurate license data and ensure accurate reporting and compliance within Xray.

### **Workflow Steps**&#x20;

#### Step 1: Open the SBOM Tab

1. Navigate to **Scans List**.
2. Select the desired artifact from the list.
3. Open the **SBOM** tab.
4. Switch to the **Components Tree** to explore the dependency graph.

#### Step 2: Select a Component

1. In the tree, expand the relevant ecosystem.
2. Select the component whose licenses you want to review.

#### Step 3: View the Component’s Licenses

The right pane displays:

* All detected licenses
* License grouping (Copyleft, Permissive, etc.)
* Source of the license (JFrog, Local File, Manual)

Example:&#x20;

* GPL-2.0-or-later
* Apache-2.0
* MIT
* GPL-2.0 (Local File)
* ISC (Manual)&#x20;

This helps identify incorrect or incomplete license attribution.

#### Step 4: Edit the Component’s Licenses

1. Click **Edit Licenses** in the right pane.
2. Use the search bar to locate licenses.
3. Select or unselect licenses to update the component's license list.
4. Click **Update Licenses**.

Any license change applies to **all occurrences** of that package in the SBOM.&#x20;
