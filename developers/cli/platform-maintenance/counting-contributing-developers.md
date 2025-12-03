# Counting Contributing Developers

The `git count-contributors` command in JFrog CLI allows users to easily determine the number of Git developers contributing to a source code repository. This is based on unique email addresses from commit history, providing an accurate count of individual contributors according to the GIT provider API used by the JFrog CLI command.&#x20;

There are several options to obtain the developer count:&#x20;

* **A single code repository**: Analyze a single Git repository by providing the repository name.
* **Across a project/group**: Analyze multiple repositories organized under a project/group by providing the owner command option.&#x20;
* **Across multiple Git servers**: Analyze repositories across various Git servers by providing a YAML file as an input file with the required parameters outlined below.

**Command**: `git count-contributors`, `git cc`&#x20;

### Before You Begin

It is essential that you have:

* JFrog CLI 2.60.0
* One of the following supported git providers: GitHub, GitLab, Bitbucket

{% hint style="info" %}
The `git count-contributors` command does not use JFrog Artifactory data. Counts are based only on Git commit history, so some repositories and developers included may not interact with JFrog products
{% endhint %}

### Command Parameters

| Option               | Required | Default | Description                                                    | Example                                |
| -------------------- | -------- | ------- | -------------------------------------------------------------- | -------------------------------------- |
| `--scm-type`         | Yes      | —       | SCM type. One of: `github`, `gitlab`, `bitbucket`.             | `--scm-type=github`                    |
| `--scm-api-url`      | Yes      | —       | Base URL of the SCM API endpoint.                              | `--scm-api-url=https://api.github.com` |
| `--token`            | Yes      | —       | Authentication token for the SCM API.                          | `--token=<token>`                      |
| `--owner`            | Yes      | —       | Owner/organization (project/group) of the repositories.        | `--owner=my-org`                       |
| `--repo-name`        | No       | —       | **Semicolon-separated** list of repository names.              | `--repo-name=repo1;repo2`              |
| `--months`           | No       | `1`     | Number of months of commit history to analyze.                 | `--months=6`                           |
| `--detailed-summary` | No       | `false` | Include a detailed list of contributors in the output.         | `--detailed-summary=true`              |
| `--input-file`       | No       | —       | Path to YAML file describing **multiple** Git servers to scan. | `--input-file="/path/to/input.yaml"`   |
| `--verbose`          | No       | —       | Verbose output.                                                | `--verbose`                            |

### Examples

#### Single Repository

```
jf git count-contributors \
  --scm-type=github \
  --scm-api-url=https://api.github.com \
  --token=<token> \
  --repo-name=repo1
```

#### Owner/Project (Group) Level

```
jf git count-contributors \
  --scm-type=gitlab \
  --scm-api-url=https://gitlab.example.com \
  --token=<token> \
  --owner=my-group
```

#### Multiple Git Servers (YAML File)

```
git cc --input-file="/Users/path/to/input.yaml"
```

#### Sample YAML File

```
git-servers-list:
  - scm-type: bitbucket
    scm-api-url: "https://api.bitbucket.example.com"
    token: "token"
    owner: "owner"
    repositories:
      - "repo1"
      - "repo2"
  - scm-type: gitlab
    scm-api-url: "https://gitlab.example.com/api/v4"
    token: "token"
    owner: "owner"
```

#### Output

Typical fields include:

* **total\_unique\_contributors** — distinct contributors
* **total\_commits** — commits analyzed
* **scanned\_repos** — repositories scanned
* **report\_date** — ISO 8601 timestamp
* **number\_of\_months** — analysis window
* **unique\_contributors\_list** — when `--detailed-summary=true`
