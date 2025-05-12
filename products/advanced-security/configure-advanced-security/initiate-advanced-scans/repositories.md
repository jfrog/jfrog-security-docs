# Repositories

### Enable Advanced Scans for a Repository

Advanced Scans apply only to newly added artifacts in the repository and run as ongoing, recurring scans. They are configured per repository and do not apply to existing artifacts.

1. Navigate to **Administration** > **Xray Settings** > **Indexed Resources**.\
   Alternatively, navigate to **Applications** > **Xray** > **Scans List**.
2. Select a repository or build and click **Configure**.\
   The **Scans Configuration** window opens.
3. Under the **Advanced Security** category, select all or some of the following scans:

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

### Trigger a One-Time Advanced Scan for a Repository

Triggering one-time advanced scans is useful when you need to perform an immediate, on-demand security analysis of your artifacts, containers, or codebases without waiting for scheduled scans.

{% hint style="info" %}
Results from one-time scans are kept for 7 days.
{% endhint %}

1. Navigate to **Administration** > **Xray Settings** > **Indexed Resources**.\
   Alternatively, navigate to **Applications** > **Xray** > **Scans List**.
2. Select a repository or build and click **Advanced Scans**.\
   The **Advanced Scans** window opens.
3.  Under **Select Date and Pattern** > **Date** and **Pattern**:



* Choose **Deployed in** to scan artifacts that were deployed to Artifactory within a specified time range
* Choose **Downloaded in** to scan artifacts that were downloaded from Artifactory within a specified time range
* Choose **Any time** to scan all artifacts currently present in the repository
* Add path pattern (wildcard patterns for repository artifact paths should be specified **without a leading slash**. The system supports **Ant-style path expressions**, including `*`, `**`, and `?`)

5. Under Select Scan Categories, select all or some of the following scans:
   * **Secrets**
   * **Services**
   * **Applications**
   * **Vulnerabilities Contextual Analysis**
