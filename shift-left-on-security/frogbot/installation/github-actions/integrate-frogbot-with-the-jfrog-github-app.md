# Integrate Frogbot with the JFrog GitHub App

This procedure guides you through integrating JFrog Frogbot with your GitHub repositories using the JFrog GitHub App. By completing this integration, Frogbot will be configured to continuously monitor your selected repositories—commenting on security issues directly in pull requests, and even creating fix pull requests for vulnerable dependencies.

### Before You Begin

* Make sure the [JFrog GitHub App](https://jfrog.com/help/r/jfrog-platform-administration-documentation/integration-with-github) is installed
* Supported for Xray version 3.128.3 and above

{% hint style="info" %}
This integration is supported only for repositories under a GitHub Organization. Personal repositories under individual user accounts are not supported
{% endhint %}

### Integration

1. Navigate to **Administration** > **Xray Settings** > **Indexed Resources**, and open the **Git Repositories** tab.
2. Select **Add Git Repositories** and choose how to integrate Frogbot with your repositories:

* **Automatic Integration**\
  Use the JFrog GitHub App to automatically configure Frogbot with GitHub Actions.
* **Manual Integration**\
  Prefer to set things up yourself? Follow the Frogbot documentation for detailed instructions.

3. Under the Select **GitHub Repositories** tab, choose the repositories you want Frogbot to integrate with and scan.\
   JFrog will handle the setup automatically, including:

* Opening a pull request in each selected repository with the Frogbot workflow YAML file.
* Adding the required secrets needed for Frogbot execution.

4. (Optional): Choose whether to **Automatically merge the Frogbot YAML file** into your repositories:

* If enabled, the workflow file will be merged automatically once the pull request is created.
* If disabled, you will need to manually review and approve each pull request before Frogbot becomes active in the repository.

5. To begin the integration process, select **Integrate Frogbot**.
6. The **View Pull Requests** tab opens.\
   Here, you can:

* See whether each pull request was successfully merged or failed.
* Select any item in the table to open the corresponding commit page on GitHub.

### What the Frogbot Workflow Does

The Frogbot YAML file is automatically added to each selected repository and sets up a workflow that protects the main branch by scanning every commit pushed to it and every pull request opened against it. The workflow also requests the necessary permissions to open fix pull requests and add comments to PRs with any security issues it detects.

#### Frogbot Workflow Template

```
name: "Frogbot Security Scan"

on:
  pull_request_target: 
    types: [opened, synchronize]
  push:
    branches:
      - main
  workflow_dispatch:

permissions:
  pull-requests: write
  contents: write
  security-events: write

jobs:
  frogbot-scan:
    runs-on: ubuntu-latest
    strategy:
      matrix:
        branch: ["main"]
    steps:
      - uses: jfrog/frogbot@v2
        env:
          JF_URL: ${{ secrets.JF_URL }}
          JF_ACCESS_TOKEN: ${{ secrets.JF_ACCESS_TOKEN }}
          JF_GIT_TOKEN: ${{ secrets.JF_GIT_TOKEN }}
          JF_GIT_BASE_BRANCH: ${{ matrix.branch }}
```

### Next Steps

1. Configure and manage your [repositories' scan settings](https://jfrog.com/help/r/jfrog-security-user-guide/shift-left-on-security/git-repository-scans-and-results/git-repository-configuration).
2. [View scan results](https://jfrog.com/help/r/jfrog-security-user-guide/shift-left-on-security/git-repository-scans-and-results/view-git-repository-scan-results).
