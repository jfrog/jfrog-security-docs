# How to Exclude Specific File Names from Scans

1.  Set file names to exclude by adding the following flag in the [Xray system.yaml](https://jfrog.com/help/r/jfrog-installation-setup-documentation/xray-system-yaml) file, specifying the file names you want to exclude (separated by a pipe \`|\`):&#x20;

    ```plaintext
    indexer:
       ignoreFileNamesIndexing: "file1.jar|file2.jar|file3.jar"
    ```
2. After updating the configuration, restart the Xray pods to apply the changes.
3. Force reindex previously scanned artifacts. The specified files will now be excluded from scanning.

