# Audit Events

## Guide to Curation Audit in JFrog Curation

Curation Audit provides visibility and transparency into the package governance process, allowing users with curation permissions to understand how packages are managed within your organization. This guide outlines the sections of the Curation Audit, how to interpret the data, and how to export audit results.

### Overview of Curation Audit Sections

The Curation Audit feature is divided into three main sections:

1. **Blocked and Approved Packages**
2. **Dry Run**
3. **User Actions**

#### Section 1: Blocked and Approved Packages

* This section displays all packages processed through the curation policies.

**Blocked Packages**

* Here, you'll find a list of all packages that have been blocked due to policy violations. For each blocked package, you can:
  * **View Reasons for Blocking** : Get insights into the specific policies that were violated.
  * **Drill Down for Details** : Click on any blocked package to see an exact explanation of the violation and specific recommendations. This may include links to fixed versions if available.

**Approved Packages**

* This list contains packages that successfully passed through the curation process. You may notice:
  * **Bypass Indicators** : If a package appears as "bypassed", it indicates that the package should have been blocked due to a policy violation but was allowed through because of relaxed conditions. For more information on relaxed conditions, refer to the respective section in your curation settings.

#### Section 2: Dry Run

* The Dry Run section simulates what would happen if a particular policy were applied without actually blocking any packages. This provides valuable data on:
  * **Understanding Policy Impact** : You can see which packages would have been blocked if the policy were active.
  * **No Real Impact on developers**: Note that the Dry Run does not create any real blockage; it merely serves as a predictive tool to help users assess the implications of changes to policies.

#### Section 3: User Actions

* This section logs all user interactions within the curation interface, including:
  * **Changing Policies**
  * **Removing or Editing Repositories**
  * **Managing Conditions**
* This log helps track governance actions taken by users, providing transparency and accountability.

#### Exporting Audit Data

* You can export the data from both the Dry Run and Blocked/Approved Packages sections into a CSV format:
  1. Locate the **Export** button in the top right corner of the Curation Audit screen.
  2. Click on it to initiate the export process.
  3. The export will generate a CSV file containing only the data currently visible on the screen, filtered by any criteria you have applied.
  4. API and Webhooks are also available and described in the API section.&#x20;
