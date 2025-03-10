# How to Block Critical and High Vulnerabilities Before Promotion

This use case outlines how to configure JFrog Xray to **block artifact promotion based on vulnerability severity**, ensuring that only secure components are promoted.



#### **Step 1: Define a Security Policy to Block Promotion**

&#x20;**Goal:** Create a security policy to prevent artifact promotion if vulnerabilities exist.

1. Navigate to **Application > Xray** > **Watches & Policies**.
2. Click **New Policy**, enter a name, and select **Security** as the type.
3. Configure the rule:
   1. Enter a rule name.&#x20;
   2. Select CVEs as the rule type.&#x20;
   3. Select Minimal Severity as the rule category and select High Severity. This will apply only to high and critical vulnerabilities.&#x20;
   4. Set the action as **Block release bundle promotion.**&#x20;
4. Apply on Scope. Attach the Policy to a Watch that contains the Release Bundle.
5. Save the policy.

#### **Step 3: Attempt to Promote a Release Bundle (Blocked Scenario)**

**Goal:** Verify that Xray blocks the promotion of a Release Bundle with high and critical vulnerability severity.&#x20;

**Scenario: Manual Promotion (Blocked)**

A DevOps engineer attempts to promote an artifact from `staging-repo` to `prod-repo`

**Expected Result:**

The promotion is blocked due to the security violation.&#x20;

#### **Step 4: Review & Resolve Security Violations**

&#x20;**Goal:** Investigate and fix issues before retrying promotion.

1. Navigate to **Xray** > **Scans List** and select a specific Release Bundle.&#x20;
2. Go to the violations tab filter based on the violation actions and mark the Block Promotion checkbox.&#x20;
3. Review the block violations:
   * **Vulnerability Details** (e.g., CVE-2023-XXXXX).
   * **Suggested Fixes** (e.g., upgrade `log4j:2.14.1` → `log4j:2.17.1`).
4. Take action:
   * **Upgrade the affected package** to a secure version.
   * Create an Ignore Rule on the violation if deemed a false positive.
