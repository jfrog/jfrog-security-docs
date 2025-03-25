# Supported Technologies

### SCM and CI Requirements

#### Operating System

Frogbot scanners support the following operating systems:

* Ubuntu 18+
* RHEL 8+
* Windows

#### Required Packages&#x20;

Ensure the following packages are available in your environment:

* **Unzip**
* **Glibc-2.33+**
* **curl**
* **Git**

{% hint style="info" %}
The above packages are included in the standard base images (e.g., Ubuntu, RHEL). Still, if you are using lighter images like Alpine, you will need to ensure these packages are installed.
{% endhint %}

#### Advanced Security Supported Technologies

See Jfrog Advanced Security Supported Technologies section:

* SAST
* Contextual analysis&#x20;
* Secrets
* IaC

#### **Software Composition Analysis (SCA)** Supported Technologies

{% hint style="info" %}
* For SCA, the command automatically detects the package manager used by your project and uses it to construct the dependency graph.
* If the project hasn’t been installed yet, the system will execute an install command to generate the dependency tree for scanning.
{% endhint %}

#### **Supported Git Providers and CI**

JFrog Frogbot integrates seamlessly with various Git providers and Continuous Integration (CI) systems, ensuring that your development workflow remains efficient and secure. Below is a list of supported platforms:

#### **Supported Git Providers**

JFrog Frogbot is compatible with the following Git providers:

| **Git Provider**                    | **Supported** |
| ----------------------------------- | ------------- |
| GitHub (Cloud and Self-Hosted)      | ✔️            |
| GitLab (Cloud and Self-Hosted)      | ✔️            |
| Azure Repos (Cloud and Self-Hosted) | ✔️            |
| Bitbucket Server (Self-Hosted)      | ✔️            |

#### **Supported CI Systems**

Frogbot can also integrate with multiple CI systems, enhancing your security scanning capabilities:

| **CI System**       | **Supported** |
| ------------------- | ------------- |
| GitHub Actions      | ✔️            |
| GitLab CI           | ✔️            |
| Azure Pipelines     | ✔️            |
| Bitbucket Pipelines | ✔️            |
| Jenkins             | ✔️            |
