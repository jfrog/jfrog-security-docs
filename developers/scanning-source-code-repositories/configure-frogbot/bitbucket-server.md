# Bitbucket Server

#### Step 1: Configure Webhook

1. Go to **Repository Settings** > **Webhooks**.
2.  Add a new webhook with the following URL:

    ```
    https://[your-jenkins-domain]/generic-webhook-trigger/invoke
    ```
3. Enable **Pull Request Events**.

#### Step 2: Set Up Jenkins Integration (Optional)

If using Jenkins:

1. Install the **Generic Webhook Trigger** plugin.
2.  Configure a Jenkins job with the following script:

    ```
    pipeline {
        agent any
        environment {
            JF_URL = credentials('JF_URL')
            JF_ACCESS_TOKEN = credentials('JF_ACCESS_TOKEN')
        }
        stages {
            stage('Run Frogbot Scan') {
                steps {
                    sh '''
                      curl -fLg "https://releases.jfrog.io/artifactory/frogbot/v2/latest/getFrogbot.sh" | sh
                      ./frogbot scan-repository --jfrog-url $JF_URL --jfrog-access-token $JF_ACCESS_TOKEN
                    '''
                }
            }
        }
    }
    ```

***

###
