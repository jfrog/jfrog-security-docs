# System Messages

Xray administrators can view a list of all artifact and data failure messages in Failure Messages and Retry Messages tab in the System Messages page, under the Administration module. Each failure can be traced to the exact step in the **scanning** and **impact analysis** Xray process in which it failed, allowing administrators to fix the issue and retry the step or contact JFrog support for further investigation.

#### Scanning <a href="#bridgehead-idm4556731675457633995429116136" id="bridgehead-idm4556731675457633995429116136"></a>

Every time a new artifact or build is added, Xray scans it and its dependencies for known vulnerabilities and compliance violations and generate Issues accordingly. This process is called "Scanning". That includes the following process steps:

* Check All
* Index
* Persist
* Analysis
* Alert
* Notify
* Artifactory Update

#### Impact Analysis <a href="#bridgehead-idm451653100083843399542973565" id="bridgehead-idm451653100083843399542973565"></a>

Every time new component metadata is available (vulnerabilities, licenses, etc.), Xray looks up the component in the components graph and if the update matches any watches, Xray will generate an issue and create a map of its impact to determine which artifacts are ultimately affected by it. This process is called "Impact Analysis". That includes the following process steps:

* Analysis
* Alert
* Notify
* Artifactory Update

### View Xray Failure Messages

| Field     | Description                                                                                                                                                                                                                               |
| --------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Subject   | The name of the failed artifact being scanned by Xray, or the data update in case of an impact analysis, such as vulnerability and license name.                                                                                          |
| Source    | The location of the artifact being scanned by Xray (including the instance name, repo name and path within the repo), or the source of the data update in case of impact analysis (including the database sync or custom issue assigned). |
| Step      | The step in which the artifact failed (including the process and step name).                                                                                                                                                              |
| Timestamp | The time in which the failure occurred. By default, the grid will be sorted from newest failure to oldest.                                                                                                                                |
| Error     | The detailed error message describing what caused this failure.                                                                                                                                                                           |

### **View Xray Retry Messages**

Displays the number of retry messages generated for selected processes.\
