# The frogbot-config.yml File Structure

See the complete content and structure of the **frogbot-config.yml** file [here](yaml-file.md).

{% hint style="info" %}
If your Git repository uses `main` instead of `master` as the default branch, be sure to update the `branches` field in your YAML file accordingly.
{% endhint %}

### Create The `frogbot-config.yml` File

#### What is the `frogbot-config.yml` File?

The **frogbot-config.yml** file encompasses project-related configurations used by Frogbot's scanning. This includes details about the repository's directory structure and may additionally encompass package manager commands necessary for Frogbot to list the project's dependencies.

#### Is the `frogbot-config.yml` File Mandatory?

No, the file isn't mandatory. In most cases, Frogbot can understand the structure of the projects in the repository and list the project's dependencies without the file.

If your project doesn't use a **frogbot-config.yml** file, all the configuration Frogbot requires\
should be provided as variables as part of the Frogbot workflows.

**How Does the `frogbot-config.yml` File Helps Frogbot Scan Repositories?**

Frogbot relies on the project's descriptor files, such as package.json and pom.xml, to identify the project's dependencies. It scans the repository for these descriptor files and utilizes the appropriate package manager, such as npm or Maven, to compile a list of dependencies for the project. If you desire manual control over the project structure or the package manager commands, you can achieve this by creating a **frogbot-config.yml** file. In the provided example, we outline two subprojects located at **path/to/project-1** and **path/to/project-2** for Frogbot to include in its scanning process.

```
- params:
    git:
      repoName: my-git-repo-name
      branches:
        - master
    scan:
      projects:
        - workingDirs:
            - path/to/npm/project-1
            - path/to/npm/project-2
```

Here's another example. Notice that we specify a custom `install` command here.

```
- params:
    git:
      repoName: my-git-repo-name
      branches:
        - master
    scan:
      projects:
        - workingDirs:
            - path/to/node/project
        - installCommand: nuget restore
          workingDirs:
            - path/to/.net/project
```

#### Can One `frogbot-config.yml` File Be Used for Multiple Git Repositories?

You have the option of using a single **frogbot-config.yml** file for scanning multiple Git repositories in the same organization if one of the following platforms is used.

* GitHub with Jenkins
* Bitbucket Server
* Azure Repos

The file can be placed in any repository if it's in the same organization as all the repositories referenced in the file. Here's an example of a **frogbot-config.yml** referencing multiple repositories.

```
- params:
    git:
      repoName: repo-1
      branches:
        - master
- params:
    git:
      repoName: repo-2
      branches:
        - master
        - dev
- params:
    git:
      repoName: repo-3
      branches:
        - master
    scan:
      projects:
        - pipRequirementsFile: requirements.txt
```

If however you're using one of the following platforms, each repository that needs to be scanned by Frogbot should include its own **frogbot-config.yml** file.

* GitHub with GitHub actions
* GitLab
