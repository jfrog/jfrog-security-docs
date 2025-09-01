# General&#x20;

General configuration tasks required for JFrog Curation.

**Step 1: Enable the Curation Service**:

1. Log in to the JFrog Platform as an admin.
2. Navigate to **Administration > Curation > General**.
3. Toggle the **Curation** switch to "On."

**Step 2: Configure Notifications**:&#x20;

Notifications set here will be triggered on any package blocked/approved event in the system and will result in an email sent to the defined email addresses or the package requester's email. Note that one package blocked event might be due to one or multiple violated policies.

1. In the **Administration** tab, select **Curation > General**:
   * **Email Package Requester on Blocked Events**: Sends a violation notification by email to the authenticated developer who attempted to download a package in violation of the policy. (This option does not support curated remote repositories that allow anonymous access.)
   * **Email Package Requester on Dry Run Events**: Sends a dry run violation notification every hour by email to the authenticated developer who attempted to download a package in violation of the policy. (Aggregated email every 60 min)
   * **Notify the Email List Regarding Blocked/Dry Run EvAggregatedents**: Sends an email daily at 8:00 local time for dry runs and blocked packages.to additional addresses that you define, for example, your security officer. &#x20;
   * **Notify the email list regarding disconnected repositories**: Sends an email when a repository is disconnected from Curation.&#x20;

**Step 3: Configure Webhooks:**

Create tickets or notifications from the system if there is a blocking action in the audit using[ Webhooks ](https://jfrog.com/help/r/jfrog-platform-administration-documentation/webhooks)events. Whenever a curation process encounters a blocked package, an event is triggered and sent to the designated webhook.

The event includes comprehensive details about the blocked package, such as:

* **Package Information**: Identifying details of the package that was requested.
* **Requester Details**: Information on the user or entity that requested the package.
* **Policy Violation**: A description of the specific policy violation that resulted in the blocking of the package.

**Step 4: Set the Policy Engine Behavior**: \
This setting determines how the system handles situations where a package is pending an update. This occurs when the system detects that a package used in your repositories requires an update, and the policy engine needs to decide what action to take. \
Available options:&#x20;

* **Block Always (Default)**: This is the default and most secure option. It ensures that any pending package update is blocked until the update is reviewed and allowed.&#x20;
* **Allow if no blocking policy on remote**: This options allows pending updated to proceed only if no block policy exists on the remote repository.&#x20;
* **Allow always**: This option allows all pending updates to proceed without any restrictions, regardless of the policy.&#x20;

**Step 5: CLI configuration**: \
Instal JF CLI to receive a full curation developer experience.\
JF CLI supports the Curation **JF CA** command, which inspects the blocked package and provides the developer with blocking reasons and suggestions. Some package types need a pass-through mechanism to enable the JF CA command. &#x20;

**Step 6: Curation Pass-Through**:

Enable package downloads for audit purposes without storing them in Artifactory. Ensures violating packages are only temporarily accessible for evaluation without impacting the repository cache.\






