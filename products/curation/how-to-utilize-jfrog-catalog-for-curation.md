# How to Utilize JFrog Catalog for Curation

**Use Case:**

As a security or DevOps team, you want to leverage **JFrog Catalog** to enhance **Curation policies** by categorizing packages into **allowlists, blocklists, and waivers**. This ensures that only approved software components are used in your organization while blocking risky dependencies.

***

#### **Workflow Steps**

#### **1️⃣ Enable JFrog Curation and Catalog Integration**

Ensure that **JFrog Curation** is enabled and configured to use **JFrog Catalog**:

* Navigate to **Administration > Curation > General**.
* Ensure the **Curation application** is **ON**.
* Check that **Catalog Integration** is active in your environment.
*   If needed, configure **Catalog Central** in the `system.yaml` file:

    ```yaml
    yamlCopyEditcatalog:
      enabled: true
      central:
        enabled: true
        url: https://jfrogxraycatalog.jfrog.io/xray
        username: <USERNAME>
        password: <PASSWORD>
    ```
* Restart the Xray service for changes to take effect.

***

#### **2️⃣ Use Catalog Labels to Manage Packages**

**A. Create a Label in JFrog Catalog**

Labels allow you to group packages based on security, compliance, and operational needs.

1. **Go to JFrog Catalog** in the JFrog UI.
2. Select **Package/Version > Labels**.
3. Click **Add a Label** and provide a meaningful name (e.g., `approved-packages` or `banned-packages`).
4. Select whether the label applies to **specific versions** or **all versions** of a package.
5. Save the label.

💡 **Tip**: Labels are case-sensitive and should follow a clear naming convention for consistency.

**B. Apply Labels to Packages**

1. Locate the package in the **Catalog UI**.
2. Click **+ Add Label** and select the appropriate label.
3. Labels can be used to:
   * **Allowlist** (e.g., `trusted-packages`)
   * **Blocklist** (e.g., `blacklisted-packages`)
   * **Waivers** (e.g., `temporary-exemptions`)

***

#### **3️⃣ Create Curation Policies Based on Catalog Labels**

1. **Go to Administration > Curation > Policies Management** and click **Create Policy**.
2. Name the policy (e.g., **Allow Only Approved Packages from Catalog**).
3. Under **Policy Scope**, select:
   * **All Curated** to apply it across all repositories.
   * **Specific Repositories** to target a subset.
4. In **Policy Conditions**, select:
   * **Block packages listed by Catalog labels** (for blocklists).
   * **Allow only packages listed by Catalog labels** (for allowlists).
5. Choose the relevant **label(s)** created in **Step 2**.
6. Select **Block** or **Dry Run** as the action.
7. Enable **notifications** to inform requesters when a package is blocked.
8. Click **Save Policy**.

***

#### **4️⃣ Apply Waivers Using Labels in Policies**

Waivers allow exceptions for specific packages while still enforcing broader security policies.

1. Navigate to **Administration > Curation > Policies Management**.
2. Edit an existing policy or create a new one.
3. In **Step 4: Create a Waiver**, select **Use Labels as Waiver**.
4. Choose the **waiver label** (e.g., `temporary-exemptions`).
5. Add a **justification** for why these packages should be exempted.
6. Save the policy.

Packages tagged with the **waiver label** will now be allowed, even if they match a block condition.

***

#### **5️⃣ Validate Your Curation Policies with JFrog CLI**

After configuring **Catalog-based Curation policies**, verify package compliance using the **JFrog CLI**:

```sh
shCopyEditjfrog curation-audit --package-type npm --project-dir .
```

This will output:\
✅ **Allowed packages** based on Catalog labels\
❌ **Blocked packages** due to missing or restricted labels\
⚠️ **Warnings** for flagged packages needing review
