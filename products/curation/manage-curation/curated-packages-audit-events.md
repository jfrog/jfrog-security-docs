# Curated Packages Audit Events

Audit Events provides visibility into package management activities, focusing on security, compliance, and governance transparency. It enables users with curation permissions to view, filter, analyze, and export audit data, helping to track how packages are managed within the organization. Audit data is retained for 30 days and can be accessed manually through the UI or via APIs and webhooks.

Audit Events are divided into two main sections:

* Search Bar
* Results Table (Blocked, Approved, Dry Run, Passed Packages)

### Search Bar

The Search Bar allows users to filter and search audit events using:

* **Package Name**: Enter a package name to locate relevant audit events.
* **Package Version**: Specify a version to narrow your search results further.
* **Date Picker**: Adjust the time frame by selecting specific dates or a range of hours.

> **Note**: Searches are limited to available audit events. If a package does not appear in the results, it means it was not recorded in the audit and may still exist in the artifact repository.

### Results Table

The Results Table is organized into four tabs that display audit results based on package status:

#### Blocked

* Lists packages that have been blocked due to policy violations.
* Clicking a package name reveals detailed information, including:
  * **Validated Policies**: Policies that triggered the block.
  * **Reason for Validation**: Explanation for why the package was blocked.
  * **Package Information**: Metadata about the package.
  * **Remediation Recommendations**: Suggested actions for resolution, such as links to fixed versions if available.

#### Approved

* Displays packages that successfully passed curation.
* Some packages may appear as "bypassed," indicating that although they violated a policy, they were allowed through under relaxed conditions.

#### Dry Run

* Simulates the effect of policies without enforcing them.
* Helps users:
  * Assess the potential impact of proposed policy changes.
  * Identify packages that _would_ have been blocked without disrupting workflows.
* Dry Run entries are informational only and do not affect actual package availability.

#### Passed

* Shows packages that went through curation without being inspected by any policies.
* It's important to monitor this tab, as unvalidated packages could pose risks if they contain unreviewed malicious or vulnerable components.

### Exporting Audit Data

Users can export visible audit data into a CSV file for further analysis or reporting:

* Click the **Export to CSV** button located at the top right of the screen.
* Only the currently visible, filtered data will be exported.

Exports are available for all sections, including Blocked, Approved, Dry Run, and Passed results.

### API and Webhook Integration

For programmatic access and workflow automation:

* Use the provided **APIs** to retrieve audit data.
* Implement **webhooks** to listen for audit-related events and integrate updates into your systems.
