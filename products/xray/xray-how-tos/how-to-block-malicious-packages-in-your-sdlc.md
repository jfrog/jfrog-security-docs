# How to Block Malicious Packages in your SDLC

This use case demonstrates how to configure Xray to enforce security policies that block malicious packages before they are used in development, CI/CD, or production.

#### **Step 1: Define a Security Policy in Xray**

**Goal:** Create a security policy to block malicious or vulnerable artifacts.

1. Navigate to **Application > Xray** > **Watches & Policies**.
2. Click **New Policy**, enter a name, and select **Security** as the type.
3. Configure the rule:
   1. Enter a rule name.&#x20;
   2. Select Malicious Packages as the rule type.&#x20;
   3. Set the following actions based on the stage you want to block/fail.&#x20;
      * **Block download**&#x20;
      * **Fail Build**
      * **Block release bundle promotion**
      * **Block release bundle distribution**
4. Apply on Scope. Attach the Policy to a Watch this will apply the security policy to relevant resources.&#x20;
5. Save the policy.

#### **Step 3:  Verify that the Security Policy Blocks a Malicious Package**

**Scenario 1: Manual Download (Blocked)**

A developer tries to download a malicious package

**Expected Result:**

The package is blocked from download.&#x20;

**Scenario 2: CI/CD Pipeline Fails Due to a Malicious Package**

A pipeline attempts to use a malicious package dependency in Jenkins

**Expected Result:**

The pipeline failed due to a malicious package.

**Scenario 3: Release Bundle Promotion/Distribution Blocked Due to Malicious Packages**

A user tries to distribute or promote a Release Bundle that contains a malicious package.&#x20;

**Expected Result:**

The action is blocked due to a malicious package.

#### **Step 4: Monitor & Respond to Security Violations**

&#x20;**Goal:** Track blocked packages and take appropriate action.

1. Navigate to **Xray** > **Scans List** and select a specific resource.&#x20;
2. Review the violations:
   * **Vulnerability Details** (e.g., CVE-2023-XXXXX).
   * **Suggested Fixes** (e.g., upgrade `log4j:2.14.1` → `log4j:2.17.1`).
3. Take action:
   * **Upgrade the affected package** to a secure version.
   * Create an Ignore Rule on the violation if deemed a false positive.
