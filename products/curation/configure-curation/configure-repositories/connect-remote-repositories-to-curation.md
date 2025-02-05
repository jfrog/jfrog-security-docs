# Connect Remote Repositories to Curation

Administrators can select which remote repositories should be protected by the Curation service. Once curation has been activated for a particular repository, curation policies can be applied to the repository to prevent packages that violate the policy from being retrieved.

{% hint style="info" %}
Curation can be used only on remote repositories that have a cache enabled (a minimum cache of 30 days is recommended).
{% endhint %}

Do the following:

1. Log in to the JFrog Platform.
2. Navigate to **Administration > Curation > Remote Repositories**.
3. Locate the repository type in the list and toggle the **Activity** switch to Connect curation.
4. You can connect by typing "one by one." To do so, click on Type and select the desired repositories.&#x20;
5. Connecting "Type" will ensure all future repositories are connected as well.&#x20;
6. The connected type also ensures that any disconnected repository will be notified by email to the stake holders.&#x20;
