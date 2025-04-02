# Setup Xray Jira Integration

The setup process for Xray Jira Integration involves four crucial stages that generate tickets based on policy violations: ​ ​ ​&#x20;

* [Connect to a Jira account](setup-xray-jira-integration.md#uuid-80d581ca-426d-171e-0e50-13dc89dd14eb)
* [Create Profiles​​ to map violations to Jira boards](setup-xray-jira-integration.md#uuid-26445b3a-38d7-7e7e-2122-bedfeba7bf98)
* [Add Profiles to Watches​​ to define the resources](setup-xray-jira-integration.md#uuid-ffb9e3db-f2dc-6c8a-9624-25e5c111ab07)
* [Configure Policy rules ​​to activate the ticket creation](setup-xray-jira-integration.md#uuid-2f862932-e821-27e8-9d33-9fe6f3ed9f05)

### Connect to a Jira Account <a href="#uuid-80d581ca-426d-171e-0e50-13dc89dd14eb" id="uuid-80d581ca-426d-171e-0e50-13dc89dd14eb"></a>

Connect Jira to Xray through the Xray interface using one of the supported authentication methods. Navigate to **Administration > Xray > Settings > Integration**

{% hint style="info" %}
JFrog Cloud New Interface (Beta)

On the taskbar, click  (Platform Configurations), and select **Xray Settings > Integrations**. To learn mor
{% endhint %}

Xray supports three authentication methods:

* OAuth1
* OAuth2
* Basic Auth

|                                                                                                                            | Xray Self Hosted                            | Xray Cloud                                  |
| -------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------- | ------------------------------------------- |
| <h4 id="id_xrayjiraintegration-jiraon-prem">Jira Self-Managed  (Jira Server / Data Center before Jira version 8.22.0)</h4> | <ul><li>Basic Auth</li><li>OAuth1</li></ul> | <ul><li>Basic Auth</li><li>OAuth1</li></ul> |
| **Jira Self-Managed (Jira Server / Jira Data Center with or after Jira version 8.22.0)**                                   | <ul><li>Basic Auth</li><li>OAuth2</li></ul> | <ul><li>Basic Auth</li><li>OAuth2</li></ul> |
| <h4 id="id_xrayjiraintegration-jiracloud">Jira Cloud</h4>                                                                  | <ul><li>Basic Auth</li><li>OAuth2</li></ul> | <ul><li>Basic Auth</li><li>OAuth2</li></ul> |

Follow the steps depending on the chosen authentication method.

**When to use basic authentication?**

[Basic authentication](https://en.wikipedia.org/wiki/Basic_access_authentication) provides a simple mechanism to do authentication when experimenting with the REST API, writing a personal script, or for use by a bot. However, as basic authentication repeatedly sends the username and password on each request, which could be cached in the web browser, it is not the most secure method of authentication we support.

We recommend you use [OAuth](https://developer.atlassian.com/server/jira/platform/oauth/) over basic authentication for most cases. OAuth requires more work to implement, but it uses a token-based workflow that is much more secure.

#### Connect Jira to Xray Using OAuth1 <a href="#id_xrayjiraintegration-connectingjiratoxrayusingoauth1" id="id_xrayjiraintegration-connectingjiratoxrayusingoauth1"></a>

{% hint style="info" %}
This method is supported only for Self Managed Jira instances.
{% endhint %}

1.  Create a public key to input in Jira:

    For more information, see [https://developer.atlassian.com/server/jira/platform/oauth/#create-an-application-link](https://developer.atlassian.com/server/jira/platform/oauth/#create-an-application-link) (Step 1, Create Application link).
2. Copy your Jira URL into the dedicated box and click **Generate Key**.
3. In Atlassian: Copy and input the generated Key into your Jira "Link application" - Public Key. Your integration is ready for testing.
4.  Click **Next**.

    A validation window will open with Jira validation that you need to allow to finish integration. If the window is not showing this message, go back to step 1.

    If the window does not appear, check your pop-up blocker settings, and then again try clicking on the Click here hyperlink shown in a modal window.
5. After approving the connection, click Test **Integration**. If everything is correct, the **Finish Step** appears. You are advised to click **Next** to complete the Integration by creating a profile.

#### Connect Jira Cloud to Xray using OAuth2 <a href="#id_xrayjiraintegration-connectingjiratoxrayusingoauth2" id="id_xrayjiraintegration-connectingjiratoxrayusingoauth2"></a>

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
    read:issue-details:jira
    read:field.default-value:jira
    read:field.option:jira
    ```

    Note: For Xray versions prior to 3.112.x,  `read:issue-details:jira`, `read:field.default-value:jira` and `read:field.option:jira` are not needed.
3.  From the Xray Jira wizard, copy the generated Client ID and Secret to the related boxes and click **Next**.

    A validation window appears with Jira validation
4. Select the desired Atlassian account in the **Authorize for Site** dropdown and click **Accept** to complete the integration.
5. After approving the connection, click **Test Integration**. If everything is correct, the **Finish Step** appears. You are advised to click **Next** to complete the Integration by creating a profile.

#### Connect Jira Self-Managed to Xray using OAuth2 <a href="#section-idm234443158402293" id="section-idm234443158402293"></a>

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

#### Connect Jira to Xray Using Basic Authentication <a href="#id_xrayjiraintegration-connectingjiratoxrayusingbasicauthentication" id="id_xrayjiraintegration-connectingjiratoxrayusingbasicauthentication"></a>

1. In the installation type select **Basic Integration** and add the integration name.
2.  In your Jira account create an API Token. Use this link: [https://id.atlassian.com/manage-profile/security/api-tokens](https://id.atlassian.com/manage-profile/security/api-tokens)

    For more information, see [https://developer.atlassian.com/server/jira/platform/basic-authentication/](https://developer.atlassian.com/server/jira/platform/basic-authentication/)
3. From the Xray Jira wizard, provide the following:
   * The created API token
   * Jira URL
   * Your User Name"(email that Jira integration is registered)
4.  Click **Next**.

    You are all set. Continue to the next step, [Profile Creation](https://about/document/preview/642388#UUID-26445b3a-38d7-7e7e-2122-bedfeba7bf98).

### Create a Jira Configuration Profile <a href="#uuid-26445b3a-38d7-7e7e-2122-bedfeba7bf98" id="uuid-26445b3a-38d7-7e7e-2122-bedfeba7bf98"></a>

After completing the connection between Jira and Xray, you need to create a Jira Configuration profile. As there are different Jira projects for different teams, the configuration profile enables you to define specific criteria for the issued Jira ticket per Jira project, such as labels and custom mappings defined in the Jira project.

**Note**:&#x20;

Xray supports the below field types of Jira if you have any other type as a required field, these issue types will not appear in the “Issue Type” list of the profile configuration page

* Short Text
* Paragraph (Xray does not support rich text)
* Drop Down
* Check Box / Check Boxes
* Labels
* Number
* Radio Buttons
* Select List (multiple choices)
* Select List (single choice)
* Jira Components

**Macros**

Xray provides a list of Macros, which you can map to your Custom Fields or Labels of the Jira Project. We would resolve these Macros for a violation and assign appropriate values to the custom fields as part of the ticket creation. Here are the available macros:

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

### Configure the Jira Policy Rules <a href="#uuid-2f862932-e821-27e8-9d33-9fe6f3ed9f05" id="uuid-2f862932-e821-27e8-9d33-9fe6f3ed9f05"></a>

Enable the Jira ticket creation in the Policy rules. In **Policy > Policy Rules > Automatic Actions**, select the **Create Jira Ticket** checkbox to trigger the creation of Jira tickets when violations are found that match the rule you defined in the Policy.

### Configure the Watch with the Jira Configuration Profile <a href="#uuid-ffb9e3db-f2dc-6c8a-9624-25e5c111ab07" id="uuid-ffb9e3db-f2dc-6c8a-9624-25e5c111ab07"></a>

To create a Jira ticket based on validation found in Watch resources, you must add a default Jira Profile. This profile will be used as the default profile to generate all the tickets.

For more advanced configuration, click the Advanced Settings:

*   **Ticket duplication**

    If you need tickets duplication for every artifact version, select the checkboxes. Most commonly left unchecked.
*   **Create tickets by impact path**

    This section allows you to create multiple tickets for the same violation or map the violation to a different Jira profiles. The tickets will be created based on the violation impact paths; all the tickets that do not match the mapped impact path will be created in the default profile. See the provided Best Practices for an elaborate example.
*   **Create tickets for ignored violations**

    If you want tickets generated for ignored violations, turn this feature on. By default, JFrog Xray does not generate tickets for ignored violations.
