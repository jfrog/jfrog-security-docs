# Working in Air-Gapped Environments

Air-gapped environments are isolated from the public internet. To enable security scanning in such environments, you’ll need to configure a local Artifactory repository that mirrors [https://releases.jfrog.io](https://releases.jfrog.io), and update your tools to use this repository for downloading required components.

**Before You Begin**

Access the internet and download the necessary files from the following link: [Releases JFrog - Analyzer Manager ](https://releases.jfrog.io/artifactory/xsc-gen-exe-analyzer-manager-local/).

### Create a Dedicated Air-Gapped Artifactory Repository&#x20;

1. In your air-gapped environment, create a local **generic** Artifactory repository to store the required resources.
2. Upload the downloaded resources to the local generic repository created in step 1.
3. Set the environment variables in your CLI, IDE, or Frogbot to point to the local generic repository in your air-gapped Artifactory.

### Configure Tools to Use Your Local Repo

After setting up the repository, you must configure your tools to pull all required components, such as binaries, analyzer tools, or metadata, from your internal Artifactory instance instead of the public internet.

Use the appropriate **environment variable** depending on the tool:

| Tool        | Environment Variable                                                                                                                         |
| ----------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| JFrog CLI   | `JFROG_CLI_RELEASES_REPO`                                                                                                                    |
| Frogbot     | `JF_RELEASES_REPO`                                                                                                                           |
| IDE Plugins | Create a remote repository in Artifactory and specify its name in your IDE's JFrog plugin settings, under **External Resources Repository**. |
