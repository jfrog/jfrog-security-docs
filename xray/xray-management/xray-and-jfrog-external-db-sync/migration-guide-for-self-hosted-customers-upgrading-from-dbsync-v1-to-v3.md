# Migration Guide for Self-Hosted Customers: Upgrading from DBSync V1 to V3

In today’s rapidly evolving threat landscape, vulnerabilities are emerging faster than ever, making the security of your software supply chain increasingly critical. That’s why we’ve launched DBSync Version 3 (DBSync v3)—a faster, more reliable way to update threat intelligence across JFrog security products, ensuring you stay ahead of the latest risks.

This guide is designed for users running **on-premise** or **self-hosted** installations of Artifactory and Xray. If you newly deployed an on-premise version of Artifactory and Xray in 2024, chances are you're already using DBSync v3. \
**Note:** If you are using the **SaaS** version of JFrog Xray and Artifactory, you can disregard this documentation, as the latest version of DBSync is already in use.

DBSync is the protocol used to update the JFrog Catalog and Vulnerability Database in JFrog Xray. We strongly recommend that on-premise or self-hosted customers migrate to the latest DBSync v3 as soon as possible to ensure timely threat intelligence updates. DBSync v3 is enabled by default for all **new** on-premise installations starting with version 3.80. Please note that **DBSync v1 will reach end of life in mid-2025.**

For customers, who have deployed on-premise installation of Xray before 2024, you will need to manually migrate to DBSync v3 as outlined in the steps below.

**How to Check Your DBSync Version?**

Run the following command to identify your current DBSync version:

```
curl -s -u<user:password> -H 'Content-Type: application/json' 'https://<instance-host-or-ip>/xray/ui/features' | jq | grep -i dbsync
```

**Output Examples:**

* `<blank>`: You are running DBSync v1 and need to migrate.
* `"FeatureDBSyncV3"`: You are already on the latest version; no action is required.

#### How to Migrate to DBSync v3? <a href="#uuid-3f10111b-8c7f-2e6a-868f-f13baa7126cc_bridgehead-idm234675016418531" id="uuid-3f10111b-8c7f-2e6a-868f-f13baa7126cc_bridgehead-idm234675016418531"></a>

Before you get started with the migration, please note the following:

1. **It is recommended that during migration the number of nodes be** [**reduced to 1**](https://jfrog.com/help/r/jfrog-installation-setup-documentation/xray-ha-upgrade)**.**
2. Initiate the DBSync v3 migration during **off-peak hours**, such as weekends or holidays, to ensure the system is not under heavy load.
3. The migration process takes approximately **2 to 4 hours** to complete.
4. Xray remains fully operational during the migration, with no downtime.
5. A complete backup of the original data is created, allowing for restoration if needed.
6. The database system requires a minimum of **200 GB** of disk space for the migration. This space will be used to store the old database backup and update it with the new DBSync v3 threat intelligence.
7.  Make sure to configure the Xray database to use the public schema during the migration.

    After migration, you can change the schema ownership as needed.
8. **Warning**: Custom vulnerabilities you’ve created, with vulnerability IDs starting with "XRAY-" and the provider set to JFrog, will be lost during migration. It is unlikely that you have created custom issues with IDs beginning with "XRAY-". All other custom issues are migrated.\
   \
   As a precaution during the migration, if numerous vulnerabilities are detected, the migration may fail with a notification regarding custom vulnerabilities or components. If this occurs, contact [JFrog Support](mailto:support@jfrog.com) for assistance.
9. **Rare case:** If you are still using the deprecated 3rd-party threat feed, please note that these will not be migrated.

#### Steps to Migrate to DBSync v3 <a href="#uuid-3f10111b-8c7f-2e6a-868f-f13baa7126cc_bridgehead-idm234675017249971" id="uuid-3f10111b-8c7f-2e6a-868f-f13baa7126cc_bridgehead-idm234675017249971"></a>

1.  Initiate the Migration from the admin console

    If you are running version 3.107 LTS with patch 18 then you will see an informational message in “Scans List” asking you to upgrade to DBSync v3. Please click on this link

    Optionally, you can directly navigate to the migration screen from “**Administration**” tab-> **Xray Settings** and then click on **Database Sync**.
2.  Select the "**Online**" option and click "**Migrate**" when ready.

    For offline upgrades in air-gapped networks, follow the steps provided on the pop-up screen
3. On the pop-screen, please read the “Migration Details" and click on the “Migrate” button
4. You should now see the upgrade status displayed on the screen.
5.  After the migration is complete, upload a test artifact and scan it with Xray to verify that the functionality is working properly.

    The **DBSync Implementation** status is now **V3.**<br>
