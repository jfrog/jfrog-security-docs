# Create Custom Conditions

Creating custom conditions in JFrog Curation helps security managers manage software packages and ensure that they meet your organization's security and compliance standards better. This guide will walk you through the steps necessary to create and manage these conditions effectively.

### Step-by-Step Instructions

#### Step 1: Access Administration Settings

1. Log in to your JFrog platform.
2. Navigate to the **Administration** panel. You can typically find this in the main menu.

#### Step 2: Go to Curation Settings

1. Within the Administration panel, look for **Curation Settings** .
2. Click on **Conditions** to view the conditions management interface.

#### Step 3: Create a New Condition

1. In the top right corner of the Conditions page, you will find a button labeled **Create Condition**. \
   Click on it to open the condition creation form.

#### Step 4: Explore Available Condition Templates

* You'll notice a range of condition templates available for selection. The number of templates may vary over time as JFrog adds new options. We advice visiting this page from every quarter to see new updates.\
  \
  Here are the currently supported templates:
  * **Open SSF**
  * **Allowed and Banned Lists for Packages**
  * **Block Specific Package Versions**
  * **Allowed and Banned Lists for Licenses**
  * **Package Vulnerability Based on CVSS Score Range**
  * **Package Version in Mature State**
  * **Package Vulnerability to a Specific CVE**

#### Step 5: Configure Your Selected Condition

1. **Select a Template** : Choose the condition template that best fits your requirements.
2. **Set Configuration Options** : Each condition template will have specific configuration fields. Fill these out according to your needs.
   * **Relaxation Elements** : Some conditions may have relaxation options. For example:
     * For the “Package Vulnerable with CVSS Score,” you can set relaxation elements like **EPSS Score** , **Cache Dependency** , and **Fixed Version Dependencies** .
     * For “Immature Package,” you might set dependencies if it fixes a critical CVE.

#### Step 6: Save Your Condition

1. Once all fields are configured, click the **Save** button.
2. The new condition will be saved and listed under **Custom Conditions** in the Conditions table.



#### Step 7: Manage Your Conditions

* After saving, you can:
  * **Edit Conditions** : Click on an existing condition to modify its settings anytime.
  * **Create Policies** : Base new policies on your custom conditions to automate compliance and security checks.

#### Conclusion

You now have the necessary steps to create and manage custom conditions in JFrog Curation. You can return at any time to edit existing conditions or create new ones based on your evolving requirements. Implementing these custom conditions will help you maintain better security and compliance for your software packages.

For further details or support, refer to the [JFrog Documentation ](https://www.jfrog.com/confluence/)or contact your JFrog customer support representative.
