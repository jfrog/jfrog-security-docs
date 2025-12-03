# Secrets Scans

### Enable Dynamic Token Validation

This feature checks whether detected secrets are **still active**, reducing false alarms for expired or inactive credentials.

{% hint style="info" %}
Currently supported for binary scans only.
{% endhint %}

1. Navigate to **Administration** > **Xray Settings** > **Advanced Security**.
2. Locate the **Enable Dynamic Token Validation** option and enable it.
3. Save the settings.

### View & Manage Secrets Scan Results

This process helps security teams **review, assess, and act** on detected secrets to prevent credential leaks.

1. Navigate to **Scans List** > **Repositories**.
2. Select the relevant **scan report** to view detected secrets.
3. Review scan results, which include:
   * **Severity classification** (Critical, High, Medium, Low).
   * **Secret type** (e.g., API Key, OAuth Token, SSH Private Key).
   * **Suggested remediation actions** (e.g., revoke, rotate, or secure the secret).
4. Take necessary actions, such as revoking compromised secrets or configuring ignore rules.
