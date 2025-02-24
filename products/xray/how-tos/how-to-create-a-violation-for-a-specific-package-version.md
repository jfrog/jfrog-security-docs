# How to Create a Violation for a Specific Package Version

This use case describes how to configure Xray to **create a violation for a specific package version**, preventing its use in development, CI/CD, or production environments.

***

### &#x20;**Involved**

* **Security Engineer**: Creates and enforces the violation.
* **DevOps Engineer**: Ensures CI/CD pipelines respect violation policies.
* **Developers**: May be impacted by blocked package versions and need remediation guidance.

***

### **Trigger Event**

A security or compliance issue is discovered in a **specific package version**, requiring an **enforced violation** to prevent its use.

Examples:

* A specific version of `log4j:2.14.1` contains a **critical vulnerability** (e.g., CVE-2021-44228).
* A specific version of `openssl:1.0.1` violates internal **license policies**.
* An internally developed library has a **known security flaw** in version `1.2.3`.

***

### **Preconditions**

* JFrog Xray is **enabled** and scanning repositories.
* The package version is **already indexed by Xray**.
* The organization has defined **policies for violations**.

***

### **Flow of Events**

#### **Step 1: Define a Security Policy for a Specific Package Version**

📌 **Goal:** Create a policy that applies a violation to a targeted package version.

1. Log in to the **JFrog Platform** and navigate to **Xray**.
2. Go to **Security & Compliance** → **Policies**.
3. Click **"Create Policy"**, selecting **"Security"** as the policy type.
4. Configure the policy:
   * **Name**: `Violation for Specific Package Version`
   * **Description**: Blocks a specific package version due to a known security issue.
   * **Severity**: Select the appropriate level (**Critical, High, Medium, Low**).
   * **Criteria**:
     * **Package Name**: (e.g., `log4j`)
     * **Specific Version**: (e.g., `2.14.1`)
   * **Actions**:
     * ✅ **Create Violation** (Marks the version as non-compliant).
     * ✅ **Block Download** (Prevents use of the package).
     * ✅ **Fail Build** (Stops pipelines if the version is detected).
     * ✅ **Notify Security Team** (Slack, email alerts).
5. Save the policy.

***

#### **Step 2: Attach the Policy to a Watch**

📌 **Goal:** Apply the violation to repositories and CI/CD pipelines.

1. Navigate to **Xray** → **Security & Compliance** → **Watches**.
2. Click **"Create Watch"**.
3. Define the **Scope**:
   * **Repositories**: Select repositories where the package may exist (e.g., `maven-central`, `internal-libs`).
   * **Builds**: Include build artifacts that may use the package.
   * **Packages**: Specify the exact package (e.g., `log4j:2.14.1`).
4. Attach the `Violation for Specific Package Version` policy.
5. Save and activate the Watch.

***

#### **Step 3: Attempt to Use the Violating Package (Blocked Scenario)**

📌 **Goal:** Verify that Xray prevents the usage of the flagged package version.

**Scenario 1: Manual Download Attempt (Blocked)**

A developer attempts to retrieve the flagged package version from Artifactory:

```sh
shCopyEditcurl -u <user>:<password> -O https://artifactory.example.com/artifactory/libs-release-local/log4j-2.14.1.jar
```

✅ **Expected Result:**

```sh
shCopyEditERROR: 403 Forbidden – Download blocked due to security policy violation.
```

**Scenario 2: CI/CD Build Fails Due to Violation**

A Jenkins pipeline tries to use `log4j:2.14.1`:

```sh
shCopyEditmvn clean package
```

✅ **Expected Result:**

```sh
shCopyEditBuild failed: Artifact "log4j-2.14.1.jar" contains a security violation and cannot be used.
```

***

#### **Step 4: Review & Address the Violation**

📌 **Goal:** Investigate and resolve the issue before retrying package usage.

1. Navigate to **Xray** → **Violations**.
2. Find the violation for `log4j:2.14.1`.
3. Review the details:
   * **CVE information** (if applicable).
   * **Impact Analysis** (which builds or services are affected).
   * **Suggested Remediation** (e.g., upgrade to `log4j:2.17.1`).
4. Apply a fix:
   * ✅ **Upgrade to a secure package version**.
   * ✅ **Request an exception** (if necessary).
5. Retry the build or download after addressing the violation.

***

### **Postconditions**

* The **specific package version is flagged** and cannot be used.
* The security team is **notified of the violation**.
* Developers are **forced to upgrade** to a secure or compliant version.

***

### **Alternative Flows & Considerations**

* **Allowlisting Exceptions**: If a package version is incorrectly flagged, a security admin can allowlist it temporarily.
* **Custom Violation Rules**: Adjust policies to include additional risk factors (e.g., usage in production vs. development).
* **Proactive Security**: Use **SBOM analysis** to detect and mitigate issues before violations occur.

***

### **Business Impact**

🔹 **Prevents known bad package versions** from being used in development and production.\
🔹 **Reduces security risks** by ensuring compliance with internal policies.\
🔹 **Ensures regulatory compliance** by enforcing strict package version control
