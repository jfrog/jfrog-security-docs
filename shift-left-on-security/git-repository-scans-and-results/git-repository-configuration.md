# Git Repository Configuration

The Git repository configuration reflects the actual hierarchy in your Source Control Management (SCM) system. It supports inheriting settings for future repositories and folders. When both repositories and folders coexist in the hierarchy, the JFrog Platform represents them using a virtual folder. In this view, all repositories that exist alongside folders at the same level are grouped under “/”. You can configure scanners to scan either SCM and downstream automatically or target custom repositories and folders directly.

#### Before You Begin

* An initial [Frogbot ](../frogbot/)scan must be executed.&#x20;
* Make sure the `JF_USE_CONFIG_PROFILE` [variable](../frogbot/configure-frogbot/frogbot-optional-configuration-parameters.md) is set to `true`      &#x20;
* Configuration settings defined in the [Frogbot YAML](../frogbot/configure-frogbot/) file and environment variables take precedence over any settings applied through the platform.

### Configuring Git Repositories

1. Navigate to **Administration** > **Xray Settings** > **Indexed Resources**, and select the **Git Repositories** tab.
2. Select one or more Git Repositories and folders.
3. From the actions menu, select **Configure**.\
   The **Scan Configurations** pop-up window opens.
4. Select one or more types of scans you wish to run on the selected Git Repositories:

* SCA
*   Advanced Security:

    * Vulnerabilities Contextual Analysis
    * IaC
    * Secrets
    * SAST

    (Optional: **Exclude Path,** using the following format: `**/*(venv,...,.venv)*`)

    (Optional for SAST only: [Exclude Rule](../../products/advanced-security/features-and-capabilities/sast/list-of-sast-rules.md))

5. Click **Apply**.\
   The **Folder** table opens and displays the:&#x20;

* Folder names within the Git repository
* Number of folders within each folder
* Last time the folder was scanned
* Configuration source, which may be the Git repository configuration (**Inherited**) or the folder itself (**custom**).
