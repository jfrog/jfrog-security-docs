# Initiate Advanced Scans

When you enable Advanced Security for the first time, existing repositories and artifacts in Artifactory are **not** scanned automatically. You must manually trigger scans for the repositories and artifacts you want to analyze.

Once advanced scans are set up, they apply **only to newly added artifacts** and run as **ongoing, recurring scans**. However, you can also trigger **one-time scans** for an immediate, on-demand security analysis of your artifacts, containers, or codebases without waiting for scheduled scans.

The [Repositories](repositories.md) and [Artifacts](artifacts.md) guides explain how to initiate and configure both **ongoing** and **one-time** advanced scans to detect:

* **Vulnerabilities through Contextual Analysis**
* **Service risks**
* **Secrets exposure**
* **Application security issues**

The following REST APIs support Advanced Security Repository and Artifact actions:

* [Repository Advanced Scans](https://jfrog.com/help/access?ft:clusterId=UUID-89c102f9-5e9b-ac33-f0c6-4c6d91909666)
* [Get Repository Advanced Scan Status](https://jfrog.com/help/access?ft:clusterId=UUID-a7e9acd3-cda9-baa7-d2cd-ffe120dc7b78)
* [Cancel Repository Advanced Scans](https://jfrog.com/help/access?ft:clusterId=UUID-319eb7e1-2ba3-7958-14e1-b1cf21b001c6)
* [Scan Artifact for Contextual Analysis](https://jfrog.com/help/access?ft:clusterId=UUID-1894543d-8403-a343-52ae-3349b744d86d)
* [Scan Artifact for Exposures](https://jfrog.com/help/access?ft:clusterId=UUID-ded1b0b1-80db-33f8-141c-5e0644c19627)

