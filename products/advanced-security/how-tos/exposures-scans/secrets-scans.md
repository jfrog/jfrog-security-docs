# Secrets Scans

## **Enable Secrets Scanning**

This step ensures that repositories are configured to scan for **hardcoded secrets, exposed credentials, and sensitive information** within artifacts.

1. Navigate to **Administration** → **Xray Settings** → **General**.
2. Select **Indexed Resources** and choose the repository where you want to enable scanning.
3. Enable **Secrets Scans** from the list of security scanning categories.
4. Save the configuration.

## **Run a Secrets Scan on an Artifact**

This process triggers an **on-demand scan** for secrets within a specific artifact stored in a repository.

1. Navigate to **Scans List** → **Repositories Tab**.
2. Select the **repository** containing the artifact you want to scan.
3. Locate the artifact and click the **Actions Menu**.
4. Select **Scan for Secrets** to initiate the scan.
5. Once completed, review results under **Security Issues**.

## **Configure Secrets Ignore Rules**

Ignore rules helps **reduce noise** by filtering out **false positives or non-actionable violations** in secret detection results.

1. Navigate to **Scans List** and locate the reported **Secrets Violation**.
2. Open the violation details and review the flagged issue.
3. Click **Ignore Violation** and configure an ignore rule using one of the following criteria:
   * **Based on Secret Type** – Ignore a specific type of secret (e.g., API Key, SSH Private Key).
   * **Based on File Path** – Ignore secrets found in a specific file or directory.
   * **Based on Artifact Name** – Ignore secrets detected in a particular artifact version.
4. Save the ignore rule to apply it to future scans.

## **Enable Dynamic Token Validation**

This feature checks whether detected secrets are **still active**, reducing false alarms for expired or inactive credentials.

1. Navigate to **Administration** → **Xray Settings** → **Advanced Security**.
2. Locate the **Enable Dynamic Token Validation** option and enable it.
3. Save the settings.

## **View & Manage Secrets Scan Results**

This process helps security teams **review, assess, and act** on detected secrets to prevent credential leaks.

1. Navigate to **Scans List** → **Repositories**.
2. Select the relevant **scan report** to view detected secrets.
3. Review scan results, which include:
   * **Severity classification** (Critical, High, Medium, Low).
   * **Secret type** (e.g., API Key, OAuth Token, SSH Private Key).
   * **Suggested remediation actions** (e.g., revoke, rotate, or secure the secret).
4. Take necessary actions, such as revoking compromised secrets or configuring ignore rules.
