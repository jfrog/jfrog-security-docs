# Configure Frogbot

* [The frogbot-config.yml File Structure](the-frogbot-config.yml-file-structure.md)
* [Frogbot Optional Configuration Parameters](frogbot-optional-configuration-parameters.md)
* [Frogbot Offline](frogbot-offline.md)
* [Troubleshooting](../troubleshooting.md)

### Where Should the `frogbot-config.yml` File Be Placed in the Repository?

Frogbot expects the frogbot-config.yml file to be in the following path from the root of the Git repository: `.frogbot/frogbot-config.yml`.

{% hint style="info" %}
Frogbot only uses the `frogbot-config.yml` file if it already exists in the target branch. So, if a pull request adds the file but it's not yet present in the target branch, Frogbot will ignore it.
{% endhint %}

### Working in Air-Gapped Environments?

Follow the [Working in Air-Gapped Environments](../../working-in-air-gapped-environments.md) procedure.
