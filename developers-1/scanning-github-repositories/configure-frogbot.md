# Configure Frogbot

The `frogbot-config.yml` file is a configuration file that allows you to define project-specific settings for Frogbot's scanning process. It plays an essential role when you want to manually control the structure of your project or specify specific package manager commands needed to list the project's dependencies. This file contains details about the repository's directory structure and can be used to configure how Frogbot scans and processes your project's dependencies.

## **Create the frogbot-config.yml File**

The `frogbot-config.yml` file encompasses project-related configurations used by Frogbot's scanning. This includes details about the repository's directory structure and may additionally encompass package manager commands necessary for Frogbot to list the project's dependencies.

1. Create a new file named `frogbot-config.yml` in the root directory of your repository.
2. Define your project configurations, including directory paths and package manager commands.

## **Determine if the frogbot-config.yml File is Needed**

The file isn't mandatory. In most cases, Frogbot can understand the structure of the projects in the repository and list the project's dependencies without the file. If your project doesn't use a `frogbot-config.yml` file, all the configuration Frogbot requires should be provided as variables as part of the Frogbot workflows.

1. Assess if your project has complex dependencies or if you require custom configurations.
2. If no custom configurations are needed, you can skip the `frogbot-config.yml` file and provide configurations via Frogbot workflows instead.

## **Configure frogbot-config.yml for Repository Scanning**

Frogbot relies on the project's descriptor files, such as `package.json` and `pom.xml`, to identify the project's dependencies. It scans the repository for these descriptor files and utilizes the appropriate package manager, such as npm or Maven, to compile a list of dependencies for the project. If you desire manual control over the project structure or the package manager commands, you can achieve this by creating a `frogbot-config.yml` file. In the provided example, we outline two subprojects located at `path/to/project-1` and `path/to/project-2` for Frogbot to include in its scanning process.

1. Identify your project descriptor files (e.g., `package.json`, `pom.xml`, etc.).
2. If needed, configure Frogbot to scan specific directories by defining the correct paths in the `frogbot-config.yml` file.
3. Customize the package manager commands in the `frogbot-config.yml` if necessary.

```yaml
yamlCopyEdit- params:
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

## **Use One frogbot-config.yml File for Multiple Git Repositories**

You have the option of using a single `frogbot-config.yml` file for scanning multiple Git repositories in the same organization if one of the following platforms is used:

* GitHub with Jenkins or JFrog Pipelines
* Bitbucket Server
* Azure Repos\
  The file can be placed in any repository if it's in the same organization as all the repositories referenced in the file. Here's an example of a `frogbot-config.yml` referencing multiple repositories.

1. Identify the Git repositories to be scanned in your organization.
2. Place the `frogbot-config.yml` file in one of the repositories within the organization.
3. Reference other repositories in the `frogbot-config.yml` file by specifying their names and branches.

```yaml
yamlCopyEdit- params:
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

***

## **Place the frogbot-config.yml File in the Correct Directory**

Frogbot expects the `frogbot-config.yml` file to be in the following path from the root of the Git repository: `.frogbot/frogbot-config.yml`.\
**IMPORTANT:** The `frogbot-config.yml` file must be pushed to the target branch before it can be used by Frogbot. This means that if, for example, a pull request includes the `frogbot-config.yml` and the target branch doesn't, the file will be ignored.

1. Ensure the `frogbot-config.yml` file is located in `.frogbot/` directory at the root of the repository.
2. Push the file to the target branch where Frogbot is expected to use it.
3. Verify that the file is available before initiating the scan.\
   The `frogbot-config.yml` file should be located at:

```arduino
arduinoCopyEdit.frogbot/frogbot-config.yml
```
