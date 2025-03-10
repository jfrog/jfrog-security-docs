# Connect Remote Repositories to Curation

Administrators can select which remote repositories should be protected by the Curation service. Once curation has been activated for a particular repository, curation policies can be applied to the repository to prevent packages that violate the policy from being retrieved.&#x20;

Curation provides two options for connecting repositories:

* Connect Individual or Multiple Repositories – Manually select specific repositories for curation
* Connect by Package Type – Automatically curate all repositories associated with a specific package type.

{% hint style="info" %}
Curation can be used only on remote repositories that have a cache enabled (a minimum cache of 30 days is recommended).
{% endhint %}

### Manually Connect Curated Repositories

1. Navigate to **Administration** **→ Curation → Remote Repositories.**
2.  From the list select the Package Type of the repository/ies you want to curate.

    A list of all repositories of that type appears.
3. You can do one of the following:
   1. **Connect all current repositories**: This connects only all current repositories that appear in the list. To do this, click on the menu in the top right above the list and select **Connect All Repositories**.
   2. **Connect individual repositories**: This connects only specific repositories. To do this, turn on the **Connected**toggle that appears on the right of the repository row.

Automatically curate all repositories that match a specified package type (e.g., Maven, Docker, NPM) and ensure immediate coverage for newly created repositories without manual configuration.

Instead of manually selecting repositories to curate, you can now connect a package type. Once connected, Xray will:

* Automatically include all repositories of that package type in curation.
* Continuously monitor and curate new repositories as they are added
* Alert administrators if any repository is disconnected from curation.

### **Connect Repositories by Package Type**

Do the following:

1. Navigate to **Administration** **→ Curation → Remote Repositories.**
2. From the list select the Package Type you want to curate.
3.  Turn on the **Connect current and future** toggle that appears on the right of the package type row.

    This connects all current and future repositories of that package type.

You can turn the connection off for individual repositories within that package type anytime, as described in Manually Disconnect Curated Repositories. To send notifications when a repository is disconnected, see Manage General Notifications.

\
