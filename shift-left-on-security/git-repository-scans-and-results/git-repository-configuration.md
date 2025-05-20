# Git Repository Configuration

To begin, an initial Frogbot scan must be executed. Scan results can then be viewed under **Xray → Indexed Resources**, where it's also possible to configure Git repository scanners. Configuration settings defined in the Frogbot YAML file and environment variables take precedence over any settings applied through the platform.

### Configuring Git Repositories

1. Navigate to **Administration** > **Xray Settings** > **Indexed Resources**.
2. Select a Git Repository.
3. From the actions menu, select **Configure**.\
   The **Scan Configurations** pop-up window opens.
4. Select one or more types of scans you wish to run:

* SCA
*   Advanced Security:

    * Vulnerabilities Contextual Analysis
    * IaC
    * Secrets
    * SAST

    (Optional: **Exclude Path,** using the following format: `**/*(venv,...,.venv)*`)

    (Optional for SAST only: [Exclude Rule](../../products/advanced-security/features-and-capabilities/sast/list-of-sast-rules.md))

5. Click **Apply**.\
   The list of folders in the Repository you configured opens.
