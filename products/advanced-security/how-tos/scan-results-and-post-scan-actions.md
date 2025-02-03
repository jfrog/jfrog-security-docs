# Scan Results and Post-Scan Actions

After running an **Advanced Security** scan, results can be accessed from the **Scans List** page. For detailed insights, refer to the relevant sections on **Exposure Scans** and **Contextual Analysis** to understand scan findings and available actions.

The following topics outline how to manage **JFrog Advanced Security** scan results and next steps:

*   #### **Ignoring an Exposures Violation**

    Ignore rules allow you to **whitelist and suppress specific security violations**, helping to reduce unnecessary alerts. This is particularly useful in scenarios such as:

    * Running **Advanced Scans** on a **testing repository** where violations should not impact the workflow.
    * Strict enforcement policies that **block development progress**, requiring temporary suppression of certain violations.

    For more details on managing ignore rules, refer to **Ignore Rules**. You can also configure, modify, or delete ignore rules as needed.

#### **Advanced Security Scan Results REST API Support**

To automate the management of **Exposures violations**, use the following **REST API**:

* **Create Ignore Rule** – Allows you to programmatically define rules to ignore specific violations.

