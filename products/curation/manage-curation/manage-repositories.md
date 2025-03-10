# Manage Repositories

#### Overview of Repository Management

* Upon accessing the Remote Repository page under **Administration > Curation Settings > Remote Repositories**, you will see two main sections:
  * Overview Section (Upper Section):
    * On the left side, you will find a summary of the current states of all your repositories categorized into Connected and Not Connected repositories.
    * On the right side, a trend graph may display how repository connections have changed over time (it takes two months to start generating a trend)&#x20;

#### Understanding Connected vs. Not Connected Repositories

* **Connected Repository**: When a repository is connected, it indicates that JFrog Curation can start governing that repository. However, it does not imply that the repository is currently under the governance of a policy.
* **Not Connected Repository**: Any repository that is not connected will not be governed by Curation policies.

#### Step 4: Viewing Package Types

* Below the overview section, you will see a table listing the different **Package Types** present in your organization.
* When you connect a specific Package Type, all repositories under that package type are automatically connected to Curation.
* This ensures that once a package type is connected, all NEW associated repositories automatically receive governance coverage.

#### Step 5: Connecting or Disconnecting Repositories

Disconnecting Repositories: If you want to remove one or more repositories from a package type:

1. Click on the package type name to view the full list of associated repositories.
2. From this list, select the repositories you wish to disconnect.
3. Confirm the disconnection process as prompted.
4. Bulk action is available in the right corner of the table by clicking the three dots.&#x20;

#### Notifications on Disconnection

When repositories are disconnected from a connected package type, an email notification will be sent to the designated state folder informing relevant parties of the disconnection. This ensures that stakeholders are updated on changes in repository governance.
