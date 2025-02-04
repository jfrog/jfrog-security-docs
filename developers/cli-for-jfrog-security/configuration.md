# Configuration

## Web Login to the JFrog Platform

You can use the `jf login` command to authenticate with the JFrog Platform through the web browser. This command is solely interactive, meaning it does not receive any options and cannot be used in a CI server.

## Creating Access Tokens

This command allows creating [Access Tokens](https://jfrog.com/help/r/jfrog-platform-administration-documentation/access-tokens) for users in the JFrog Platform. By default, a user-scoped token will be created. Administrators may provide the scope explicitly with `--scope`, or implicitly with `--groups`, `--grant-admin`.

### Commands Params

| Command                      | Default | Description                                                                                                                                                                                                                                                                                                                                                       |
| ---------------------------- | ------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Command Name**             |         |                                                                                                                                                                                                                                                                                                                                                                   |
| `access-token-create`, `atc` |         |                                                                                                                                                                                                                                                                                                                                                                   |
| **Command Arguments**        |         |                                                                                                                                                                                                                                                                                                                                                                   |
| `username`                   |         | The username for which this token is created. If not specified, the token will be created for the current user.                                                                                                                                                                                                                                                   |
| **Command Options**          |         |                                                                                                                                                                                                                                                                                                                                                                   |
| `--audience`                 |         | <p>[Optional]</p><p>A space-separated list of the other instances or services that should accept this token identified by their Service-IDs.</p>                                                                                                                                                                                                                  |
| `--description`              |         | <p>[Optional]</p><p>Free text token description. Useful for filtering and managing tokens. Limited to 1024 characters.</p>                                                                                                                                                                                                                                        |
| `--expiry`                   |         | <p>[Optional]</p><p>The amount of time, in seconds it would take for the token to expire. Must be non-negative. If not provided, the platform default will be used. To specify a token that never expires, set to zero. Non-admin may only set a value that is equal or lower than the platform default that was set by an administrator (1 year by default).</p> |
| `--grant-admin`              | `false` | Set to `true` to provide admin privileges to the access token. This is only available for administrators.                                                                                                                                                                                                                                                         |
| `--groups`                   |         | <p>[Optional]</p><p>A list of comma-separated(,) groups for the access token to be associated with. This is only available for administrators.</p>                                                                                                                                                                                                                |
| `--project`                  |         | <p>[Optional]</p><p>The project for which this token is created. Enter the project name on which you want to apply this token.</p>                                                                                                                                                                                                                                |
| `--reference`                | `false` | Generate a Reference Token (alias to Access Token) in addition to the full token (available from Artifactory 7.38.10).                                                                                                                                                                                                                                            |
| `--refreshable`              | `false` | Set to `true` if you'd like the token to be refreshable. A refresh token will also be returned in order to be used to generate a new token once it expires.                                                                                                                                                                                                       |
| `--scope`                    |         | <p>[Optional]</p><p>The scope of access that the token provides. This is only available for administrators.</p>                                                                                                                                                                                                                                                   |

### Examples

#### Example 1

Create an access token for the user in the default server configured by the [jf c add](configuration.md#adding-and-editing-configured-servers) command:

```
jf atc
```

#### Example 2

Create an access token for the user with the **toad** username:

```
jf atc toad
```

## Adding and Editing Configured Servers

The `config add` and `config edit` commands are used to add and edit JFrog Platform server configuration, stored in JFrog CLI's configuration storage. These configured servers can be used by other commands. The configured servers' details can be overridden per command by passing in alternative values for the URL and login credentials. The values configured are saved in a file under the JFrog CLI home directory.

| Command                  | Default                                                       | Description                                                                                                                                                                                                                                                                                                                                                            |
| ------------------------ | ------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Command Name**         |                                                               | `config add`, `c add` / `config edit`, `c edit`                                                                                                                                                                                                                                                                                                                        |
| **Command Arguments**    |                                                               | The command accepts no arguments                                                                                                                                                                                                                                                                                                                                       |
| **Command Options**      |                                                               |                                                                                                                                                                                                                                                                                                                                                                        |
| `--access-token`         |                                                               | <p>[Optional]</p><p>Access token.</p>                                                                                                                                                                                                                                                                                                                                  |
| `--artifactory-url`      |                                                               | <p>[Optional]</p><p>JFrog Artifactory URL. (example: https://acme.jfrog.io/artifactory)</p>                                                                                                                                                                                                                                                                            |
| `--basic-auth-only`      | `false`                                                       | Used for Artifactory authentication. Set to `true` to disable replacing username and password/API key with automatically created access token that's refreshed hourly. Username and password/API key will still be used with commands which use external tools or the JFrog Distribution service. Can only be passed along with username and password/API key options. |
| `--client-cert-key-path` |                                                               | <p>[Optional]</p><p>Private key file for the client certificate in PEM format.</p>                                                                                                                                                                                                                                                                                     |
| `--client-cert-path`     |                                                               | <p>[Optional]</p><p>Client certificate file in PEM format.</p>                                                                                                                                                                                                                                                                                                         |
| `--dist-url`             |                                                               | <p>[Optional]</p><p>Distribution URL. (example: https://acme.jfrog.io/distribution)</p>                                                                                                                                                                                                                                                                                |
| `--enc-password`         | `true`                                                        | If `true`, the configured password will be encrypted using Artifactory's [encryption API](https://www.jfrog.com/confluence/display/RTF/Artifactory+REST+API#ArtifactoryRESTAPI-GetUserEncryptedPassword) before being stored. If `false`, the configured password will not be encrypted.                                                                               |
| `--insecure-tls`         | `false`                                                       | Set to true to skip TLS certificates verification, while encrypting the Artifactory password during the config process.                                                                                                                                                                                                                                                |
| `--interactive`          | <p>true<br>(unless <code>$CI</code> is <code>true</code>)</p> | Set to false if you do not want the config command to be interactive.                                                                                                                                                                                                                                                                                                  |
| `--mission-control-url`  |                                                               | <p>[Optional]</p><p>JFrog Mission Control URL. (example: https://acme.jfrog.io/ms)</p>                                                                                                                                                                                                                                                                                 |
| `--password`             |                                                               | <p>[Optional]</p><p>JFrog Platform password.</p>                                                                                                                                                                                                                                                                                                                       |
| `--ssh-key-path`         |                                                               | <p>[Optional]</p><p>For authentication with Artifactory. SSH key file path.</p>                                                                                                                                                                                                                                                                                        |
| `--url`                  |                                                               | <p>[Optional]</p><p>JFrog Platform URL. (example: https://acme.jfrog.io)</p>                                                                                                                                                                                                                                                                                           |
| `--user`                 |                                                               | <p>[Optional]</p><p>JFrog Platform username.</p>                                                                                                                                                                                                                                                                                                                       |
| `--xray-url`             |                                                               | \[Optional] Xray URL. (example: https://acme.jfrog.io/xray)                                                                                                                                                                                                                                                                                                            |
| `--overwrite`            | `false`                                                       | <p>[Available for <code>config add</code> only]<br>Overwrites the instance configuration if an instance with the same ID already exists.</p>                                                                                                                                                                                                                           |
| **Command Arguments**    |                                                               |                                                                                                                                                                                                                                                                                                                                                                        |
| server ID                |                                                               | A unique ID for the server configuration.                                                                                                                                                                                                                                                                                                                              |

## Removing Configured Servers

The `config remove` command is used to remove the JFrog Platform server configuration, stored in JFrog CLI's configuration storage.

| Command               | Default | Description                                                                          |
| --------------------- | ------- | ------------------------------------------------------------------------------------ |
| **Command Name**      |         | `config remove`, `c rm`                                                              |
| **Command Arguments** |         |                                                                                      |
| \<server ID>          |         | The server ID to remove. If no argument is sent, all configured servers are removed. |
| **Command Options**   |         |                                                                                      |
| `--quiet`             | `$CI`   | Set to `true` to skip the delete confirmation message.                               |

## Showing the Configured Servers

The `config show` command shows the stored configuration. You may show a specific server's configuration by sending its ID as an argument to the command.

| Command               | Description                                                                             |
| --------------------- | --------------------------------------------------------------------------------------- |
| Command name          | `config show`, `c s`                                                                    |
| **Command Arguments** |                                                                                         |
| \<server ID>          | The ID of the server to show. If no argument is sent, all configured servers are shown. |

## Setting a Server as Default

The `config use` command sets a configured server as default. The following commands will use this server.

|                       |                                         |
| --------------------- | --------------------------------------- |
| **Command Name**      | `config use`                            |
| **Command Arguments** |                                         |
| \<server ID>          | The ID of the server to set as default. |

## Exporting and Importing Configuration

The `config export` command generates a token, which stores the server configuration. This token can be used by the `config import` command, to import the configuration stored in the token, and save it in JFrog CLI's configuration storage.

### Export

|                       |                                |
| --------------------- | ------------------------------ |
| **Command Name**      | `config export`, `c ex`        |
| **Command Arguments** |                                |
| \<server ID>          | The ID of the server to export |

### Import

|                       |                         |
| --------------------- | ----------------------- |
| **Command Name**      | `config import`, `c im` |
| **Command Arguments** |                         |
| \<server token>       | The token to import     |

## Sensitive Data Encryption

### File-Based Encryption

Starting from version 1.37.0, JFrog CLI introduces support for encrypting sensitive data stored in its configuration using an encryption key stored in a file. Follow these steps to enable encryption:

1. Generate a random 32-character master key. Ensure that the key size is exactly 32 characters. For example: `f84hc22dQfhe9f8ydFwfsdn48!wejh8A`
2.  Create a file named `security.yaml` under `~/.jfrog/security`.

    > If you've customized the default JFrog CLI home directory by setting the `JFROG_CLI_HOME_DIR` environment variable, create the `security/security.yaml` file under the configured home directory.
3.  Add the generated master key to the `security.yaml` file:

    ```yaml
    version: 1
    masterKey: "your master key"
    ```
4. Ensure that the `security.yaml` file has only read permissions for the user running JFrog CLI.

The configuration will be encrypted the next time JFrog CLI accesses the config. If you have existing configurations stored before creating the file, you'll need to reconfigure the servers stored in the config.

> **Warning:** When upgrading JFrog CLI from a version prior to 1.37.0 to version 1.37.0 or above, automatic changes are made to the content of the `~/.jfrog` directory to support the new functionality introduced. Before making these changes, the content of the `~/.jfrog` directory is backed up inside the `~/.jfrog/backup` directory. After enabling sensitive data encryption, it is recommended to remove the `backup` directory to ensure no sensitive data is left unencrypted.

### Environment Variable-Based Encryption

Starting from version 2.36.0, JFrog CLI also supports encrypting sensitive data in its configuration using an encryption key stored in an environment variable.

## Enable Encryption

1. Generate a random 32-character master key.&#x20;

&#x20;      For example: `f84hc22dQfhe9f8ydFwfsdn48!wejh8A`

2. Store the key in an environment variable named `JFROG_CLI_ENCRYPTION_KEY`.

The configuration will be encrypted the next time JFrog CLI attempts to access the config. If you have configurations already stored before setting the environment variable, you'll need to reconfigure the servers stored in the config.
