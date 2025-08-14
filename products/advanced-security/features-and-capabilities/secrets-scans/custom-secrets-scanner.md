# Custom Secrets Scanner

The Custom Secrets scanner lets you define search patterns to detect sensitive information in your artifacts and source code, scanning both binary and text files.

JFrog Advanced Security includes built-in secret detection, but your organization may have unique secrets or patterns that require a customized approach.\
Custom secret scanners allow you to define specific patterns using RE2 regular expressions and seamlessly integrate them into the Advanced Security scanning process. This ensures comprehensive secret detection across your entire software development lifecycle.

### Before You Begin

Consider these regex best practices:&#x20;

* Craft regex patterns carefully to prevent performance issues and false positives
* Thoroughly test regex patterns before deployment&#x20;

Ensure compliance with RE2 syntax, as Xray uses the RE2 regex engine; refer to the [RE2 documentation](https://github.com/google/re2/wiki/syntax) for supported syntax and limitations.

### Create a Custom Scanner

1. In the Xray **Administration** tab, go to **Xray Settings** and select **Custom Scanners**.
2. Select **Create New Scanner** and fill in the following fields:
   1. **Name**: A descriptive name for your scanner.
   2. **Description**: A detailed explanation of the scanner's purpose. The scan result will display this description when a matching secret is detected.
   3. **Severity**: Assign a severity level (High, Medium, Low) to identified secrets.
   4. **CWE** (Optional): Associate a relevant CWE for better vulnerability tracking.
   5. **Scanner Code**: The regular expression pattern to search for.
   6. **Notes** (Optional): Any additional information about the scanner.
3. Select **Save**.

### Manage Existing Custom Scanners

1. In the **Custom Scanners** view, you can:
   1. **Enable**/**Disable**: Activate or deactivate a scanner. \
      Only enabled scanners are used in scans.
   2. **Edit**: Modify an existing scanner's settings.&#x20;
   3. **Delete**: Remove a custom scanner.&#x20;
   4. **View**: See details about each scanner.

### View Custom Scan Results

Custom scan results can be viewed in Xray’s [Scans List](https://jfrog.com/help/r/jfrog-security-documentation/xray-scans-list).

### Example

To detect API keys with the prefix `API_KEY_`, you can create a custom scanner with the following settings:

* Name: API Key Scanner
* Description: Detects API keys with the `API_KEY_` prefix
* Severity: High

Regex: `API_KEY_[a-zA-Z0-9]{32}`
