# Initiate Advanced Scans

When you enable Advanced Security for the first time, existing repositories and artifacts in Artifactory are not scanned automatically. You must manually trigger scans for the repositories and artifacts you want to analyze.

Once advanced scans are set up, they apply only to newly added artifacts and run as ongoing, recurring scans. However, you can also trigger one-time scans for an immediate, on-demand security analysis of your artifacts, containers, or codebases without waiting for scheduled scans.

The [Repositories](repositories.md) and [Artifacts](artifacts.md) guides explain how to initiate and configure both **ongoing** and **one-time** advanced scans to detect:

* **Vulnerabilities through Contextual Analysis**
* **Service risks**
* **Secrets exposure**
* **Application security issues**

The following REST APIs support Advanced Security Repository and Artifact actions:

* [Repository Advanced Scans](https://jfrog.com/help/r/xray-rest-apis/repository-advanced-scans/)
* [Get Repository Advanced Scan Status](https://jfrog.com/help/r/xray-rest-apis/get-repository-advanced-scan-status)
* [Cancel Repository Advanced Scans](https://jfrog.com/help/r/xray-rest-apis/cancel-repository-advanced-scans)
* [Scan Artifact for Contextual Analysis](https://jfrog.com/help/r/xray-rest-apis/scan-artifact-for-contextual-analysis)
* [Scan Artifact for Exposures](https://jfrog.com/help/r/xray-rest-apis/scan-artifact-for-exposures)
