# Manage Waivers

* If a package is blocked by specific policies, the developer runs the `JF CA` command.
* The command will list all blocked packages and prompt the developer to request a waiver.
* The developer must specify which packages to request waivers for and describe why they want this package.

```
jf curation-audit
```

* The command will list all blocked packages and prompt the developer to request a waiver.
* The developer must specify which packages to request waivers for and describe why they want this package.

Waivers provide a controlled way for organizations to temporarily override Curation policy decisions. When a package is blocked—due to vulnerabilities, licenses, malicious indicators, or policy rules—authorized users can request or approve a waiver to allow the package to be used under defined governance.

Waivers support two personas:

* **Admins** configure waiver behavior and approve requests.
* **Developers** request waivers when they are blocked and need to proceed with their work.

This page provides an overview of the waiver model, lifecycle, and user responsibilities.\
Use the links below to continue to the relevant persona workflows.

### **Waiver Types**

#### **Label-based waivers (Recommended)**

Applies when a package has a specific label used by a policy’s conditions.\
Fully supported across all ecosystems, direct & transitive resolution, and **required for CVS compatibility**.

#### **Package-version waivers (Legacy)**

A waiver assigned to a specific version.\
**Does not work with CVS** and is gradually being replaced by label-based waivers.

### **Waiver Lifecycle**

1. **Package request is blocked** by a Curation policy.
2. **Developer submits a waiver request** (from UI, Audit, or CLI).
3. **Relevant decision owner group** is notified.
4. **Admin reviews the request** and approves or rejects it.
5. **Decision is enforced** in Curation.
6. **Developer is notified** of the decision.

### **Waiver Personas**

#### **Admins**

* Configure waiver handling in policy settings
* Define approval modes (automatic/manual/not allowed)
* Manage and review waiver requests
* Receive email notifications
* Ensure governance and audit compliance

See [how-to-manage-waiver-requests-as-an-admin.md](../how-tos/how-to-manage-waiver-requests-as-an-admin.md "mention")

#### **Developers**

* Request waivers when blocked
* Use the UI or Audit page to submit a request
* Provide justification
* Track request status

See [how-to-create-a-waiver-request-from-the-waivers-requests-page-developer.md](../how-tos/how-to-create-a-waiver-request-from-the-waivers-requests-page-developer.md "mention"), [how-to-create-a-waiver-request-from-the-audit-page.md](../how-tos/how-to-create-a-waiver-request-from-the-audit-page.md "mention")
