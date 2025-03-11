# Set a Retention Period for Xray Indexed Resources

As Xray's indexed resources are retained in the system, this can result in large amounts of data being stored, impacting your storage and causing performance issues. Starting from Xray version 3.41.4, you can set retention periods for repositories and builds. The retention period defines how long Xray will retain artifact scan data, and after the set retention period, this data is deleted, thus improving performance and freeing up storage space. The default period is 90 days. You can change the default period using the `server.repo.defaultRetentionDaysForIndexedRepo` in the Xray System YAML.

Note

> The retention period is reset to the beginning of the configured retention once an artifact is downloaded.

## Set Retention Period in UI

### Set Retention Period for Repositories

To set the retention period for a repository, do the following:

1. In the **Administration** module, go to **Xray Settings** and click **Indexed Resources**.
2. Select the repository or multiple repositories and select **Configure**.
3. Select one of the following:
   *   **Any artifact from the last number of days**: The artifact will be retained for the number of days you set here, after it is scanned. This will apply to all artifacts in the repository.


   * **Scan all Artifacts**: This applies only to the selected subset of future artifacts uploaded to the repository.
   *   **Scan By Pattern**: This option enables you to set a more granular retention period by scanning future artifacts within a specific path, and setting a retention period for the historical data of artifacts after they are scanned. This applies only to the subset of future artifacts uploaded to the repository.

       * **Scan**: If checked, Xray will scan newly added artifacts in the path. Note that existing artifacts will not be scanned. If the folder contains existing artifacts that have been scanned, and you do not want to index new artifacts in that folder, you can choose not to index that folder.
       * **Retention period**: The number of days to retain artifact data after they are scanned by Xray.

       For example, if you have a repository that contains all of your artifacts, you can set a retention period for artifacts within a folder in the repository. Let's assume your repository contains a production folder, and you would like to set a retention period for artifacts within that folder. You can provide the path to that folder as an include pattern and set the retention period. If that folder also contains other folders that you do not want to be scanned or retained, you can exclude them using the exclude pattern.

#### Notes

> Patterns are set using simple comma-separated wildcard patterns for repository artifact paths (with no leading slash). Ant-style path expressions are supported (`*`, `**`, `?`). For example: `"org/apache/**"`

> Patterns are limited to 10 patterns per repository. If you select by pattern, you must define a retention period for all other artifacts in the repository in the **All Other Artifacts** setting.

### Set Retention Period for Builds

To set the retention period for a Build, do the following:

1. In the **Administration** module, go to **Xray Settings** and click **Indexed Resources**. Select the **Builds** tab.
2. Select the build and select **Configure**.
3. Set the retention period. The default is 15 days.

## Set Retention Period Using REST API

Repository Configuration is also supported through the following REST APIs:

* Update Repositories Configurations
* Get Repositories Configurations
* Scans List - Get Release Bundle V2 Versions
* Release Bundle V2 Details

## Set Retention Period Using `System.yaml`

The following table lists all the configuration system parameters that support Xray Data Retention:

| System Parameter                                      | Description                                                           | Default Value |
| ----------------------------------------------------- | --------------------------------------------------------------------- | ------------- |
| `server.repo.maxRetentionDaysLimit`                   | Max limit of retention period for artifacts in a repository.          | 1000          |
| `server.repo.maxRepoPathsPatternsAllowed`             | Max limit of number of patterns in repository paths per repository.   | 10            |
| `server.repo.defaultRetentionDaysForIndexedRepo`      | Default retention period for artifacts of an index repository.        | 90            |
| `server.repo.defaultRetentionDaysForNonIndexedRepo`   | Default retention period for artifacts in a non-indexed repository.   | 3             |
| `server.disableXrayDataCleanupJob`                    | Disable data cleanup.                                                 | FALSE         |
| `server.build.defaultRetentionDaysForIndexedBuild`    | Default retention period for indexed builds.                          | 15            |
| `server.build.defaultRetentionDaysForNonIndexedBuild` | Default retention period for builds that are not marked for indexing. | 3             |
