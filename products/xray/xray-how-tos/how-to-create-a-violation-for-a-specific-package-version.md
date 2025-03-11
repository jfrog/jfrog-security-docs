# How to Create a Violation for a Specific Package Version

This use case describes how to configure Xray to **create a violation for a specific package version.**

#### **Step 1: Define a Security Policy for a Specific Package Version**

**Goal:** Create a policy that applies a violation to a targeted package version.

1. Navigate to **Application > Xray** > **Watches & Policies**.
2. Click **New Policy**, enter a name, and select **Security** as the type.
3. Configure the rule:
   1. Enter a rule name.&#x20;
   2. Select Package Version as the rule type.&#x20;
   3. Select Package Type and provide the package name. Take note that this field depends on the package type, the specific instructions are in the watermark of the field.&#x20;
   4. Select a specific version or all versions of the package.
4. Apply on Scope. Attach the Policy to a Watch.
5. Save the policy.

#### **Step 4: Review & Address the Violation**

**Goal:** Investigate and resolve the issue before retrying package usage.

1. Navigate to **Xray** > **Scans List** and select a specific resource.&#x20;
2. Go to the violations tab and review the violation.
3. Take action:
   * **Upgrade the package** to a secure version.
   * Create an Ignore Rule on the violation if deemed a false positive.

