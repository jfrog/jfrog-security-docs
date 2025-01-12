# Policies

## Create an Xray Policy

Creating an Xray Policy involves the following primary steps:

1. In the **Administration** module, select **Watches & Policies** and from the **Policies** tab click **New Policy**.
2. Provide a name for the Policy.
3.  Select the **Policy Type**; **Security**, **License**, or **Operational Risk**. For more information, see [Trigger Violations Using Xray Policy Rules](https://jfrog.com/help/r/6nte66fuu2ZQMB2dfriysg/6HGKZw6F3lnul8K12To_IQ)&#x20;

    <figure><img src="../../.gitbook/assets/image (3) (1).png" alt=""><figcaption></figcaption></figure>
4.  **Click Next**.

    The **Policy Rules List** appears.
5. Define the rules and actions depending on what you have selected. The various options are outlined in [Trigger Violations Using Xray Policy Rules](https://jfrog.com/help/r/6nte66fuu2ZQMB2dfriysg/6HGKZw6F3lnul8K12To_IQ) and [Policy Violation Automatic Actions](https://jfrog.com/help/r/6nte66fuu2ZQMB2dfriysg/ytBDSmiGVVseDRMOLK0qtQ).

<figure><img src="../../.gitbook/assets/image (4) (1).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (5) (1).png" alt=""><figcaption></figcaption></figure>



6.  Click **Next**.

    The **Apply on Scope** section appears
7. Select the Watch or multiple Watches that contain the resources the Policy rules will apply to.

<figure><img src="../../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

8. Click **Save Policy** to complete the creation.

## Trigger Violations Using Xray Policy Rules

Policies contain user-defined rules allowing you to trigger violations for specific vulnerabilities or license breaches by setting a license or security criteria, with a corresponding set of automatic actions according to your needs. Rules are processed according to the ascending order in which they are placed in the Rules list on the Policy. If a rule is met, the subsequent rules in the list will not be applied.

Xray supports the following policy types:

#### Security Rules <a href="#uuid-fd14393c-41a6-e3de-1cef-c9ea5c81a6e8_bridgehead-idm4647015730982433963147294951" id="uuid-fd14393c-41a6-e3de-1cef-c9ea5c81a6e8_bridgehead-idm4647015730982433963147294951"></a>

A Security Rule allows you to create a set of rules around security vulnerabilities. These are the possible criteria:

* **CVEs**: Create a rule to generate violations on CVEs by the following:
  * **Minimal Severity** (Minor, Major, Critical, All): The minimal security vulnerability severity as it is in the JFrog vulnerabilities database. If the artifact or build contains a vulnerability with the selected severity or higher, the rule will meet the criteria, the automatic actions will be executed, and the policy will stop processing.
  * **CVSS Score** (1-10): The CVSS score range to apply to the rule. This is used for a fine-grained control, rather than using the predefined severities. The score range is based on CVSS v3 scoring, and CVSS v2 score is CVSS v3 score is not available.
  * **CVE IDs**: Create policy rules for specific vulnerability IDs that you input. You can add multiple vulnerability IDs up to 100, separated by ",". CVEs and Xray IDs are supported.
  * **Except if a Fix Version is available**: Xray will not generate violations for issues that do not contain a fixed version. If a fixed version is available later, the violation will be generated.
  * **Skip if not applicable CVEs (JFrog Advanced Security only)**: If The CVE is not applicable as defined by a Contextual Analysis scan, the rule will not be applied.
* **Malicious Packages:**&#x43;reate a rule that generates violations for detected malicious packages.
* **Exposures:** Create a rule to generate violations for detected Secrets, Applications, Services and IaC misconfigurations.
* **Package Version:** Xray will generate violations for the specific packages defined in this Policy. Provide the package type and name, and versions. You can either select all versions of the package or custom versions. Custom versions allow you to add specific package versions, or include a range.

#### License Rules <a href="#uuid-fd14393c-41a6-e3de-1cef-c9ea5c81a6e8_bridgehead-idm4647015704699233963146514363" id="uuid-fd14393c-41a6-e3de-1cef-c9ea5c81a6e8_bridgehead-idm4647015704699233963146514363"></a>

A license Rule allows you to create a set of rules around license compliance. There are three possible criteria:

* **Allowed Licenses**: Specifies an Allow List of OSS licenses that **may** be attached to a component. If a component has an OSS license outside the specified Allow List, The rule will meet the criteria, a violation will be generated, automatic actions will be executed, and the policy will stop processing.
* **Banned Licenses**: Specifies a Block List of OSS licenses that **may not** be attached to a component. If a component has any of the OSS licenses specified, The rule will meet the criteria, a violation will be generated, automatic actions will be executed, and the policy will stop processing.
* **Multiple license permissive approach:** A violation will not be generated if at least one license is valid in cases where multiple licenses were detected on the component.

## Policy Violation Automatic Actions

An action determines the automatic response to a detected Policy violation. You can define one or more action within each Policy Rule. Actions include the following:

* **Generate Violation (Minor, Major, Critical)**: The severity of the violations that is generated if the criteria are met.
* **Notify Email:** This action lets you specify email addresses to which Xray should send an email message about a violation when one is triggered. For this to work, you need to have a mail server configured in Xray.
* **Notify Watch's Recipients:** This action lets you send an email to all the watch recipients about a violation when triggered.
* **Notify Deployer:** This action lets you send an email to the user who deployed the component about a violation when triggered.
* **Create Jira Ticket**: This action enables the Jira ticket creation in the Policy rules
* **Trigger Webhook:** This action lets you specify webhooks you have configured in Xray that should be invoked when a violation is triggered (See payload below).
* **Block Download:** This action lets you specify that artifacts should be blocked for download and allows you to select one of these options:
  * Block Download: When set, Artifactory will block the download of artifacts that meet the Artifact Filter and Severity Filter specifications for this watch.
  * Block Unscanned: When set, Artifactory will block download of artifacts that meet the Artifact Filter specifications for this watch, but have not been scanned yet or the Xray data has been removed due to a retention policy. For more information on Xray Data Retention, see [Indexing Xray Resources](https://jfrog.com/help/r/6nte66fuu2ZQMB2dfriysg/QkeI5aDvqoggEGUdFO49fw).
* **Block Release Bundle distribution:** This action lets you specify that Release Bundles should be blocked for download if they meet the policy criteria rule.
*   **Fail Build:** This action lets you specify that if a CI server requests a build to be scanned, and the Watch triggers a violation, Xray will respond with an indication that the build job should fail.

    This action is only available if the Watch is defined with Builds as the target type.

    *   **Grace Period**: There are many cases where you do not want to fail the first build, for example, some violations are not showstoppers, and you would like to look into them later without stopping the build creation. You can set a grace period for a number of days that you define according to your needs. During the grace period you define, the build will not fail and all violations are ignored during this period. An automatic Ignore Ruleis created for the grace period with the following criteria:

        * On the specific vulnerability/license
        * On the specific component
        * On any version of the specific build
        * On the specific Policy
        * On the specific Watch

        Once the grace period ends, the Ignore Rule is deleted, and if the build contains violations, those violations are created and the build will fail.\


