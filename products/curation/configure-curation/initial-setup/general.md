# General&#x20;

1. **Enable the Curation Service**:
   1. Log in to the JFrog Platform as an admin.
   2. Navigate to **Administration > Curation > General**.
   3. Toggle the **Curation** switch to "On."
2.  **Configure Notifications**:&#x20;

    Notification set here will be triggered on any package blocked/approved event in the system and will result in an email sent to the defined email addresses or the package requester's email. Note that one package blocked event might be due to one or multiple violated policies.

    1. In the **Administration** tab, select **Curation > General**:
       * **Notify Requester**: Sends a violation notification by email to the authenticated developer who attempted to download a package in violation of the policy. (This option does not support curated remote repositories that allow anonymous access.)
       * **Notify by Email**: Sends an email to additional addresses that you define, for example, your security officer.
3. **Set the Policy Engine Behavior**: \
   This setting determines how the system handles situations where a package is pending an update. This occurs when the system detects that a package used in your repositories requires an update, and the policy engine needs to decide what action to take. \
   Available options:&#x20;
   * **Block Always (Default)**: This is the default and most secure option. It ensures that any pending package update is blocked until the update is reviewed and allowed.&#x20;
   * **Allow if no blocking policy on remote**: This options allows pending updated to proceed only if no block policy exists on the remote repository.&#x20;
   * **Allow always**: This option allows all pending updates to proceed without any restrictions, regardless of the policy. \
     \


\








