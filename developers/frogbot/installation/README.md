# Installation

* [GitHub](github-actions/)[ Actions](github-actions/)
* [GitLab](gitlab-ci.md)[ CI](gitlab-ci.md)
* [Azure ](azure-devops.md)[DevOps](azure-devops.md)
* [Jenkins](jenkins.md)

#### Where Should the `frogbot-config.yml` File Be Placed in the Repository?

Frogbot expects the frogbot-config.yml file to be in the following path from the root of the Git repository: `.frogbot/frogbot-config.yml`.

{% hint style="info" %}
Frogbot only uses the `frogbot-config.yml` file if it already exists in the target branch. So, if a pull request adds the file but it's not yet present in the target branch, Frogbot will ignore it.
{% endhint %}
