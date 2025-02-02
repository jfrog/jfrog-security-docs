# Enable/Disable Scanning Categories

**Enable/Disable Scanning Categories**

The scanning categories are disabled by default. You can enable or disable each category separately as desired.

|                                                                                                                                                                                                                                                                                                                             | Note |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---- |
| The scanning categories are applied on new scans only, and not on existing indexed artifacts. The scan will run on indexed resources, however, it will not run on the Index Artifacts History. For more information, see [Indexing Xray Resources](https://www.jfrog.com/confluence/display/JFROG/Indexing+Xray+Resources). |      |

Note that in some cases, because deep scanning is involved, the scan might take longer to complete.

If you would like to enable the scanning categories, do the following:

1. Go to the **Administration** module, go to **Xray** **| Settings | General,** and click **Indexed Resources.**
2. Select the repository or build and select **Configure**.
3. Select the categories you want to enable: Vulnerability Contextual Analysis, Services, Secrets, and Applications.
