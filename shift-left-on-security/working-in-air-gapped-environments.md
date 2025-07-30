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

#### CLI

1.  Define a JPD and server ID using:

    ```bash
    bashCopyEditjf c add <server-id>
    ```
2.  Set the environment variable `JFROG_CLI_RELEASES_REPO` using the following format:

    ```
    php-templateCopyEdit<ServerID>/<RemoteRepo>
    ```

    **Example**:\
    If your JPD is:\
    `https://artifactory-dev.us-east-1.d70888.aws.skycloud.gs/`\
    And you configure the server ID as `skycloud`, and the remote repository is `jfrog-release-remote`, then:

    ```bash
    bashCopyEditexport JFROG_CLI_RELEASES_REPO=skycloud/jfrog-release-remote
    ```

#### Frogbot

1. Set the standard Frogbot environment variables (e.g., `JF_URL`, `JF_ACCESS_TOKEN`, etc.) to connect to your JPD.
2.  Set the `JF_RELEASES_REPO` environment variable with the **remote repository name only**:

    ```bash
    bashCopyEditexport JF_RELEASES_REPO=jfrog-release-remote
    ```

#### IDE

1. The connected JPD will be used as the server.
2.  In the extension settings, set the `External Resources Repository` field to your repository name,\
    or provide the environment variable:

    ```bash
    bashCopyEditexport JFROG_IDE_RELEASES_REPO=jfrog-release-remote
    ```
