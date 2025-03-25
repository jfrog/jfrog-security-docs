# Installation

### Step 1: Provide Connection Details

Go to your repository's **settings** tab and save the JFrog connection details as repository secrets with the following names:

| Secret Name               | Description                  | Notes                                                                            |
| ------------------------- | ---------------------------- | -------------------------------------------------------------------------------- |
| `JF_URL`                  | JFrog platform URL           | You may also use `JF_XRAY_URL` and `JF_ARTIFACTORY_URL` instead of `JF_URL`**.** |
| `JF_ACCESS_TOKEN`         | JFrog access token           | [OIDC](openid-connect-authentication.md) is recommended                          |
| `USER_TOKEN`              | GitHub personal access token | Must have `repo` and `read:packages` scopes                                      |
| `JF_USER` + `JF_PASSWORD` | JFrog user name and password |                                                                                  |

### Step 2: Allow Frogbot to Open Pull Requests

Under **Actions** > **General**, check the **Allow GitHub Actions to create and approve pull requests** check box.

### Step 3: Create an Execution Environment (open source projects only)

Create a new [GitHub environment](https://docs.github.com/en/actions/deployment/targeting-different-environments/using-environments-for-deployment#creating-an-environment) called **frogbot** and add people or public teams as reviewers. \
The chosen reviewers can trigger Frogbot scans on pull requests.

## Create the Required GitHub Actions Templates

### Step 1: Navigate to the Project You Wish to Scan&#x20;

1. Clone the GitHub repository you wish to scan to your local environment:

```
> git clone <my-project.git>
> cd <my-project>
```

2. Switch to the branch you'd like to scan with Frogbot:

```
> git checkout <branch-to-scan>
```

### Step 2: Set Up Repository Scan

1. In the branch you'd like to scan, create a file named `frogbot-scan-repository.yml`.&#x20;
2. Fill it with the provided [template](installation.md#basic-frogbot-scan-repository.yml-template) and push it into the `.github/workflows` directory at the root of your GitHub repository.\
   For advanced options, see the [full scan repository template](scan-pull-request-full-template.md).

`frogbot-scan-repository.yml` template:

```
name: "Frogbot Scan Repository"
on:
  workflow_dispatch:
  schedule:
    # The repository will be scanned once a day at 00:00 GMT.
    - cron: "0 0 * * *"
permissions:
  contents: write
  pull-requests: write
  security-events: write
  # [Mandatory If using OIDC authentication protocol instead of JF_ACCESS_TOKEN]
  # id-token: write
jobs:
  scan-repository:
    runs-on: ubuntu-latest
    strategy:
      matrix:
        # The repository scanning will be triggered periodically on the following branches.
        branch: ["dev"]
    steps:
      - uses: jfrog/frogbot@v2
        env:
          # [Mandatory]
          # JFrog platform URL
          JF_URL: ${{ secrets.JF_URL }}

          # [Mandatory if JF_USER and JF_PASSWORD are not provided]
          # JFrog access token with 'read' permissions on Xray service
          JF_ACCESS_TOKEN: ${{ secrets.JF_ACCESS_TOKEN }}

          # [Mandatory if JF_ACCESS_TOKEN is not provided]
          # JFrog username with 'read' permissions for Xray. Must be provided with JF_PASSWORD
          # JF_USER: ${{ secrets.JF_USER }}

          # [Mandatory if JF_ACCESS_TOKEN is not provided]
          # JFrog password. Must be provided with JF_USER
          # JF_PASSWORD: ${{ secrets.JF_PASSWORD }}

          # [Mandatory]
          # The GitHub token is automatically generated for the job
          JF_GIT_TOKEN: ${{ secrets.GITHUB_TOKEN }}

          # [Mandatory]
          # The name of the branch on which Frogbot will perform the scan
          JF_GIT_BASE_BRANCH: ${{ matrix.branch }}

        # [Mandatory if using OIDC authentication protocol instead of JF_ACCESS_TOKEN]
        # Insert to oidc-provider-name the 'Provider Name' defined in the OIDC integration configured in the JPD
        # with:
        #   oidc-provider-name: ""
```

### Step 3: Set Up Pull Request Scan

1. Create a file named `frogbot-scan-pull-request.yml`.&#x20;
2. Fill it with the provided [template](installation.md#basic-frogbot-scan-pull-request.yml-template), and then push it into the `.github/workflows` directory at the root of your GitHub repository.\
   For advanced options, see the [full scan repository template](scan-pull-request-full-template.md).

`frogbot-scan-pull-request.yml` template:

```
name: "Frogbot Scan Pull Request"
on:
  pull_request_target:
    types: [opened, synchronize]
permissions:
  pull-requests: write
  contents: read
  # [Mandatory If using OIDC authentication protocol instead of JF_ACCESS_TOKEN]
  # id-token: write
jobs:
  scan-pull-request:
    runs-on: ubuntu-latest
    # A pull request needs to be approved before Frogbot scans it. Any GitHub user who is associated with the
    # "frogbot" GitHub environment can approve the pull request to be scanned.
    environment: frogbot
    steps:
      - uses: jfrog/frogbot@v2
        env:
          # [Mandatory]
          # JFrog platform URL
          JF_URL: ${{ secrets.JF_URL }}

          # [Mandatory if JF_USER and JF_PASSWORD are not provided]
          # JFrog access token with 'read' permissions on Xray service
          JF_ACCESS_TOKEN: ${{ secrets.JF_ACCESS_TOKEN }}

          # [Mandatory if JF_ACCESS_TOKEN is not provided]
          # JFrog username with 'read' permissions for Xray. Must be provided with JF_PASSWORD
          # JF_USER: ${{ secrets.JF_USER }}

          # [Mandatory if JF_ACCESS_TOKEN is not provided]
          # JFrog password. Must be provided with JF_USER
          # JF_PASSWORD: ${{ secrets.JF_PASSWORD }}

          # [Mandatory]
          # The GitHub token is automatically generated for the job
          JF_GIT_TOKEN: ${{ secrets.GITHUB_TOKEN }}
          
        # [Mandatory if using OIDC authentication protocol instead of JF_ACCESS_TOKEN]
        # Insert to oidc-provider-name the 'Provider Name' defined in the OIDC integration configured in the JPD
        # with:
        #   oidc-provider-name: ""
```
