# How to Block Critical and High Vulnerabilities Before Promotion

This use case outlines how to configure JFrog Xray to **block artifact promotion based on vulnerability severity**, ensuring that only secure components are deployed.

***

### &#x20;**Involved**

* **Security Engineer**: Defines and enforces vulnerability-based promotion policies.
* **DevOps Engineer**: Manages CI/CD pipelines and artifact promotion workflows.
* **Release Manager**: Oversees artifact readiness for production deployment.

***

### **Trigger Event**

A development team attempts to **promote an artifact** (e.g., from **dev → staging** or **staging → production**), but the artifact contains **critical or high-severity vulnerabilities** detected by Xray.

***

### **Preconditions**

* JFrog Xray is **enabled** and scanning artifacts.
* Security policies are **defined** to block promotion based on vulnerability severity.
* CI/CD pipelines are configured to **use Xray enforcement rules** for promotion.

***

### **Flow of Events**

#### **Step 1: Define a Security Policy to Block Promotion**

📌 **Goal:** Create a security policy to prevent artifact promotion if vulnerabilities exist.

1. Log in to the **JFrog Platform** and navigate to **Xray**.
2. Go to **Security & Compliance** → **Policies**.
3. Click **"Create Policy"**, selecting **"Security"** as the type.
4. Configure the policy:
   * **Name**: `Block Promotion of Vulnerable Artifacts`
   * **Severity Threshold**: Select **Critical** and **High**.
   * **Actions**:
     * ✅ **Block Artifact Promotion** (Prevents promotion to higher environments).
     * ✅ **Fail CI/CD Pipeline** (Stops deployments if violations exist).
     * ✅ **Notify Security Team** (Alerts via Slack, email, or Webhooks).
5. Save the policy.

***

#### **Step 2: Attach the Policy to a Watch**

📌 **Goal:** Apply the security policy to relevant repositories and builds.

1. Go to **Xray** → **Security & Compliance** → **Watches**.
2. Click **"Create Watch"** and define its scope:
   * Select the **repositories** containing build artifacts (e.g., `staging-repo`, `prod-repo`).
   * Add **specific build names** if necessary.
3. Attach the **Block Promotion of Vulnerable Artifacts** policy.
4. Save and activate the Watch.

***

#### **Step 3: Attempt to Promote an Artifact (Blocked Scenario)**

📌 **Goal:** Verify that Xray blocks the promotion of a vulnerable artifact.

**Scenario 1: Manual Promotion (Blocked)**

A DevOps engineer attempts to promote an artifact from `staging-repo` to `prod-repo`:

```sh
shCopyEditjfrog rt mv staging-repo/com/example/app-1.0.jar prod-repo/
```

✅ **Expected Result:**

```sh
shCopyEditERROR: Artifact promotion blocked due to security policy violation.
```

**Scenario 2: CI/CD Pipeline (Blocked)**

A Jenkins pipeline attempts to promote a build:

```sh
shCopyEditcurl -X POST -u user:password "https://artifactory.example.com/api/build/promote" \
  -H "Content-Type: application/json" \
  -d '{
        "buildName": "my-app",
        "buildNumber": "42",
        "targetRepo": "prod-repo"
      }'
```

✅ **Expected Result:**

```sh
shCopyEditBuild promotion failed: Critical vulnerability detected (CVE-2023-XXXXX).
```

***

#### **Step 4: Review & Resolve Security Violations**

📌 **Goal:** Investigate and fix issues before retrying promotion.

1. Go to **Xray** → **Violations**.
2. Select the blocked artifact and review:
   * **CVE Details** (e.g., `CVE-2023-XXXXX`).
   * **Affected dependencies** (e.g., `log4j:2.14.1`).
   * **Suggested Remediation** (e.g., upgrade to `log4j:2.17.1`).
3. Apply a fix:
   * ✅ **Upgrade the package** to a secure version.
   * ✅ **Request an exception** (only in controlled cases).
4. Reattempt artifact promotion after fixing vulnerabilities.

***

### **Postconditions**

* The **artifact is blocked** from promotion if it contains critical/high vulnerabilities.
* The security team is **notified of violations** and can take action.
* Only **secure artifacts** move to staging and production environments.

***

### **Alternative Flows & Considerations**

* **Allowlisting Exceptions**: If a false positive occurs, the security team can allowlist a package for promotion.
* **Policy Customization**: Configure different policies for different environments (e.g., stricter rules for production).
* **Automated Fix Recommendations**: Use IDE security scanning or SBOM analysis to suggest secure versions before promotion.

***

### **Business Impact**

🔹 **Prevents vulnerable artifacts** from reaching critical environments.\
🔹 **Reduces security risks** by enforcing strict promotion controls.\
🔹 **Ensures compliance** with security regulations (e.g., NIST, OWASP, ISO 27001).
