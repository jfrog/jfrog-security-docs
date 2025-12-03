# Quick Start

## **Modes of Operation**

The JFrog Plugin offers two modes: **Local** and **CI**. You can switch between them using the JFrog Panel tabs at the IDE's bottom.

### **Local View**

* Displays information about the local code as it is being developed in the IDE.
* Enables continuous scanning of your project with the JFrog Platform.
* Identifies security vulnerabilities in dependencies and source code before they become part of the final product.
* To scan your project, click the **Run Scan** button in the JFrog panel.

### **CI View**

* Tracks code as it is built, tested, and scanned by a CI server.
* Displays build status and includes a link to the CI server log.
* Provides security information about build artifacts and dependencies.
* Accessible through the **JFrog Panel > CI Tab**.

## Severity Icons

The plugin uses severity icons to indicate the highest severity issue within a selected component and its transitive dependencies.

| Icon                                                                                                                                                                                                                                                                                   | Severity       | Description                             |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------- | --------------------------------------- |
| ![](../../../../.gitbook/assets/Critical.png)                                                                                                                                                                                                                                          | Critical       | Issue with critical severity            |
| ![](../../../../.gitbook/assets/High.png)                                                                                                                                                                                                                                              | High           | Issue with high severity                |
| ![](../../../../.gitbook/assets/Medium.png)                                                                                                                                                                                                                                            | Medium         | Issue with medium severity              |
| ![](../../../../.gitbook/assets/Low.png)                                                                                                                                                                                                                                               | Low            | Issue with low severity                 |
| ![](../../../../.gitbook/assets/Unknown.png)                                                                                                                                                                                                                                           | Unknown        | Issue with unknown severity             |
| ![](../../../../.gitbook/assets/notApplicableCritical.png)![](../../../../.gitbook/assets/notApplicableHigh.png)![](../../../../.gitbook/assets/notApplicableMedium.png)![](../../../../.gitbook/assets/notApplicableLow.png)![](../../../../.gitbook/assets/notApplicableUnknown.png) | Not Applicable | CVE issue not applicable to source code |
| ![](../../../../.gitbook/assets/Normal.png)                                                                                                                                                                                                                                            | Normal         | No issues (used only in CI view)        |

## **How Does it Work?**

* The CI information displayed in the IDE is fetched from **JFrog Artifactory**.
* Build details are stored as **build-info**, published to Artifactory by the CI server.
* If **JFrog Xray** scans build-info, the plugin will display the scan results in the **CI View**.

## **Setting Up CI Integration**

Before the **CI View** can display data, configure your CI pipeline to expose build information:

1. Go to **Settings (Preferences) > Other Settings > JFrog Global Configuration**.
2. Configure your **JFrog Platform URL** and user credentials.
3. Navigate to **Settings (Preferences) > Other Settings > JFrog CI Integration**.
4. Set your CI **Build Name Pattern** – this should match the build name published to Artifactory.
   * Use `*` to view all builds published to Artifactory.
5. Click **Apply**, then open the **CI Tab** in the JFrog panel.
6. Click **Refresh** to fetch and display build details.
