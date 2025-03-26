# GitLab CI

Step 1: Set Up Repository Secrets

1. Go to **Settings** > **CI/CD** > **Variables**.
2. Add the following variables:

| Variable Name             | Purpose                                        | Notes                                                                    |
| ------------------------- | ---------------------------------------------- | ------------------------------------------------------------------------ |
| `JF_URL`                  | JFrog platform URL                             | Required for authentication                                              |
| `JF_ACCESS_TOKEN`         | JFrog access token                             | Alternative: Use `JF_USER` and `JF_PASSWORD`                             |
| `JF_GIT_TOKEN`            | GitLab personal access token (API permissions) | Must have `api`, `read_api`, `read_repository` , `write_reposity` scopes |
| `JF_USER` + `JF_PASSWORD` | JFrog user name and password                   | Alternative to the `JF_ACCESS_TOKEN` secret                              |

{% hint style="warning" %}
In the `gitlab-ci.yml` file, Make sure that either **JF\_USER** and **JF\_PASSWORD** or **JF\_ACCESS\_TOKEN** are set, **but not both**.
{% endhint %}

Step 2: Create the CI YAML File

1. Open your GitLab YAML `.gitlab-ci.yml` file in the route directory.
2. Add the following job to your GitLab pipeline configuration:

```
frogbot-scan:
 image: releases-docker.jfrog.io/jfrog-ecosystem-integration-env
 rules:
   - if: $CI_PIPELINE_SOURCE == 'merge_request_event'
     when: manual
     variables:
       FROGBOT_CMD: "scan-pull-request"
       JF_GIT_BASE_BRANCH: $CI_MERGE_REQUEST_TARGET_BRANCH_NAME
     # Repository scanning is triggered by any push to the default branch.
     # If you'd like a different branch to be scanned, replace $CI_DEFAULT_BRANCH in the line below with the name of the branch, wrapped with quotes (").
   - if: $CI_COMMIT_BRANCH == $CI_DEFAULT_BRANCH || $CI_PIPELINE_SOURCE == "schedule"
     variables:
       FROGBOT_CMD: "scan-repository"
       JF_GIT_BASE_BRANCH: $CI_COMMIT_BRANCH
 variables:
   # [Mandatory]
   # JFrog platform URL (This functionality requires version 3.29.0 or above of Xray)
   JF_URL: $JF_URL

   # [Mandatory if JF_USER and JF_PASSWORD are not provided]
   # JFrog access token with 'read' permissions for Xray
   JF_ACCESS_TOKEN: $JF_ACCESS_TOKEN

   # [Mandatory if JF_ACCESS_TOKEN is not provided]
   # JFrog user and password with 'read' permissions for Xray
   # JF_USER: $JF_USER
   # JF_PASSWORD: $JF_PASSWORD

   # [Mandatory]
   # GitLab access token. Ensure the token has the following permissions, depedending on your GiLab deployment type:
   # Self hosted: api, read_api, read_user, read_repository, write_repository.
   # Cloud: api, read_api, read_repository, write_repository
   JF_GIT_TOKEN: $JF_GIT_TOKEN

   # Predefined GitLab variables. There's no need to set them.
   JF_GIT_PROVIDER: gitlab
   JF_GIT_OWNER: $CI_PROJECT_NAMESPACE
   JF_GIT_REPO: $CI_PROJECT_NAME
   JF_GIT_PULL_REQUEST_ID: $CI_MERGE_REQUEST_IID

 script:
   # For Linux / MacOS runner:
   - |
     getFrogbotScriptPath=$(if [ -z "$JF_RELEASES_REPO" ]; then echo "https://releases.jfrog.io"; else echo "${JF_URL}/artifactory/${JF_RELEASES_REPO}"; fi)
     curl -fLg "$getFrogbotScriptPath/artifactory/frogbot/v2/[RELEASE]/getFrogbot.sh" | sh
     ./frogbot ${FROGBOT_CMD}

   # For Windows runner:
   #
   # - $getFrogbotScriptPath = $(if ([string]::IsNullOrEmpty($env:JF_RELEASES_REPO)) { "https://releases.jfrog.io" } else { "$($env:JF_URL)/artifactory/$($env:JF_RELEASES_REPO)" })
   # - Invoke-WebRequest -Uri "$getFrogbotScriptPath/artifactory/frogbot/v2/[RELEASE]/getFrogbot.sh" -UseBasicParsing | ForEach-Object { & $_.Content }
   # - .\frogbot ${FROGBOT_CMD}
```

3. (Optional) You may replace the `image: releases-docker.jfrog.io/jfrog-ecosystem-integration-env` configuration key to run your own image with the required technologies or manually install the technologies your project requires. The `image: releases-docker.jfrog.io/jfrog-ecosystem-integration-env`installs all the technologies Frogbot supports.
