# How to Use JFrog Curation as a Developer with the JFrog CLI

**Use Case:**

As a developer, you want to check if the dependencies in your project comply with your organization’s security and licensing policies before attempting to build or deploy your application. You can use the **JFrog CLI** to scan your dependencies and determine if any packages will be blocked by JFrog Curation.

#### **Workflow Steps**

**Step 1: Install and Configure JFrog CLI**

First, ensure that you have the **JFrog CLI** installed and configured to connect to your JFrog instance.

*   **Install JFrog CLI** (if not already installed):

    ```sh
    shCopyEditcurl -fL https://install-cli.jfrog.io | sh
    ```
*   **Configure CLI with your JFrog instance**:

    ```sh
    shCopyEditjfrog config add
    ```

    * Enter your **JFrog Platform URL**
    * Provide your **username and API key**
    * Confirm connection

#### **Step 2: Run a Curation Audit on Your Project**

Use the **curation-audit** command to analyze your project dependencies and check for potential blocks.

**For a Node.js (npm) Project:**

```sh
shCopyEditjfrog curation-audit --package-type npm --project-dir .
```

**For a Java (Maven) Project:**

```sh
shCopyEditjfrog curation-audit --package-type maven --project-dir .
```

**For a Python (pip) Project:**

```sh
shCopyEditjfrog curation-audit --package-type pip --project-dir .
```

This will:

* Scan all dependencies used in your project
* Check them against your organization's **curation policies**
* Identify **blocked** or **flagged** packages
* Provide **remediation suggestions** if available

#### **Step 3: Review the Audit Results**

Once the command runs, the CLI will output a **curation summary** listing all evaluated packages. Example output:

```markdown
markdownCopyEditCuration Audit Summary:
------------------------
❌ Blocked Packages:
1. lodash@4.17.21 - Blocked due to Security Policy (CVE-2022-1234)
2. moment@2.25.3 - Blocked due to Deprecated Package Policy

⚠️ Warning:
- requests@2.18.0: License issue (GPL-3.0 detected)

✅ Approved Packages:
- express@4.17.2
- react@17.0.2
```

#### **Step 4: Take Action Based on the Results**

* **If a package is blocked:**
  * Check the reason for blocking (security, license, or operational issues).
  * Update the package to a newer, approved version.
  * Contact your security team if a waiver is needed for an essential package.
* **If a package has a warning:**
  * Check with your legal/compliance team if it can be used.
  * Consider replacing it with an alternative dependency.

#### **Step 5: Verify Fixes & Rerun the Audit**

After making changes, rerun the **curation-audit** command to confirm that your project is now compliant:

```sh
shCopyEditjfrog curation-audit --package-type npm --project-dir .
```

If no blocked packages appear, your project is safe to use under your organization's policies!
