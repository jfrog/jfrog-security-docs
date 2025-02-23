# Quick Start

## Enable Advanced Scans for a Repository

Advanced Scans apply only to newly added artifacts in the repository and run as ongoing, recurring scans. They are configured per repository and do not apply to existing artifacts.

1. In Classic Navigation, go to **Administration** > **Xray Settings** > **General** > **Indexed Resources**.
2. In New Navigation, go to **Administration** > **Xray Settings** > **Indexed Resources**.
3. Select the repository or build and click **Configure**.\
   The **Scans Configuration** window opens.
4. Under the **Advanced Security** category, select all or some of the following scans:

* **Vulnerabilities Contextual Analysis**
* **Services**
* **Secrets**
* **Applications**

5. Under **Scope**, select:

* **Scan all artifacts** to scan all artifacts currently present in the repository
* **Scan by pattern** defines a specific path within the repository

6. If you select **Scan by pattern**, you will be able to manage advanced scans for specific artifacts within the repository, by:

* Setting path patterns&#x20;
* Setting data retention period
* Toggling **Scan** on&#x20;
* Configuring **All other Artifacts** within the repository that are excluded from the defined scan patterns with a data retention period of their own.&#x20;

## Trigger One-Time Advanced Scans

Triggering one-time advanced scans is useful in scenarios where you need to perform an immediate, on-demand security analysis of your artifacts, containers, or codebases without waiting for scheduled scans.

1. In Classic Navigation, go to **Administration** > **Xray Settings** > **General** > **Indexed Resources**.
2. In New Navigation, go to **Administration** > **Xray Settings** > **Indexed Resources**.
3. Select a repository or build and click **Advanced Scans**.\
   The **Advanced Scans** window opens.
4. Under **Select Date and Pattern** > **Date** and **Pattern**:

* Choose **Deployed in** to scan artifacts that were deployed to Artifactory within a specified time range
* Choose **Downloaded in** to scan artifacts that were downloaded from Artifactory within a specified time range
* Choose **Any time** to scan all artifacts currently present in the repository
* Add path pattern (wildcard patterns for repository artifact paths should be specified **without a leading slash**. The system supports **Ant-style path expressions**, including `*`, `**`, and `?)`

5. Under Select Scan Categories, select all or some of the following scans:
   * **Secrets**
   * **Services**
   * **Applications**
   * **Vulnerabilities Contextual Analysis**

## Create a Security Policy with Advanced Scan Rules

Security policies enable you to define rules based on security criteria, with automatic actions triggered according to your needs. These policies are enforced when applied to Xray Watches. For guidance on creating policies, see _Creating Xray Policies and Rules_.

It is recommended to create policies for a focused list of violations based on your security criteria. You can create policies specific to exposures and contextual analysis rules. A violation is issued when the criteria set in the policy are met. Violations can be viewed on either the _Scans List_ or _Watch Violations_ pages.

###
