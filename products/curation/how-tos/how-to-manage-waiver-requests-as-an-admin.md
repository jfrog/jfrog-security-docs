# How to Manage Waiver Requests as an Admin

### **Use Case**

Admins are responsible for reviewing and acting on waiver requests created by developers when Curation blocks a package. This how-to explains the Waiver Requests page, how to navigate and filter requests, and how to approve or reject waiver requests.

### **Overview of the Waiver Requests Page**

The **Waiver Requests** page provides a complete management view of all waiver activity across the organization. Admins use this page to review incoming requests, access historical decisions, and audit the decision workflow.

#### **Page Areas**

**Pending Requests**

Displays all open waiver requests requiring admin review.\
You can sort by request number, date, package, decision owner group, policy count, or requester.

**Closed Requests**

Displays previously **approved**, **rejected**, and **expired** waiver requests for auditing and compliance.

**My Requests Toggle**

Filters the list to show only requests created by the current user.

### **Filters and Search**

Admins can refine the list using:

* **Date Range** (last 7 days, last 30 days, custom)
* **Search** (package, event details, requester)
* **Policy Count**
* **Decision Owner Group**
* **Requesters**

These filters help admins quickly locate relevant requests in large organizations.

### **What You See in a Single Waiver Request**

Opening a request displays:

* **Package name and version**
* **Requester name(s)**
* **Origin repository and server**
* **Event details** (Event ID, Date, Package URL)
* **Blocking policies table**, including:
  * Approval type (Automatic, Manual, Not Allowed)
  * Policy name
  * Condition and explanation
  * Decision owner groups

#### **Waiver Eligibility**

If **any policy** related to the event is marked **Not Allowed**, the waiver request **cannot** be approved.

The system displays:

> **One or more policies blocking this package do not allow waiver requests.**

Approval actions remain disabled.

### **Workflow Steps**

#### **Step 1: Access the Waiver Requests Page**

1. Go to **Applications → Curation → Waivers requests**.
2. Review the **Pending Requests** tab for new items.

#### **Step 2: Open a Request to Review**

Click any request to open the details panel.

Review:

* Package and version
* Event metadata
* Blocking policies
* Approval types
* Developer’s justification

#### **Step 3: Determine Waiver Eligibility**

* If all policies are **Automatic** or **Manual**, the request is eligible.
* If ANY policy is **Not Allowed**, the waiver cannot be created.

#### **Step 4: Approve or Reject the Request**

If eligible:

1. Click **Approve** to create the waiver.
2. Click **Reject** to deny the request.

The requester is notified automatically.

#### **Step 5: View Historical Decisions (Optional)**

Switch to **Closed Requests** to view previously approved or rejected waivers.

