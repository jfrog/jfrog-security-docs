# Configure Waiver Handling in Policy

You can configure how Curation handles waiver requests for each policy. This determines whether developers can request waivers and how those requests are processed.

### **Approval Modes**

#### **Automatic Approval**

Waiver is created automatically without admin review.\
Used for low-impact policies or internal workflows.

#### **Manual Approval**

The request must be reviewed and approved by a decision owner group.

#### **Not Allowed**

Waiver requests cannot be created for this policy.\
If a package is blocked by a “Not Allowed” policy, the **Submit** button is disabled and the system displays a message explaining that waivers are not permitted.&#x20;

### **Decision Owner Groups**

Each policy may specify one or more **decision owner groups**.\
These groups receive notifications for manual approvals.

Multiple groups can share ownership of decisions, enabling distributed governance across teams.

### **Waivers and Policy Scope**

Policies may limit waiver applicability based on:

* Repository scope
* Package ecosystem
* User groups
* Conditions (e.g., specific CVSS thresholds, license categories)

Waiver behavior follows the policy definition.

### **Waivers, Labels, and CVS**

* Label-based waivers are recommended and are fully compatible with CVS.
* Package-version waivers do **not** work with CVS and should be avoided when using compliant version selection.

### **Related How-Tos**

* How to Review and Approve Waiver Requests
* How Developers Request Waivers from the UI
