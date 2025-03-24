# Installation

Step 1: Set Up Repository Secrets

1. Go to **Settings** > **Secrets and variables** > **Actions**.
2. Add the following secrets:

| Secret Name               | Description                  | Notes                                                   |
| ------------------------- | ---------------------------- | ------------------------------------------------------- |
| `JF_URL`                  | JFrog platform URL           |                                                         |
| `JF_ACCESS_TOKEN`         | JFrog access token           | [OIDC](openid-connect-authentication.md) is recommended |
| `USER_TOKEN`              | GitHub personal access token | Must have `repo` and `read:packages` scopes             |
| `JF_USER` + `JF_PASSWORD` | JFrog user name and password |                                                         |

Step 2: Create a GitHub Actions Workflow

1. Create a new YAML workflow file: \
   `.github/workflows/frogbot.yml`
2.  Add the following workflow configuration and commit changes:

    ```yaml
    name: "Frogbot Security Scan"

    on:
      pull_request_target:
        types: [opened, synchronize]
      push:
        branches:
          - main
          - master
      schedule:
        - cron: "0 0 * * *"   # The repository will be scanned once a day at 00:00 GMT.

    permissions:
      pull-requests: write
      contents: write
      security-events: write
      # [Mandatory If using OIDC authentication protocol instead of JF_ACCESS_TOKEN]
      # id-token: write

    jobs:
      security-scan:
        runs-on: ubuntu-latest
        strategy:
          matrix:
            # The repository scanning will be triggered periodically on the following branches.
            branch: ["main"]
        steps:
          - uses: jfrog/frogbot@v2
            # [Mandatory if using OIDC authentication protocol instead of JF_ACCESS_TOKEN]
            # Insert to oidc-provider-name the 'Provider Name' defined in the OIDC integration configured in the JPD
            # with:
            #   oidc-provider-name: ""
            env:
              JF_URL: ${{ secrets.JF_URL }}
              JF_ACCESS_TOKEN: ${{ secrets.JF_ACCESS_TOKEN }}
              JF_GIT_TOKEN: ${{ secrets.GITHUB_TOKEN }}
              JF_GIT_BASE_BRANCH: ${{ matrix.branch }}    # For repository scan action
    ```
