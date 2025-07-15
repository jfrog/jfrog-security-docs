# Assign/Unassign Jira Tickets

Prerequisites:

* A healthy Jira integration and a Jira profile mapped to the same Jira Project where the user's Jira ticket is created on Jfrog Xray.
* Permissions for OAuth 2.0: If you have set up Jira integration with Xray using OAuth2, manually assigning Jira tickets requires additional permissions. Ensure that the permissions are updated before manually assigning Jira tickets. For more information, see Connecting Jira to Xray Using OAuth2.
* Xray version 3.124 or higher must be installed.

**To assign a Jira ticket:**

1. In the Application, navigate to a violation on one of the following pages:
   * Scans List > Repositories > Select a Repository > Select an Artifact > Select a Version > Policy Violations
   * Scans List > Builds > Select a Build > Select a Version > Policy Violations
   * Scans List > Release Bundles > Select a Release Bundle > Select a Version > Policy Violations
2. Click on a violation, and in the window that appears on the right, click the action button (represented by three dots) and select Assign Ticket.
3. In the Assign Jira ticket window, enter the Jira Ticket URL and click Assign.
4. Optional: You can also view the details of the ticket being assigned by clicking on the View Ticket Details.

**To Unassign a manually assigned ticket:**

To Unassign a manually assigned ticket from a violation, click on a violation, and in the window that appears on the right, click the Tickets Info tab. Click on the Unassign icon against the corresponding ticket on the same Tickets Info tab.

**Limitations:**

1. Unassignment is only available for:
   * Manually assigned tickets.
   * Users with admin or watch manager permissions.
2. Manually assigned tickets cannot be updated via the Xray Update Ticket capability.



