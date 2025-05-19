# Installation

Step 1: Set Up Repository Secrets

1. Go to **Settings** > **Secrets and variables** > **Actions**.
2. Add the following secrets:

| Secret Name               | Description                  | Notes                                                   |
| ------------------------- | ---------------------------- | ------------------------------------------------------- |
| `JF_URL`                  | JFrog platform URL           |                                                         |
| `JF_ACCESS_TOKEN`         | JFrog access token           | [OIDC](openid-connect-authentication.md) is recommended |
| `JF_GIT_TOKEN`            | GitHub personal access token | Must have `repo` and `read:packages` scopes             |
| `JF_USER` + `JF_PASSWORD` | JFrog user name and password | Alternative to the `JF_ACCESS_TOKEN` secret             |

Step 2: Allow Frogbot to open Pull Requests

1. In GitHub, navigate to the **Settings** tab.&#x20;
2. From the main menu, select **Actions** > **General** and check the **Allow GitHub Actions to create and approve pull requests** check box.

Step 3: Create an Execution Environment (Open Source Projects Only)

1. In GitHub, navigate to the **Settings** tab.
2. From the main menu, select **Environments** and click on **New environment**.\
   The Environments window opens.
3. Create a new [GitHub environment](https://docs.github.com/en/actions/deployment/targeting-different-environments/using-environments-for-deployment#creating-an-environment) named **frogbot.**
4. Add people or public teams as reviewers. \
   The chosen reviewers can trigger Frogbot scans on pull requests.

Step 4: Create a GitHub Actions Workflow

1. Create a new YAML workflow file: \
   `.github/workflows/frogbot.yml`
2. Add the following workflow configuration:

```
name: "Frogbot Security Scan"

on:
  pull_request_target: 
    types: [opened, synchronize] # Triggers scan-pr flow for every opened/updated pull request
  push: # Triggers scan-repo flow for every push to the specified branches
    branches:
      - main
  schedule:
    - cron: "0 0 * * *"   # The repository will be scanned once a day at 00:00 GMT.
  workflow_dispatch: # The repository will be scanned on demand

permissions:
  pull-requests: write
  contents: write
  security-events: write
  # [Mandatory If using OIDC authentication protocol instead of JF_ACCESS_TOKEN]
  # id-token: write

jobs:
  frogbot-scan:
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
          JF_GIT_TOKEN: ${{ secrets.JF_GIT_TOKEN }}
          JF_GIT_BASE_BRANCH: ${{ matrix.branch }}    # For repository scan action
```

3. Before setting up Frogbot, ensure all required tools and technologies are installed on your system and are available in your system's `$PATH`.&#x20;
