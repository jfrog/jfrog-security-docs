# Configure Frogbot

## Using GitLab CI

### **Prepare GitLab to Work with Frogbot**

#### **Step 1: Provide Connection Details**

In your GitLab repository settings, save the following JFrog connection details as repository secrets:

| **Purpose**         | **Secret Name**   | **Notes**                                                                              |
| ------------------- | ----------------- | -------------------------------------------------------------------------------------- |
| JFrog Platform URL  | `JF_URL`          |                                                                                        |
| JFrog Access Token  | `JF_ACCESS_TOKEN` | Alternatively, use`JF_USER + JF_PASSWORD`. Ensure tokens are not set as protected.     |
| GitLab Access Token | `USER_TOKEN`      | Ensure it has the required permissions (api, read\_api, read\_user, read\_repository). |

#### **2. Add Frogbot to Your .gitlab-ci.yml File**

Add the following job to your `.gitlab-ci.yml` file:

{% code overflow="wrap" %}
```yaml
frogbot-scan:
  rules:
    - if: $CI_PIPELINE_SOURCE == 'merge_request_event'
      when: manual
      variables:
        FROGBOT_CMD: "scan-pull-request"
        JF_GIT_BASE_BRANCH: $CI_MERGE_REQUEST_TARGET_BRANCH_NAME
    - if: $CI_COMMIT_BRANCH $CI_DEFAULT_BRANCH || $CI_PIPELINE_SOURCE == "schedule"
      variables:
        FROGBOT_CMD: "scan-repository"
        JF_GIT_BASE_BRANCH: $CI_COMMIT_BRANCH
  variables:
    JF_URL: $JF_URL
    JF_ACCESS_TOKEN: $JF_ACCESS_TOKEN
    JF_GIT_TOKEN: $USER_TOKEN
    JF_GIT_PROVIDER: gitlab
    JF_GIT_OWNER: $CI_PROJECT_NAMESPACE
    JF_GIT_REPO: $CI_PROJECT_NAME
    JF_GIT_PULL_REQUEST_ID: $CI_MERGE_REQUEST_IID
    JF_INSTALL_DEPS_CMD: ""
  script:
    - |
      getFrogbotScriptPath=$(if [ -z "$JF_RELEASES_REPO" ]; then echo "https://releases.jfrog.io"; else echo "${JF_URL}/artifactory/${JF_RELEASES_REPO}"; fi)
      curl -fLg "$getFrogbotScriptPath/artifactory/frogbot/v2/[RELEASE]/getFrogbot.sh" | sh
      ./frogbot ${FROGBOT_CMD}
```
{% endcode %}

### Setup Frogbot Using Jenkins

#### **1. Install the Required Jenkins Plugin**

1. Navigate to **Manage Jenkins** > **Manage Plugins** from your Jenkins dashboard.
2. Select the **Available** tab and search for **Generic Webhook Trigger** .
3. Install the plugin. Learn more about the plugin.

#### **2. Set Up a Webhook**

You need to configure a webhook for your Git provider to trigger the Jenkins job for Frogbot.

**GitHub**

* Go to your repository **Settings** > **Webhooks** > **Add webhook** .
* Set the URL to: `https://[your-jenkins-domain]/generic-webhook-trigger/invoke`.

**Bitbucket Server**

* Go to **Repository settings** > **Webhooks** > **Create new webhook** .
* Set the webhook URL: `https://[your-jenkins-domain]/generic-webhook-trigger/invoke`.

**GitLab**

* Go to **Project Settings** > **Webhooks** > **Add webhook** .
* Set the URL: `https://[your-jenkins-domain]/generic-webhook-trigger/invoke`.
* Enable **Merge request events** .

**Azure Repos**

* Follow this guide to set up the webhook using the same URL pattern: `https://[your-jenkins-domain]/generic-webhook-trigger/invoke`.

#### Configuring Frogbot for Jenkins

**API Token for Webhooks**

To ensure your Frogbot webhook only triggers specific Jenkins jobs:

1. Generate a **dedicated API token** in your Git provider.
2. Add this token to the webhook URL: `https://[your-jenkins-domain]/generic-webhook-trigger/invoke?token=[your-token]`. Refer to the Jenkins documentation for more details on triggering specific jobs.

**Jenkins Credentials**

Configure the following credentials as **Secret Text** in Jenkins:

| **Purpose**        | **Secret Name**   | **Notes**                                                                          |
| ------------------ | ----------------- | ---------------------------------------------------------------------------------- |
| JFrog Platform URL | `JF_URL`          |                                                                                    |
| JFrog Access Token | `JF_ACCESS_TOKEN` | Alternatively, use`JF_USER + JF_PASSWORD`. Ensure tokens are not set as protected. |
| Git Access Token   | `JF_GIT_TOKEN`    | Git access token with read/write permissions.                                      |

Ensure your Jenkins agent has the necessary package managers (e.g., npm, Go, Python) installed.

#### Jenkins Pipeline Job Configuration

**Generic Webhook Trigger Setup**

Enable **Generic Webhook Trigger** for your Jenkins job and use the following **Pipeline script template** :

```yaml
// Define your CRON schedule here
CRON_SETTINGS = '''0 0 * * *''' // Runs once a day at midnight

pipeline {
    agent any

    triggers {
        cron(CRON_SETTINGS)
        GenericTrigger(
            genericVariables: [
                // Define your Git provider-specific variables here
                // Uncomment and customize as needed
            ],
            causeString: 'Triggered by Pull Request',
            printContributedVariables: false,
            token: 'MyJobToken'
        )
    }

    environment {
        JF_GIT_PROVIDER = "CHOOSE_ONE_OF_THE_FOLLOWING" // Select your git provider
        JF_URL = credentials("JF_URL")
        JF_ACCESS_TOKEN = credentials("JF_ACCESS_TOKEN")
        JF_GIT_TOKEN = credentials("JF_GIT_TOKEN")
    }

    stages {
        stage('Check Trigger') {
            steps {
                script {
                    if (env.TRIGGER_KEY != null && env.TRIGGER_KEY != 'synchronize') {
                        error('Invalid trigger event for PR. Aborting pipeline.')
                    }
                }
            }
        }

        stage('Download Frogbot') {
            steps {
                script {
                    if (env.JF_RELEASES_REPO == "") {
                        sh """ curl -fLg "https://releases.jfrog.io/artifactory/frogbot/v2/[RELEASE]/getFrogbot.sh" | sh """
                    } else {
                        sh """ curl -fLg "$env.JF_URL/artifactory/$env.JF_RELEASES_REPO/artifactory/frogbot/v2/[RELEASE]/getFrogbot.sh" | sh """
                    }
                }
            }
        }

        stage('Scan Pull Request or Repository') {
            steps {
                script {
                    if (env.TRIGGER_KEY != null) {
                        sh "./frogbot scan-pull-request"
                    } else {
                        sh "./frogbot scan-repo"
                    }
                }
            }
        }
    }
}
```

## Using Azure Pipelines

## **Before You Begin**

Configure the following environment variables:

| **Purpose**        | **Secret Name**   | **Notes**                                                                          |
| ------------------ | ----------------- | ---------------------------------------------------------------------------------- |
| JFrog Platform URL | `JF_URL`          |                                                                                    |
| JFrog Access Token | `JF_ACCESS_TOKEN` | Alternatively, use`JF_USER + JF_PASSWORD`. Ensure tokens are not set as protected. |
| Git Access Token   | `JF_GIT_TOKEN`    | Git access token with read/write permissions.                                      |

### **Setup**

1. **Navigate to Azure Pipelines**\
   Open your Azure Pipelines project and add a new pipeline.
2. **Select Azure Repos Git as the Code Source**\
   Choose the repository where the Frogbot pipeline will reside.
3. **Select Starter Pipeline**\
   Name the pipeline `frogbot`.
4. **Configure the Pipeline**\
   Use the template below to set up the pipeline configuration. Ensure that the mandatory variables are properly edited.

#### **Pipeline Configuration Example**

```yaml
schedules:
  - cron: '0 0 * * *'
    displayName: Daily midnight build
    branches:
      include:
        - main

pr: none
trigger: none

pool:
  vmImage: ubuntu-latest

variables:
    # Predefined Azure Pipelines variables. There's no need to modify them.
    JF_GIT_PROJECT: $(System.TeamProject)
    JF_GIT_REPO: $(Build.Repository.Name)
    JF_GIT_API_ENDPOINT: $(System.CollectionUri)
    JF_GIT_BASE_BRANCH: $(Build.SourceBranchName)
    JF_GIT_OWNER: $(System.TeamProject)
    JF_GIT_PROVIDER: 'azureRepos'

jobs:
  - job:
      displayName: "Frogbot Scan Repository and Fix"
      steps:
        - task: CmdLine@2
          displayName: 'Download and Run Frogbot'
          env:
            # [Mandatory]
            # JFrog platform URL (This functionality requires version 3.29.0 or above of Xray)
            JF_URL: $(JF_URL)

            # [Mandatory if JF_USER and JF_PASSWORD are not provided]
            JF_ACCESS_TOKEN: $(JF_ACCESS_TOKEN)

            # [Mandatory if JF_ACCESS_TOKEN is not provided]
            # JF_USER: $JF_USER
            # JF_PASSWORD: $JF_PASSWORD

            # [Mandatory]
            JF_GIT_TOKEN: $(JF_GIT_TOKEN)

            # [Optional]
            # JF_RELEASES_REPO: ""

            # [Mandatory if project uses yarn 2, NuGet, or .NET and installCommand isn't set in frogbot-config.yml]
            # JF_INSTALL_DEPS_CMD: ""

            # [Optional, default: "."]
            # JF_WORKING_DIR: maven

            # [Default: "*.git*;*node_modules*;*target*;*venv*;*test*"]
            # JF_PATH_EXCLUSIONS: "*.git*;*node_modules*;*target*;*venv*;*test*"

            # [Optional]
            # JF_WATCHES: <watch-1>,<watch-2>...<watch-n>

            # [Optional]
            # JF_PROJECT: <project-key>

            # [Optional, Default: "FALSE"]
            # JF_INCLUDE_ALL_VULNERABILITIES: "TRUE"

            # [Optional, Default: "FALSE"]
            # JF_AVOID_PREVIOUS_PR_COMMENTS_DELETION: "TRUE"

            # [Optional, Default: "TRUE"]
            # JF_FAIL: "FALSE"

            # [Optional, Default: "FALSE"]
            # JF_REQUIREMENTS_FILE: ""

            # [Optional, Default: "TRUE"]
            # JF_USE_WRAPPER: "FALSE"

            # [Optional]
            # JF_DEPS_REPO: ""

            # [Optional]
            # JF_BRANCH_NAME_TEMPLATE: "frogbot-${IMPACTED_PACKAGE}-${BRANCH_NAME_HASH}"

            # [Optional]
            # JF_COMMIT_MESSAGE_TEMPLATE: "Upgrade ${IMPACTED_PACKAGE} to ${FIX_VERSION}"

            # [Optional]
            # JF_PULL_REQUEST_TITLE_TEMPLATE: "[🐸 Frogbot] Upgrade ${IMPACTED_PACKAGE} to ${FIX_VERSION}"

            # [Optional, Default: "FALSE"]
            # JF_GIT_AGGREGATE_FIXES: "FALSE"

            # [Optional, Default: "FALSE"]
            # JF_FIXABLE_ONLY: "TRUE"

            # [Optional]
            # JF_MIN_SEVERITY: ""

            # [Optional, Default: eco-system+frogbot@jfrog.com]
            # JF_GIT_EMAIL_AUTHOR: ""

            # [Optional]
            # JF_ALLOWED_LICENSES: "MIT, Apache-2.0"

            # [Optional]
            # JF_AVOID_EXTRA_MESSAGES: "TRUE"

            # [Optional]
            # JF_PR_COMMENT_TITLE: ""

          inputs:
            script: |
              getFrogbotScriptPath=$(if [ -z "$JF_RELEASES_REPO" ]; then echo "https://releases.jfrog.io"; else echo "${JF_URL}/artifactory/${JF_RELEASES_REPO}"; fi)
              curl -fLg "$getFrogbotScriptPath/artifactory/frogbot/v2/[RELEASE]/getFrogbot.sh" | sh
              ./frogbot cfpr
```

\


