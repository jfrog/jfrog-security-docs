# Upgrade Xray with Operational Risk Feature Support in Offline Mode

If you are working in an offline mode, you need to manually sync the database to download components data and enable Operational Risk detection.

Do the following:

1. In the **Administration** module, go to **Xray Security and Compliance** and select **Database Sync.**
2. Select the **Offline** sync mode and click **Generate Download Command.**
3.  A command is generated similar to this:

    ```
    jfrog xr offline-update --license-id=<LICENSE_ID> --version=<XRAY_VERSION>
    ```

    ⧉
4. If the command includesFromandToparameters, remove them so the command looks like the example above.
5. Copy the command and run it in the CLI.
6. The CLI will download 2 files: comp\_0.zip and vuln\_0.zip
7. Unzip the components file, for example, comp\_{NUMBER}.zip. It contains additional zip files such as:
   1. 2022-03-22\_\_onboardingf\_\_comp2801\_2803\_\_.zip
8.  Place the extracted components zip files under the following folder in Xray server.

    ```
    ${XRAY_HOME}/var/work/server/updates/data_migration/public_comps_operational_risk_files/
    ```

    ⧉
9.  Trigger the components operational risk persistence migration:

    ```
    [post] <XRAY_URL>/api/v1/migration/trigger/public_comps_operational_risk

    Content-Type : application/json
    ```

    ⧉
10. Use the migration values REST API to monitor the operational risk migration process. To learn more about running Xray commands, see [Xray REST API](https://jfrog.com/help/access?ft:clusterId=UUID-31c8b6b1-2d07-5418-5805-254fd4a703bc).

    Once the migration is completed, the migration status will be set to finished. In case of any other status that contains failure information, check the logs and or contact JFrog's customer support.

    ```
    [GET] <XRAY_URL>/api/v1/migration/data/value?key=public_comps_operational_risk
    ```

    ⧉

    Sample Response:

    ```
    {
       "key": "public_comps_operational_risk",
       "value": "finished"
    }
    ```

    ⧉

\
