# Create Policies

Curation is based on a set of defined policies. To create a new curation policy, the Curation Admin must choose the remote repositories to which the policy applies, the policy condition (only 1 condition can be defined for each policy), and the action to be performed when the policy is violated. In addition, any exceptions to the policy can be defined in a waiver.

{% hint style="info" %}
This is a basic procedure outlining the steps to create a policy. In the [How-Tos ](../../how-tos.md)section we provide more scenario specific procedures for creating policies.&#x20;
{% endhint %}

Do the following:

1. Go to **Administration > Curation > Policies Management**.
2. Click **Create Policy** and follow the wizard:
   * **Step 1**: Enter a name for the policy (max 50 characters, no special symbols).
   * **Step 2**: Define the scope:
     * **All Curated**: Applies to all curated repositories (optionally exclude specific repositories).
     * **Specific**: Select a single curated repository.
   * **Step 3**: Choose a condition from the predefined or custom options. For a full detailed list of the conditions, see [here.](list-of-available-conditions.md) Examples:
     * Block based on CVSS score thresholds.
     * Block non-official Docker images.
     * Block packages not labeled as "allowed."
   * **Step 4** (optional): Add waivers to exclude specific packages or versions.
   *   **Step 5**: Define the action (Block or Dry Run) and configure email notifications.



