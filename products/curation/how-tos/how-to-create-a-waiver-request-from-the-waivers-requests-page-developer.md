# How to Create a Waiver Request from the Waivers Requests Page (Developer)

### **Use Case**

When a package is blocked by Curation, developers can submit a waiver request directly from the Waivers Requests page. This how-to describes how to locate blocked packages, review event details, and submit a justification.

### **Overview of the Waiver Requests Page (Developer Perspective)**

Developers use this page to:

* Create new waiver requests
* Track their own open and closed requests
* Review the status of pending requests (Approved, Rejected, Automatic)

#### **Page Areas**

**Create New Request**

Starts the waiver creation flow.

**Pending Requests**

Shows open requests relevant to the developer.

**Closed Requests**

Displays previously approved or rejected requests.

**My Requests Toggle**

Filters the list to show only the developer’s own requests.

Developers typically use this page to self-service waiver creation without relying on CLI.

### **Workflow Steps**

#### **Step 1: Start a New Request**

1. Go to **Applications → Curation → Waivers requests**.
2. Click **Create New Request**.

#### **Step 2: Select Blocked Package and Requester**

**Package Name**

* Begin typing to search blocked packages.
* Autocomplete uses audit data.

**Version**

Select the version that triggered the block.

**Requester**

* If multiple requesters were involved, select the correct name.
* If only one exists, it is automatically selected.

**Origin Repository**

Appears only when the block occurred across multiple repos.

Click **Next**.

#### **Step 3: Review Blocked Event Details**

The page displays:

* Event ID
* Date
* Package URL
* Origin Server
* Origin Repository
* Blocking Policies Table
  * Approval type
  * Condition
  * Explanation
  * Decision owner group

If any policy = **Not Allowed**, submission is disabled.

Banner shown:

> **One or more policies blocking this package do not allow waiver requests.**

#### **Step 4: Enter a Justification**

* Type the request reason (required).
* Max 300 characters.
* The **Submit** button activates only when the reason is valid and all policies allow waivers.

#### **Step 5: Submit the Waiver Request**

Click **Submit**.\
You will see a confirmation message and be redirected back to the **Waivers Requests** page.



