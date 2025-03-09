# Azure Repos

#### Step 1: Create a Pipeline in Azure DevOps

1. Navigate to **Pipelines** in Azure DevOps.
2. Click **New Pipeline**.
3. Select **Azure Repos Git** as the source.

#### Step 2: Add the Pipeline Configuration

Use the following YAML template:

```
trigger:
  branches:
    include:
      - main
pool:
  vmImage: ubuntu-latest
steps:
  - script: |
      curl -fLg "https://releases.jfrog.io/artifactory/frogbot/v2/latest/getFrogbot.sh" | sh
      ./frogbot scan-repository --jfrog-url $(JF_URL) --jfrog-access-token $(JF_ACCESS_TOKEN)
    env:
      JF_URL: $(JF_URL)
      JF_ACCESS_TOKEN: $(JF_ACCESS_TOKEN)
```

#### Step 3: Save and Run the Pipeline

* This will trigger a security scan whenever a push is made to the `main` branch.

***

###
