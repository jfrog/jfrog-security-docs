# How to Enable and Monitor SBOM Migration in Xray

**Use Case**

JFrog Xray's  **SBOM Service** manages scan results using an optimized data model for CVE search, SBOM generation, and impact analysis.\
This migration process transfers existing data to the new model seamlessly and runs in the background once enabled.

{% hint style="info" %}
This migration process is required only for Self-Hosted deployments.&#x20;
{% endhint %}

### **Workflow Steps**

#### **Step 1:  Verify Prerequisites**

Before enabling the SBOM service, ensure the following requirements are met:

* **Database:** PostgreSQL 10 or later
* **Disk Space:** At least 50% free
* **Database CPU:** Average usage under 60%
* **Xray Version:** 3.131.20 or later

Run the following query to confirm worker configurations:

```sql
select convert_from(config, 'UTF8') from configuration where config_id = 'xrayConfig';
```

Ensure the following worker keys are **not set to 0**:\
`sbom_workers, usercatalog_workers, sbom_enricher_workers, sbom_dependencies_workers, sbomimpactanalysis_workers, migrationsbom_workers`, and related `*_existing_content_workers` keys.

#### Step 2: Enable the SBOM Service

1. Edit the `system.yaml` file on **all Xray nodes**.
2.  Add the following configuration:

    ```yaml
    sbom:
      enabled: true
    ```
3. Restart all Xray nodes.

Once restarted, the migration begins automatically in the background.

#### Step 3: Monitor Migration Progress

**Check Overall Migration Status**

Run:

```sql
select * from sbom.migration_state;
```

This query returns:

* `root_files_to_migrate`: total number of root files to migrate
* `start_time`: migration start time
* `finished_time`: completion timestamp (or `NULL` if ongoing)
* `finished_state`: `FinishedSuccessful`, `StoppedByApi`, or `NULL`
* `count_all_migration`: total files migrated so far
* `count_failed`: failed root files
* `count_succeeded`: successfully migrated root files

**Check Status per Root File**

For debugging specific files:

```sql
select * from sbom.migration;
```

Each record includes:

* `root_file_id`, `status`, `retries`, and `last_err`
* Possible statuses: `Success`, `Fail`, `InProgress`, `FailedRetrying`, `ReadyForRetry`

#### Step 4: Control Migration via API

You can manage the migration process using the following endpoints:

All endpoints return **HTTP 200** on success.

| Action           | HTTP Method | Endpoint                                                  | Description                                                                                  |
| ---------------- | ----------- | --------------------------------------------------------- | -------------------------------------------------------------------------------------------- |
| Stop Migration   | `POST`      | `/api/v1/sbomMigration/stop`                              | Stops the migration process.                                                                 |
| Start Migration  | `POST`      | `/api/v1/sbomMigration/start?only_failures=[true\|false]` | Restarts the migration process. If `only_failures=true`, only failed root files are retried. |
| Pause Migration  | `POST`      | `/api/v1/sbomMigration/pause`                             | Pauses the running migration process.                                                        |
| Resume Migration | `POST`      | `/api/v1/sbomMigration/resume`                            | Resumes a paused migration process.                                                          |

#### Step 5: Troubleshooting

*   **Configuration values are 0**\
    Update the relevant worker counts in the configuration table.

    ```sql
    UPDATE configuration SET xrayConfig=<MODIFIED CONFIG>;
    ```
*   **Migration is too slow / not using DB resources**\
    Increase the number of migrant workers in `system.yaml`:

    ```yaml
    server:
      migrationSbomWorkers: 8
    ```
*   **Migration too fast / DB overloaded**\
    Reduce workers:

    ```yaml
    server:
      migrationSbomWorkers: 1
    ```

    Optionally, increase sleep intervals between artifact migrations:

    ```yaml
    sbom:
      sleepTimeSuccess: 5000000000
      sleepTimeFailed: 5000000000
    ```

Once the migration is complete, Xray operates using the new SBOM data model, improving performance for CVE search, dependency tracking, and impact analysis.
