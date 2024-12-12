# Jira Integration



With Xray's integration into Atlassian's Jira Software, you can manually or automatically create Jira tickets based on security threats identified by Xray. Once set up, policy violations are converted to Jira tickets. This allows the development teams to pinpoint the violations, prioritize them effectively, and take swift action to resolve them.

## **Prerequisites**

As a Jira admin, you must have the following information:

> #### Note
>
> You must have Jira Admin permissions to be able to connect Jira to Xray. For the Jira-related steps, refer to [Atlassian Jira Documentation ](https://confluence.atlassian.com/jira)



1. The supported authentication type should be one of OAuth1, OAuth2, or Basic Authentication.
2. User credentials depend on the authentication type.
3. Jira Project Name.
4. Issue type (bug, security, escalation, etc.).
5. Jira labels (optional).
6. Custom Field Mapping (optional).

## Setup Jira Integration

The setup process for Xray Jira Integration involves four crucial stages that generate tickets based on policy violations:&#x20;

### Connect to Jira Account

Connect Jira to Xray through the Xray interface using one of the supported authentication methods. Navigate to **Administration > Xray > Settings > Integration**

#### JFrog Cloud New Interface (Beta)

On the taskbar, click  (Platform Configurations), and select **Xray Settings > Integrations**. To learn more, click here.

Xray supported  authentication methods:



|                                                                                          | Xray Self Hosted                            | Xray Cloud                                  |
| ---------------------------------------------------------------------------------------- | ------------------------------------------- | ------------------------------------------- |
| **Jira Self-Managed  (Jira Server / Data Center before Jira version 8.22.0)**            | <ul><li>Basic Auth</li><li>OAuth1</li></ul> | <ul><li>Basic Auth</li><li>OAuth1</li></ul> |
| **Jira Self-Managed (Jira Server / Jira Data Center with or after Jira version 8.22.0)** | <ul><li>Basic Auth</li><li>OAuth2</li></ul> | <ul><li>Basic Auth</li><li>OAuth2</li></ul> |
| **Jira Cloud**                                                                           | <ul><li>Basic Auth</li><li>OAuth2</li></ul> | <ul><li>Basic Auth</li><li>OAuth2</li></ul> |

Follow the steps depending on the chosen authentication method.

#### **When to use basic authentication?**

[Basic authentication](https://en.wikipedia.org/wiki/Basic_access_authentication) provides a simple mechanism to do authentication when experimenting with the REST API, writing a personal script, or for use by a bot. However, as basic authentication repeatedly sends the username and password on each request, which could be cached in the web browser, it is not the most secure method of authentication we support.

We recommend you use [OAuth](https://developer.atlassian.com/server/jira/platform/oauth/) over basic authentication for most cases. OAuth requires more work to implement, but it uses a token-based workflow that is much more secure.

#### **Connect Jira to Xray Using OAuth1**

#### Note

This method is supported only for Self Managed Jira instances.

1.  Create a public key to input in Jira:

    For more information, see [https://developer.atlassian.com/server/jira/platform/oauth/#create-an-application-link](https://developer.atlassian.com/server/jira/platform/oauth/#create-an-application-link) (Step 1, Create Application link).
2. Copy your Jira URL into the dedicated box and click **Generate Key**.
3. In Atlassian: Copy and input the generated Key into your Jira "Link application" - Public Key. Your integration is ready for testing.
4.  Click **Next**.

    A validation window will open with Jira validation that you need to allow to finish integration. If the window is not showing this message, go back to step 1.

    If the window does not appear, check your pop-up blocker settings, and then again try clicking on the Click here hyperlink shown in a modal window.
5. After approving the connection, click Test **Integration**. If everything is correct, the **Finish Step** appears. You are advised to click **Next** to complete the Integration by creating a profile.

#### **Connect Jira Cloud to Xray using OAuth2**

1.  In your Jira account configure the Client and Secret ID.

    For more information, see [https://developer.atlassian.com/cloud/jira/platform/oauth-2-3lo-apps/](https://developer.atlassian.com/cloud/jira/platform/oauth-2-3lo-apps/)
2.  In Atlassian: When you are required to input your **Scope Permissions**, use the following list of permissions:

    ```
    read:issue-type:jira
    read:issue-type.property:jira
    read:project:jira
    read:project.property:jira
    read:user:jira
    read:application-role:jira
    read:avatar:jira
    read:group:jira
    read:issue-type-hierarchy:jira
    read:project-category:jira
    read:project-version:jira
    read:project.component:jira
    read:field:jira
    read:field-configuration:jira
    read:issue-meta:jira
    write:issue:jira
    write:comment:jira
    write:comment.property:jira
    write:attachment:jira
    read:issue:jira
    read:label:jira
    read:issue-security-level:jira
    read:issue.vote:jira
    read:issue.changelog:jira
    read:status:jira
    read:comment:jira
    read:comment.property:jira
    read:project-role:jira
    ```
3. In Atlassian: When inputting your **Callback URL**, use the **Copy Callback URL** in the Xray Jira wizard.&#x20;
4.  From the Xray Jira wizard, copy the generated Client ID and Secret to the related boxes and click **Next**.

    A validation window appears with Jira validation
5. Select the desired Atlassian account in the **Authorize for Site** dropdown and click **Accept** to complete the integration.
6. After approving the connection, click **Test Integration**. If everything is correct, the **Finish Step** appears. You are advised to click **Next** to complete the Integration by creating a profile.

#### **Connect Jira Self-Managed to Xray using OAuth2**

1. In the JFrog Platform:
   1. Navigate to **Administration > Xray Settings > Integration**. Click **Add Jira Integration**. A window opens up where you can configure the integration.
   2. Under **Installation Type** select **Server**. Under **Authentication Type** select **OAuth2**. Add an Integration Name and click on **Next**.
   3. Click on the copy icon to copy the callback URL and proceed to the next step.
2. In the Jira platform:
   1. Navigate to the **Administration** page. Under the options of Integrations select the **Application links** tab.
   2.  Click the **Create Link** button to create a new Application link. This will be used to connect to Xray. To learn more about Application links, see [here](https://confluence.atlassian.com/adminjiraserver/link-to-other-applications-938846918.html).

       A window appears for creating the Application link.
   3.  Under **Application type** select **External application**. Under **Direction** select Incoming. Click **Continue**.

       You will be redirected to the page for configuring the incoming link.
   4.  Add a name for the link. Paste the callback URL from Xray in the Redirect URL input. From the **Permission** dropdown, select **Write**. Click **Save**.

       You will now be taken to the **Credentials** page where the **Client ID** and **Client Secret** will be shown. They will be needed in the next step.
3. In the JFrog Platform:
   1. Copy the **Client ID** and **Client Secret** from the previous step and paste them under the Client ID and Secret inputs in Xray. Add the base URL of the Jira instance under the **Jira URL**. Click **Next**.
   2. A window opens asking for approval of the connection. Click **Allow**.
   3. After approving the connection, click **Test Integration**. If everything is correct, the **Finish Step** appears. You are advised to click **Next** to complete the Integration by creating a profile.

#### **Connect Jira to Xray Using Basic Authentication**

1. In the installation type select **Basic Integration** and add the integration name.
2.  In your Jira account create an API Token. Use this link: [https://id.atlassian.com/manage-profile/security/api-tokens](https://id.atlassian.com/manage-profile/security/api-tokens)

    For more information, see [https://developer.atlassian.com/server/jira/platform/basic-authentication/](https://developer.atlassian.com/server/jira/platform/basic-authentication/)
3. From the Xray Jira wizard, provide the following:
   * The created API token
   * Jira URL
   * Your User Name"(email that Jira integration is registered)
4.  Click **Next**.

    You are all set. Continue to the next step, [Profile Creation](broken-reference).

### Create Jira Configuration Profile

After completing the connection between Jira and Xray, you need to create a Jira Configuration profile. As there are different Jira projects for different teams, the configuration profile enables you to define specific criteria for the issued Jira ticket per Jira project, such as labels and custom mappings defined in the Jira project.

> #### Note
>
> Xray supports the below field types of Jira if you have any other type as a required field, these issue types will not appear in the “Issue Type” list of the profile configuration page:
>
> * Short Text
> * Paragraph (Xray does not support rich text)
> * Drop Down
> * Check Box / Check Boxes
> * Labels
> * Number
> * Radio Buttons
> * Select List (multiple choices)
> * Select List (single choice)



**Macros**

Xray provides a list of Macros, which you can map to your Custom Fields or Labels of the Jira Project. We would resolve these Macros for a violation and assign appropriate values to the custom fields as part of the ticket creation.Here are the available macros:

* Impacted Artifact        &#x20;
* Impacted Component
* Package Type
* Vulnerability ID
* Violation Type
* Severity
* Severity Source
* JFrog Research Severity
* CVE
* CVSS V2 Vector
* CVSS V2 Score
* CVSS V3 Vector
* CVSS V3 Score
* CVSS V2 Access Complexity
* CVSS V2 Attack Vector
* CVSS V3 Attack Complexity
* CVSS V3 Attack Vector
* Fix Version
* Watch Name
* Policy Name
* Triggered Rule
* Component License ID
* Fix Version Available?
* CVE Applicable
* Exposure Fix Cost

Example:

Consider you have a Jira Project called “Xray” and would like to configure the “Security” issue type as a profile and create tickets under it for any violations.  Here are the steps you would follow:

1. The issue type “Security” is configured as below.
2. Note the custom field “Severity” added to the context fields.  “Severity” has the below configuration.
3. Now, while creating the profile, you select “Xray” as the project type and “Security” as the issue type. Xray automatically lists all the required mandatory fields; in this case, you can see “Severity” listed here.
4. In “Severity”, you will see two types of options to select: “Dynamic Value” and “Static Value.” These are the options to select an Xray Macro or one of the options you have set in the Jira Custom Field Configurations. Xray displays the most suitable macros based on your custom field configuration.
5. Assign the Xray macro “Severity” to the Jira custom field; as soon you do this, you will see a popup prompting you to provide a default value. When you map a macro to a mandatory custom field, we need a default value, which we will use while creating the ticket. For example, when a CVE is reported, there may not be a Severity in this case. What would you want to see in the Jira ticket?
6. You may also want to add a “Label” when Xray creates a ticket. Label is an optional field during ticket generation, you must add that to the profile before editing it.  Click “Add Optional Fields” and add Labels to the profile page.
7. You could select one of the Xray Macros or type in a static text or both. Note that white spaces are not allowed in Jira Labels, these will be replaced by \_ (underscores)  in the Jira ticket.
8. To validate your configurations, try “Creating a test ticket.”
9. Save your profile.

Enable the Jira ticket creation in the Policy rules. In **Policy > Policy Rules > Automatic Actions**, select the **Create Jira Ticket** checkbox to trigger the creation of Jira tickets when violations are found that match the rule you defined in the Policy.

To create a Jira ticket based on validation found in Watch resources, you must add a default Jira Profile. This profile will be used as the default profile to generate all the tickets.

For more advanced configuration, click the Advanced Settings:

*   **Ticket duplication**

    If you need tickets duplication for every artifact version, select the checkboxes. Most commonly left unchecked.
*   **Create tickets by impact path**

    This section allows you to create multiple tickets for the same violation or map the violation to a different Jira profiles. The tickets will be created based on the violation impact paths; all the tickets that do not match the mapped impact path will be created in the default profile. See the provided Best Practices for an elaborate example.
*   **Create tickets for ignored violations**

    If you want tickets generated for ignored violations, turn this feature on. By default, JFrog Xray does not generate tickets for ignored violations.



When the tickets are created, you can see the Jira icons against the violation, and the details view in the UI.

In Xray reports, the violations reports of Xray, also have the ticket ID wherever applicable.



## Jira Ticket Manual Creation

In addition to automatic creation of Jira ticket, Xray enables you to create a Jira ticket for the following issue types manually:

* Violations (all types)
  * Operational risk
  * License violation
  * Security

> #### More Permissions for OAuth2
>
> If you have set up Jira integration with Xray using OAuth2, manual creation of Jira tickets requires some extra permissions.Ensure that the permissions are updated before manually creating Jira tickets. For more information, seeConnecting Jira to Xray Using OAuth2.



To manually create a Jira ticket:

1. In the **Application** tab, navigate to a violation on one of the following pages:
   * **Artifactory > Builds**
   * **Artifactory > Artifacts**
   * **Scans List > Repositories**
   * **Scans List > Builds**
   * **Scans List > Release Bundles**
   * **Watch Violations**
2. Click the vulnerability ID, and in the window that appears on the right, click the action button (three dots) and click **Create a Jira**.
3.  In the **Create a Jira Ticket** window, update the following fields:

    | Field            | Description                                                                                                                                                                                                                  |
    | ---------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
    | **Profile Name** | <p>This dropdown lists all the Jira configuration profiles that were defined when creating the Jira integration.</p><p>Click to select the relevant profile.</p>                                                             |
    | **Issue Type**   | This is auto-filled according to the profile selection.                                                                                                                                                                      |
    | **Labels**       | This is auto-filled with all the labels. The drop-down displays the labels on the profile integration page. While you can remove the label from the field, it will not delete it from the main profile integration.          |
    | **Component**    | This is auto-filled. The drop-down lists all the components affected by the vulnerability and all components are selected by default. You have the option of selecting a subset of the listed components.                    |
    | **Title**        | The is auto-filled based on the type of violation.                                                                                                                                                                           |
    | **Description**  | <p>This is auto-filled and cannot be edited.</p><p>Description is auto-filled based on the violation's current state and the selected components. If the components are changed, the description is updated accordingly.</p> |
    | **User comment** | Add relevant comments for the ticket.                                                                                                                                                                                        |
4. Click **Create**.

> #### Note
>
> If a ticket has already been created for the issue, you have the option of updating it.

Whenever a Jira ticket is manually created for a violation, it is indicated with an icon . Hover over the icon to see the list of Jira tickets that have already been created for the violation. If there are multiple tickets, the last created ticket will be the leading ticket.

The Jira indicator along with the Jira Id is also shown on the Details screen. Clicking on a Jira Id redirects you to the Jira page for that ticket.

To manually update a Jira ticket:

1. In the **Application** tab, navigate to a violation on one of the following pages:
   * **Artifactory > Builds**
   * **Artifactory > Artifacts**
   * **Scans List > Repositories**
   * **Scans List > Builds**
   * **Scans List > Release Bundles**
   * **Watch Violations**
2. Click the vulnerability ID that already has a Jira indication, and in the window that appears on the right, click the action button (three dots) and click **Update a Jira**.
3. In the **Update a Jira Ticket** window:
   1. If there are multiple tickets, click the **Jira Ticket Number** drop-down to select the ticket to be updated.
   2. Scroll down to the **Add Comments** field and add relevant comments for the ticket.
4.  Click **Update**.

    The **Title** and **Description** are automatically updated based on the current state of the violation.

> #### Note
>
> If you try to update a ticket that has already been deleted, a message is displayed to that effect and you will have the option of creating a new ticket.

## Best Practices



Creating effective and manageable tickets in Jira or any issue-tracking system is crucial for maintaining an efficient workflow, clear communication, and project management.

A few strategies curated by Atlassian around organizing Projects are as follows,

* Releasable product: Organizing your projects by releasable products or groups of work that share a common release cycle.
* Team-based projects are another common organizational model. This allows your work to mirror your social organization and is convenient in less cross-functional setups, as it allows for more straightforward project permission management.
* Business Unit: Closely related to organizing around teams, you might also consider organizing around larger business units - marketing, product, IX, IT, etc. Types of work will likely fall into similar patterns, making setting up workflows - and issue types particularly - more convenient.
* Components: Be aware that using components, you can still sub-categorize issues within a given project.

We have seen our clients mix these strategies to have a solution that reflects their operational model.

**Releasable Product**

Your Jira will have a Project representing a “Product”. This project will be used to track all activities for the product.&#x20;

When creating a releasable product, various teams within the same group will work together to produce the final artifact. For instance, the engineering team will develop the core product while the dev ops team will create artifacts for log shipping, deployment, and other related tasks. Additionally, the database team will provide utilities for initializing and migrating the database.

After scanning the final artifact, you may come across violations that need to be addressed by various teams depending on the impact path. In some cases, different teams may work together to resolve a CVE. For tracking purposes in Jira, you can assign relevant "Components" fields in each ticket.

Xray's Jira Integration supports this organizational structure. Set up three profiles for the same Jira Project with different components.

Afterwards, you will configure the relevant watch as follows. Here, we add two entries in the advanced settings to create a separate ticket whenever a violation affects anything under '\*\*/DevOps/\*\*' and '\*\*/database/\*\*'

Xray applies settings for each of the violations generated by the Watch. We examine the impact paths affected by the violation. If any of the paths match the specified patterns, a separate ticket is created under the corresponding mapped profile.&#x20;

If there are no advanced settings or the violation does not have an impact path that matches the pattern, a ticket is created with all violation details under the default profile mapped to the Watch. In the given example, the default profile is "Xray-Security-Core."

**Team-Based / Business Unit**

To organize your work effectively in Jira, you can create separate projects for each team or business unit (BU) in your organization. This way, different teams can collaborate on the same product, but each team will have its own Jira project.&#x20;

To ensure you receive updates for each specific project, you must create a separate profile for each Jira project. You can then use these profiles in your watches with path-based patterns.

**Profile Naming Conventions**

Have you noticed the naming conventions we use for profiles? They follow the format of "\{{Jira Project\}} - \{{Issue Type\}} - \{{What’s this for\}}". This format helps Xray users understand the intention of each profile, even if they do not have permission to review the Jira integration in Xray.
