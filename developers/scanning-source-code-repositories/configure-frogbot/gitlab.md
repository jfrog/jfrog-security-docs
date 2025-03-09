# GitLab

#### Step 1: Set Up Repository Secrets

1. Go to **Settings** > **CI/CD** > **Variables**.
2. Add the following variables:

| Variable Name     | Purpose                                        | Notes                                                 |
| ----------------- | ---------------------------------------------- | ----------------------------------------------------- |
| `JF_URL`          | JFrog platform URL                             | Required for authentication                           |
| `JF_ACCESS_TOKEN` | JFrog access token                             | Alternative: Use `JF_USER` and `JF_PASSWORD`          |
| `USER_TOKEN`      | GitLab personal access token (API permissions) | Must have `api`, `read_api`, `read_repository` scopes |

#### Step 2: Modify `.gitlab-ci.yml`

Add the following job to your GitLab pipeline configuration:

```
frogbot-scan:
  image: alpine
  before_script:
    - apk add --no-cache curl bash
  script:
    - |
      curl -fLg "https://releases.jfrog.io/artifactory/frogbot/v2/latest/getFrogbot.sh" | sh
      ./frogbot scan-repository --jfrog-url $JF_URL --jfrog-access-token $JF_ACCESS_TOKEN --git-token $USER_TOKEN
  variables:
    JF_URL: $JF_URL
    JF_ACCESS_TOKEN: $JF_ACCESS_TOKEN
    USER_TOKEN: $USER_TOKEN
```

#### Step 3: Commit and Push Changes

* This will trigger a security scan each time changes are pushed.
