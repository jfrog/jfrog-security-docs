# Quick Start

## **Modes of Operation**

The JFrog VS Code Extension offers two modes: **Local** and **CI**. You can switch between them using the respective buttons next to the components tree.

### **Local View**

* Displays information about the local code as it is being developed in VS Code.
* Enables continuous scanning of your workspace.
* Shows security vulnerabilities in dependencies and source code before they become part of the final product.
* To scan your workspace, click the **Scan/Rescan** button in the extension tab or select **Start Xray Scan** from the editor.

### **CI View**

* Tracks code as it is built, tested, and scanned by a CI server.
* Displays build status and includes a link to the CI server log.
* Provides security information about build artifacts and dependencies.
* Accessible through the JFrog Panel after switching to CI mode.

## **Severity Icons**

| Icon                                                                                                                                                                                                                                                                                   | Severity       | Description                             |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------- | --------------------------------------- |
| ![](../../../../.gitbook/assets/Critical.png)                                                                                                                                                                                                                                          | Critical       | Issue with critical severity            |
| ![](../../../../.gitbook/assets/High.png)                                                                                                                                                                                                                                              | High           | Issue with high severity                |
| ![](../../../../.gitbook/assets/Medium.png)                                                                                                                                                                                                                                            | Medium         | Issue with medium severity              |
| ![](../../../../.gitbook/assets/Low.png)                                                                                                                                                                                                                                               | Low            | Issue with low severity                 |
| ![](../../../../.gitbook/assets/Unknown.png)                                                                                                                                                                                                                                           | Unknown        | Issue with unknown severity             |
| ![](../../../../.gitbook/assets/notApplicableCritical.png)![](../../../../.gitbook/assets/notApplicableHigh.png)![](../../../../.gitbook/assets/notApplicableMedium.png)![](../../../../.gitbook/assets/notApplicableLow.png)![](../../../../.gitbook/assets/notApplicableUnknown.png) | Not Applicable | CVE issue not applicable to source code |

## **Setting Up Your CI Pipeline**

Before the CI View can display data, the CI pipeline must be configured correctly. Follow the guide on how to configure your CI pipeline to expose this data.

### **Setting Up the CI View**

1. In **Extension Settings**, set the **Build name pattern** to match the build name published to Artifactory.
2. Use `*` to view all builds published to Artifactory.
3. After fetching builds from Artifactory, click the **Builds** button to select which build to display.
