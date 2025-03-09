# How to Block Malicious Packages in your SDLC

This use case demonstrates how to configure Xray to enforce security policies that **block malicious artifacts before they are used in development, CI/CD, or production**.

***

### &#x20;**Involved**

* **Security Engineer**: Configures Xray to block malicious packages.
* **Developers**: Attempt to download or use an artifact that is flagged.
* **DevOps Engineer**: Ensures CI/CD pipelines comply with security policies.

***

### **Trigger Event**

A developer or automated process attempts to **download or use a package** that contains **known vulnerabilities, malware, or security risks**.

***

### **Preconditions**

* JFrog Xray is **enabled** and configured.
* Artifactory repositories are **scanned** by Xray.
* The organization has defined security policies for blocking threats.

***

### **Flow of Events**

#### **Step 1: Define a Security Policy in Xray**

📌 **Goal:** Create a security policy to block malicious or vulnerable artifacts.

1. Log in to the **JFrog Platform** and navigate to **Xray**.
2. Go to **Security & Compliance** → **Policies**.
3. Click **"Create Policy"**, selecting **"Security"** as the type.
4. Configure the policy:
   * **Name**: `Block Malicious Packages`
   * **Severity**: `Critical`
   * **Actions**:
     * ✅ **Block Download** (Prevents artifact retrieval).
     * ✅ **Fail Build** (Blocks CI/CD processes).
     * ✅ **Notify Security Team** (Email/Slack alerts).
5. Save the policy.

***

#### **Step 2: Attach the Policy to a Watch**

📌 **Goal:** Apply the security policy to relevant repositories and builds.

1. Go to **Xray** → **Security & Compliance** → **Watches**.
2. Click **"Create Watch"** and define its scope:
   * Select the **repositories** to monitor (`docker-prod`, `maven-central`, etc.).
   * Add specific **packages or artifacts** if needed.
3. Attach the `Block Malicious Packages` policy.
4. Save and activate the Watch.

***

#### **Step 3: Attempt to Download a Malicious Package**

📌 **Goal:** Verify that the security policy blocks an artifact download.

**Scenario 1: Manual Download (Blocked)**

A developer tries to download a flagged package:

```sh
shCopyEditcurl -u <user>:<password> -O https://artifactory.example.com/artifactory/libs-release-local/com/example/malicious-lib-1.0.jar
```

✅ **Expected Result:**

```sh
shCopyEditERROR: 403 Forbidden – Download blocked due to security policy violation.
```

**Scenario 2: CI/CD Pipeline Fails Due to a Blocked Artifact**

A pipeline attempts to use a vulnerable dependency in Jenkins:

```sh
shCopyEditmvn clean package
```

✅ **Expected Result:**

```sh
shCopyEditBuild failed: Artifact "malicious-lib-1.0.jar" contains a critical vulnerability and cannot be used.
```

***

#### **Step 4: Monitor & Respond to Security Violations**

📌 **Goal:** Track blocked artifacts and take appropriate action.

1. Navigate to **Xray** → **Violations**.
2. Review details of blocked packages:
   * **CVE Details** (e.g., CVE-2023-XXXXX).
   * **Impact Analysis** (which components are affected).
   * **Suggested Fixes** (e.g., upgrade `log4j:2.14.1` → `log4j:2.17.1`).
3. Take action:
   * ✅ **Upgrade the affected package** to a secure version.
   * ✅ **Manually allowlist** the package (if deemed a false positive).

***

### **Postconditions**

* The **malicious package is blocked** from being downloaded, built, or deployed.
* The security team **receives alerts** and can take action.
* Developers are **forced to use secure dependencies**, reducing risk.

***

### **Alternative Flows & Considerations**

* **Allowlisting Exceptions**: If a package is incorrectly flagged, a security admin can **temporarily allowlist** it.
* **Advanced Policy Customization**: Policies can be adjusted to block only specific severities (e.g., `Critical` but not `Medium`).
* **Automated Remediation**: Integrate with **IDE security plugins** to suggest alternative safe dependencies before a commit.

***

### **Business Impact**

🔹 **Prevents malware or vulnerable dependencies** from entering the SDLC.\
🔹 **Reduces risk of security breaches** due to unpatched libraries.\
🔹 **Ensures compliance** with regulatory security standards (e.g., NIST, OWASP).
