# View Scan Results in GitHub Security

Frogbot performs both full repository scans and pull request (PR) scans to detect security issues. Results are posted directly to the GitHub Security dashboard, allowing developers to stay within their native GitHub workflow.

### Before You Begin

* It is essential that you enable [GitHub code scanning](https://docs.github.com/en/code-security/code-scanning/introduction-to-code-scanning/about-code-scanning) for the repositories you wish to scan.
* Full repository scans automatically appear in GitHub Security.
* PR scans must be manually enabled.

### Procedure

1.  (Optional) Enable PR security results by setting the following environment variable to true:

    ```ini
    JF_UPLOAD_PR_SECURITY_RESULTS_TO_VCS=true
    ```
2. In GitHub, go to the repository scanned by Frogbot and click the **Security** tab.
3. In the left pane, select **Code scanning** alerts.\
   Full repository scan results appear under the scanned branch and are filtered by `branch:<branch-name>`.\
   PR scan results appear under the scanned PR and are filtered by `pr:<pr-number>`.
4. (Optional) Use the filter **Tool** to narrow down results.\
   The Frogbot tools to filter with are:

* JFrog SAST
* JFrog Secrets scanner
* JFrog Terraform scanner
* JFrog Xray scanner

5. Click an issue to view its details.
