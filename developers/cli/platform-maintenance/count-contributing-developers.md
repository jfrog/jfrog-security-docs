---
hidden: true
---

# Count Contributing Developers

The `git count-contributors` command in JFrog CLI allows users to easily determine the number of Git developers contributing to their code. This is based on unique email addresses from commit history, providing an accurate count of individual contributors.

There are several options to obtain the developer count:

* **A single repository**: Analyze a single Git repository by providing the repository name.
* **Across a project/group**: Analyze multiple repositories organized under a project/group by providing the owner command option.
* **Across multiple Git servers**: Analyze repositories across various Git servers by providing a YAML file as an input file with the required parameters outlined below.

**Command**: `jf git count-contributors`, `jf git cc`

## Before You Begin

* It is essential that you have:
  * JFrog CLI 2.60.0
  * One of the following supported git providers: GitHub, GitLab, Bitbucket

## Command Parameters

| Parameter            | Optional/Default          | Description                                                                                                   |
| -------------------- | ------------------------- | ------------------------------------------------------------------------------------------------------------- |
| `--scm-type`         | Mandatory                 | The type of SCM for analysis. Supported values: `github`, `gitlab`, `bitbucket`. Example: `--scm-type=github` |
| `--scm-api-url`      | Mandatory                 | Base URL of the SCM system's API endpoint. Example: `--scm-api-url=https://api.github.com`                    |
| `--token`            | Mandatory                 | Authentication token for accessing the SCM system's API. Example: `--token=your_access_token`                 |
| `--owner`            | Mandatory                 | Owner or organization of the repositories. Example: `--owner=your-organization`                               |
| `--repo-name`        | Optional                  | Semicolon-separated list of repositories. Example: `--repo-name=repo1;repo2`                                  |
| `--months`           | Optional (Default: 1)     | Number of months to analyze. Example: `--months=6`                                                            |
| `--detailed-summary` | Optional (Default: false) | Generates a detailed summary of contributors. Example: `--detailed-summary=true`                              |
| `--input-file`       | Optional                  | Path to a YAML file with multiple Git providers. Example: `--input-file="/path/to/input.yaml"`                |
| `--verbose`          | Optional                  | Enables verbose output for detailed information.                                                              |

## Examples <a href="#example-commands" id="example-commands"></a>

### **Single Repository**

<pre><code><strong>jf git cc --scm-type=github --scm-api-url=https://api.github.com --token=&#x3C;token> --repo-name=repo1
</strong></code></pre>

### **Group/Project Level**

```
jf git cc --scm-type=gitlab --scm-api-url=https://git.vdoo.io --token=<token> --owner=my-group
```

### **Multiple Git Servers (YAML File)**

```
jf git cc --input-file="/Users/path/to/input.yaml"
```

### **Sample YAML File**

```
git-servers-list:
  - scm-type: bitbucket
    scm-api-url: "https://api.bitbucket.url"
    token: "token"
    owner: "owner"
    repositories:
      - "repo1"
      - "repo2"
  - scm-type: gitlab
    scm-api-url: "https://api.gitlab.com"
    token: "token"
    owner: "owner"
```

### Sample Output

```
{
  "total_unique_contributors": 4,
  "total_commits": 4,
  "scanned_repos": ["repo1", "repo2"],
  "report_date": "2024-07-22T12:08:04+03:00",
  "number_of_months": "5",
  "unique_contributors_list": [
    { "email": "dev1@github.com", "name": "Developer 1" },
    { "email": "dev2@github.com", "name": "Developer 2" }
  ]
}
```

This output includes:

* **Total Unique Contributors:** Count of distinct contributors.
* **Total Commits:** Number of commits analyzed.
* **Scanned Repositories:** List of repositories scanned.
* **Contributor Details:** Names and emails of contributors.
