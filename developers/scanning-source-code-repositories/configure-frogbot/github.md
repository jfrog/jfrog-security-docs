# GitHub

#### Step 1: Set Up Repository Secrets

1. Go to **Settings** > **Secrets and variables** > **Actions**.
2. Add the following secrets:

| Secret Name       | Purpose                      | Notes                                        |
| ----------------- | ---------------------------- | -------------------------------------------- |
| `JF_URL`          | JFrog platform URL           | Required for authentication                  |
| `JF_ACCESS_TOKEN` | JFrog access token           | Alternative: Use `JF_USER` and `JF_PASSWORD` |
| `USER_TOKEN`      | GitHub personal access token | Must have `repo` and `read:packages` scopes  |

#### Step 2: Create a GitHub Actions Workflow

1. Navigate to `.github/workflows` in your repository.
2. Create a new YAML file, e.g., `frogbot.yml`.
3.  Add the following workflow configuration:

    ```
    name: Frogbot Scan
    on:
      pull_request:
      push:
        branches:
          - main
    jobs:
      frogbot_scan:
        runs-on: ubuntu-latest
        steps:
          - name: Checkout Code
            uses: actions/checkout@v3
          - name: Set up JFrog CLI
            run: |
              curl -fL https://getcli.jfrog.io | sh
              chmod +x jfrog
              mv jfrog /usr/local/bin/
          - name: Download and Run Frogbot
            run: |
              curl -fLg "https://releases.jfrog.io/artifactory/frogbot/v2/latest/getFrogbot.sh" | sh
              ./frogbot scan-repository --jfrog-url $JF_URL --jfrog-access-token $JF_ACCESS_TOKEN --git-token $USER_TOKEN
    ```

#### Step 3: Commit and Push Changes

* Push the file to your repository. The workflow will now trigger scans automatically on pull requests and pushes.
