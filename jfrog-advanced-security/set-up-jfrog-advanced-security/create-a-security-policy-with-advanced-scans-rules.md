# Create a Security Policy with Advanced Scans Rules

#### Create a Security Policy with Advanced Scans Rules <a href="#uuid-018f8c6d-3470-30cf-a421-78814c54a2c8" id="uuid-018f8c6d-3470-30cf-a421-78814c54a2c8"></a>

Policies enable you to create a set of rules, in which each rule defines security criteria, with a corresponding set of automatic actions according to your needs. Policies are enforced when applying them to [Configuring Xray Watches](https://about/document/preview/361196#UUID-8827a9ab-1073-844c-095f-17c69daa11e0). To learn more on how to create a Policy, see [Creating Xray Policies and Rules](https://about/document/preview/625848#UUID-05f92e64-4f1a-a5e3-072b-4e8e108efbd8).

We recommend creating Policies to get a focused list of violations based on your security criteria.

You can create a security policy with exposures and contextual analysis-specific rules. A violation is issued when the criteria you set are met. You can view issued violations either from [Scans List](https://about/document/preview/551896#UUID-82a35411-384b-423c-8aba-0b6796583862)or [Watch Violations](https://about/document/preview/361938#UUID-d1b510b5-16a4-37c7-6da5-e6e649aecb90)pages.

**Create an Exposures Policy**

1. In the **Administration** module, under **Xray**, select **Watches** **& Policies** and from the **Policies** tab click **New Policy**.
2. Select the policy rule type **Security**.
3. Click **New Rule**, and from the **Type** drop-down, select **Exposures**.
4. Select the **Minimal JFrog Severity**. The severity given by the JFrog Security Research team after the manual analysis of the CVE by the team. This specifies that a violation is issued only if the selected severity is met.
5. Select one or more exposure categories. This specifies that a violation is issued only for the selected categories.
6. Define the automatic actions that determine the automatic response to a detected Policy violation. For more information, see [Creating Xray Policies and Rules](https://about/document/preview/625848#UUID-05f92e64-4f1a-a5e3-072b-4e8e108efbd8).

**Create a Contextual Analysis Policy**

1. In the **Administration** module, under **Xray**, select **Watches & Policies** and from the **Policies** tab click **New Policy**.
2. Select the policy rule type **Security**.
3. Check the **Skip not applicable CVEs** checkbox. By selecting this option, the Policy will not issue any violations on CVEs that were found not applicable by the Contextual Analysis scanners.
