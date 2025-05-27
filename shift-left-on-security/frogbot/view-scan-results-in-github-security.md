# View Scan Results in GitHub Security

Frogbot performs both full repository scans and pull request (PR) scans to detect security issues. Results from full scans are posted directly to the GitHub Security dashboard, allowing developers to stay within their native GitHub workflow.

{% hint style="info" %}
This is an [Advanced Security](../../products/advanced-security/) feature
{% endhint %}

### Before You Begin

It is essential that you enable [GitHub code scanning](https://docs.github.com/en/code-security/code-scanning/introduction-to-code-scanning/about-code-scanning) for the repositories you wish to scan.

### Procedure

1. In GitHub, go to the repository scanned by Frogbot and click the **Security** tab.
2. In the left pane, select **Code scanning alerts**.
3. (Optional) Use the **Tool** filter to narrow down results.\
   The Frogbot tools to filter with are:

* JFrog SAST
* JFrog Secrets scanner
* JFrog Terraform scanner
* JFrog Xray scanner

4. Click an issue to view its details.
