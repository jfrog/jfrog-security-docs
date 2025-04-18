# Create Custom Conditions

Creating custom conditions in JFrog Curation helps security managers manage software packages and ensure that they meet your organization's security and compliance standards better. This guide will walk you through the steps necessary to create and manage these conditions effectively.

1. Navigate to the **Administration > Curation Settings > Conditions**
2. In the top right corner of the Conditions page, you will find a button labeled **Create Condition**. \
   Click on it to open the condition creation form.
3.  Explore the list of available templates. You'll notice a range of condition templates available for selection. The number of templates may vary over time as JFrog adds new options. We advise visiting this page every quarter to see new updates.\


    Here are the currently supported templates:

    * **Open SSF**
    * **Allowed and Banned Lists for Packages**
    * **Block Specific Package Versions**
    * **Allowed and Banned Lists for Licenses**
    * **Package Vulnerability Based on CVSS Score Range**
    * **Package Version in Mature State**
    * **Package Vulnerability to a Specific CVE**
4. Select a Template: Choose the condition template that best fits your requirements.
5. Set Configuration Options: Each condition template will have specific configuration fields. Fill these out according to your needs.
   * Relaxation Elements: Some conditions may have relaxation options. For example:
     * For the “Package Vulnerable with CVSS Score,” you can set relaxation elements like **EPSS Score** , **Cache Dependency** , and **Fixed Version Dependencies** .
     * For “Immature Package,” you might set dependencies if it fixes a critical CVE.
6. Click **Save o**nce all fields are configured. \
   The new condition will be saved and listed under **Custom Conditions** in the Conditions table

After saving, you can:

* **Edit Conditions** : Click on an existing condition to modify its settings anytime.
* **Create Policies** : Base new policies on your custom conditions to automate compliance and security checks.
