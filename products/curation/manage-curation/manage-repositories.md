# Manage Repositories

### Steps to Manage Repositories

#### Step 1: Access the Remote Repository Page

1. **Log in** to your JFrog platform.
2. Navigate to the **Administration** panel in the main menu.
3. Go to **Curation Settings** and then select **Remote Repositories**.

#### Step 2: Overview of Repository Management

* Upon accessing the Remote Repository page, you will see two main sections:
  * **Overview Section (Upper Section)**:
    * On the **left side**, you will find a summary of the current states of all your repositories categorized into **Connected** and **Not Connected** repositories.
    * On the **right side**, a trend graph may display how repository connections have changed over time (it takes two months to start generating a trend)&#x20;

#### Step 3: Understanding Connected vs. Not Connected Repositories

* **Connected Repository**: When a repository is connected, it indicates that JFrog Curation can start governing that repository. However, it does not imply that the repository is currently under the governance of a policy.
* **Not Connected Repository**: Any repository that is not connected will not be governed by Curation policies.

#### Step 4: Viewing Package Types

* Below the overview section, you will see a table listing the different **Package Types** present in your organization.
* When you connect a specific **Package Type**, all repositories under that package type are automatically connected to Curation.
* This ensures that once a package type is connected, all NEW associated repositories automatically receive governance coverage.

#### Step 5: Connecting or Disconnecting Repositories

1. **Disconnecting Repositories**: If you want to remove one or more repositories from a package type:
   * Click on the package type name to view the full list of associated repositories.
   * From this list, select the repositories you wish to disconnect.
   * Confirm the disconnection process as prompted.
   * Bulck action is available in the right corner of the table by clicking the three dots.&#x20;

#### Step 6: Notifications on Disconnection

* When repositories are disconnected from a connected package type, an email notification will be sent to the designated state folder informing relevant parties of the disconnection. This ensures that stakeholders are updated on changes in repository governance.
