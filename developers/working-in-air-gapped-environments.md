# Working in Air-Gapped Environments

Air-gapped environments are isolated from the public internet. To enable security scanning in such environments, you’ll need to configure a local Artifactory repository that mirrors [https://releases.jfrog.io](https://releases.jfrog.io), and update your tools to use this repository for downloading required components.

### Set Up a Local Releases Repository

1. In the **JFrog Platform**, go to **Administration > Repositories > Remote**.
2. Click **Create a remote repository**.
3. Set the following values:
   * **Package Type**: _Generic_
   * **Repository Key**: _e.g., `jfrog-releases-repo`_
   * **URL**: `https://releases.jfrog.io`
4. (Optional) Uncheck **Store Artifacts Locally** to save storage space.
5. Click **Save & Finish**.

### Configure Tools to Use Your Local Repo

After setting up the repository, you must configure your tools to pull all required components, such as binaries, analyzer tools, or metadata, from your internal Artifactory instance instead of the public internet.

Use the appropriate **environment variable** depending on the tool:

| Tool        | Environment Variable                                                                                                                         |
| ----------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| JFrog CLI   | `JFROG_CLI_RELEASES_REPO`                                                                                                                    |
| Frogbot     | `JF_RELEASES_REPO`                                                                                                                           |
| IDE Plugins | Create a remote repository in Artifactory and specify its name in your IDE's JFrog plugin settings, under **External Resources Repository**. |
