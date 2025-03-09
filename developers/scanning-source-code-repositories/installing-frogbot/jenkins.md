# Jenkins

## Step 1: Install Required Plugin

1. In Jenkins, go to **Manage Jenkins** > **Manage Plugins**.
2. In the Available tab, search for the **Generic Webhook Trigger** plugin.
3. Select Install.

## Step 2: Configure Webhook

1. Navigate to **Repository Settings** in your Git provider.
2.  Add a new webhook with this URL:

    ```
    https://[your-jenkins-domain]/generic-webhook-trigger/invoke?token=[your-token]
    ```

## Step 3: Configure Jenkins Pipeline

Use the following Jenkinsfile:

```
pipeline {
    agent any
    triggers {
        cron('0 0 * * *')
    }
    environment {
        JF_URL = credentials('JF_URL')
        JF_ACCESS_TOKEN = credentials('JF_ACCESS_TOKEN')
        JF_GIT_TOKEN = credentials('JF_GIT_TOKEN')
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
