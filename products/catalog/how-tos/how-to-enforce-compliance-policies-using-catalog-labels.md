# How to Enforce Compliance Policies Using Catalog Labels

&#x20;**Use Case:** A compliance team wants to ensure that only **approved OSS packages** are used in development and that high-risk packages are blocked.

**Steps:**

1. **Create Labels for Package Management**
   * Go to **Package/Version > Labels** in JFrog Catalog.
   * Click **Add a Label**, name it `"Approved"` for safe packages.
   * Create another label called `"Restricted"` for high-risk packages.
2. **Apply Labels to Packages**
   * Search for specific OSS packages used in your repositories.
   * Assign `"Approved"` to secure packages.
   * Assign `"Restricted"` to packages with **compliance risks** (e.g., GPL-licensed software if your organization restricts GPL usage).
3. **Define Curation Policies**
   * Navigate to **JFrog Curation** in the JFrog Platform.
   * Create a policy that **blocks packages labeled `"Restricted"`** from being downloaded.
   * Create a policy that **allows only `"Approved"` packages** for internal use.
4. **Automate Compliance Enforcement**
   * Use the **GraphQL API** to programmatically assign labels to new OSS packages.
   * Set up notifications to alert teams when a **new package violates the compliance policy**.
