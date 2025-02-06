# Builds Security Overview

The Builds Security Overview dashboard provides a centralized and comprehensive view of build versions, highlighting detected security issues and trends. This feature enables teams to aggregate and display security issues across different build versions, gain insights into security trends and vulnerabilities, and prioritize issues for effective remediation. With this dashboard, you can analyze trends, identify the most vulnerable components, and mitigate security risks effectively.

**Key features**

**Dashboard Overview**

The dashboard centralizes security data across build versions, providing an at-a-glance summary of critical issues and trends.

* Trend Visualization:
  * Interactive stacked bar chart displays issues across build versions.
  * Highlights increases and decreases in issue counts.
  * Hover tooltips show version-specific details
* Data Filtering Options:
  * Filter by issue types, including:
    * Active Violations: Security, license, and operational risks.
    * CVEs: Categorized by severity (Critical, High, Medium, Low).
    * Secrets: Hardcoded credentials and similar vulnerabilities.
  * Apply criticality filters (e.g., Critical, High) for targeted insights.
  * Filter by using a selected date range to focus on specific time periods and display vulnerabilities within that range only.
* Real-Time Updates: The graph dynamically adjusts based on selected filters.

**Reocurring Issues Tab**

* Identifies recurring issues across build versions.
* Sorting options:
  * By severity (Critical first).
  * By applicability.
  * By recurrence duration.

**New Issues Tab**

* Lists vulnerabilities unique to the selected build version.
* Sorting by criticality and applicability.

**Resolved Tab**

* Lists vulnerabilities that have been resolved in the selected version.

**Workflow**

Access Build Security Overview

1. Navigate to **Xray > Scans List**.
2. Select the **Builds** tab.
3. Choose a specific build.
4. View the **Overview** tab for detailed security information.

Dashboard Navigation

* Use filtering options to customize views.
* Click on bar chart elements to drill down into version-specific security details.
* Switch between Overview and Versions tabs for a broader or more detailed perspective.

Watch our video to explore this feature:

{% embed url="https://www.youtube.com/watch?embeds_referring_euri=https://jfrog.com/&source_ve_path=MjM4NTE&themeRefresh=1&v=VXo1CHUw1Vo" %}

