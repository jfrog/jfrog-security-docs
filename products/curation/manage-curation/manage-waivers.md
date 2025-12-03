# Manage Waivers

### Curation Waivers Approval Flow

**1. Policy Configuration (Step 5)**

In the final stage of policy creation, you must configure the waiver request options for blocked packages. There are three main options:

* **Not Allowed**: Waiver requests cannot be automatically made for this policy.
* **Manually Approved**: All waiver requests will require manual review and approval from the policy owner.
  * When this option is selected, you must designate a Decision Owner. This is a group of users who can review and approve or reject waiver requests. They will receive notifications when a waiver is requested.
* **Automatically Approved**: The system automatically approves waiver requests. This option is typically used for "soft block" policies like operational risks or licenses that require an opt-in decision. No decision owner needs to be assigned for this option.

**2. Waiver Request Flow Initiation**

Once the policy is configured, the waiver flow is initiated by the developer:

* If a package is blocked by specific policies, the developer runs the `JF CA` command.
* The command will list all blocked packages and prompt the developer to request a waiver.
* The developer must specify which packages to request waivers for and describe why they want this package.

Based on the policy settings:

* **Manual Approval**: A request will be created, and the policy owner will receive an email for review.
* **Automatic Approval**: The waiver will be granted automatically, allowing the developer to proceed without issues.

**3. Waiver Management Interface**

A new section for managing waivers has been added to the platform:

* **Pending Requests**:
  * A toggle at the top allows owners to view only requests assigned to them or all requests in the system.
  * Clicking a request displays the developer who requested it, the policies blocking it, and the owner assigned to those policies.
* **Multiple Considerations**:
  * Multiple policies can block a single package.
  * More than one owner may be required for a specific request (e.g., a legal team for one policy, a technical team for another).
* **Closed Requests**:
  * This section shows all approved, rejected and automatically approved requests.
  * Users can audit the system to see detailed logs of who approved or rejected requests and when those actions were taken.
  * Approved waiver is created as a label, which can be reused or reconfigured in the catalog.&#x20;

Waiver management is supported on the JFrog CLI for Curation. For more information, see [here](../../../developers/cli/curation-compliance-check.md#exclude-specific-packages-or-versions-from-policy-restrictions-using-waivers).
