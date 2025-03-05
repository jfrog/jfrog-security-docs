# Ticket Status

### Ticket Status

**Note:** Available from Xray version 3.112.3 and above.

Customers utilizing the Xray Jira Integration can now view the statuses of Jira tickets created through the integration directly within the JFrog platform.

**Periodic Ticket Retrieval**

The ticket statuses will be periodically retrieved from the Jira instance to Xray every 8 hours and displayed in the UI under the Ticket Status column.

![](<../../../../../.gitbook/assets/0 (3).png>)

**Manual Ticket Retrieval**

By default, the ticket statuses will be retrieved periodically (every 8 hours) to ensure minimal divergence between the JFrog platform and Jira. However, if the user wishes to see the current status of tickets, they may do so for tickets created for a particular violation of an artifact.

1. Under the Xray Scans List page, click on the resource of interest. It can be an artifact, build or a release bundle.
2. Go to the Policy Violations page and select the violation for which you want to retrieve the status.
3. Under the Tickets Info tab, click on the refresh button. The statuses for all the tickets associated with the violation would be refreshed and shown in the UI.

![](<../../../../../.gitbook/assets/1 (3).png>)

**Enable / Disable the ticket retrieval feature**

For customers who have Jira Integrations created after Xray version 3.112, this feature would be enabled by default for all instances and authentication types.

Customers who already have a Jira Integration enabled and upgrading to a version at or after 3.112 would have it enabled by default. The exception to this are customers who are using the Jira Integration with a Jira Cloud instance using OAuth2 authentication. Please refer to the section “Enabling for OAuth2 on Jira Cloud” on how to enable for them.

If you want to enable / disable the feature:

1. Under Administration, go to Xray Settings > Integrations and select the integration for which you want to toggle the feature.
2. Click on the menu button on the right-hand side and click on Settings.\
   The settings window should appear
3. Click on the “Retrieve Jira Tickets” toggle to select the state of the toggle.
4. Click Apply.

Please note that the changes would take some time to reflect in the UI. If the feature is enabled, it would take some time for the statuses to refresh in the UI as Xray would retrieve all the ticket statuses from Jira. Similarly when disabled, the status data would take some time to disappear from the UI.

**Enabling for OAuth2 on Jira Cloud**

For customers who have a Jira integration created on Jira Cloud with OAuth2 prior to version 3.112 and upgrading to any version at or after that, the feature would be disabled by default.

To enable , do the following:

1. In the Atlassian developer console:
   1. Go to the Jira Developer console and select the OAuth2 Application using which the Jira Integration was created.
   2. Under Permissions \&gt; Granular scopes, include the following additional scopes.\
      read:issue-details:jira\
      read:field.default-value:jira\
      read:field.option:jira
2. In the JFrog platform:
   1. Under Administration, go to Xray settings \&gt; Integrations and select the integration for which the scopes were added.
   2. Click on the menu button (ellipsis) in the right hand side and select “Edit Integration”.
   3. Complete the wizard in a similar way to how an Integration is created. For this case, only the Secret Key from the Atlassian platform needs to be entered.
   4. Re-establish the integration by granting access to the popup.
   5. Click on Test Integration and continue.
   6. Follow the steps mentioned in the “Enable / Disable the ticket retrieval feature” section to enable status refresh.

**Operational Safeguards**

The features has some guard rails in place to ensure we don’t load the system with unnecessary operations:

* The statuses of tickets created only in the last year would be refreshed.
* For tickets created using the integration but deleted from Jira, the status would be shown as “Unknown” and no more attempts would be made to refresh it.
* If for any reason, the Jira Integration breaks, the statuses for all the tickets created using it would be shown as “Unknown” until the integration is recovered and the statuses are refreshed automatically.
