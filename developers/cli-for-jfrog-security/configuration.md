# Configuration

You can use the `jf login` command to authenticate with the JFrog Platform through a web browser. This command is solely interactive, meaning it does not accept options and cannot be used in a CI server.

This command allows creating Access Tokens for users in the JFrog Platform. By default, a user-scoped token will be created. Administrators may provide the scope explicitly with `--scope` or implicitly with `--groups`, `--grant-admin`.

### Access Token Creation

#### Command Name: `access-token-create`, `atc`

|                       |                                                                                                                 |
| --------------------- | --------------------------------------------------------------------------------------------------------------- |
| **Command Arguments** | **Description**                                                                                                 |
| `username`            | The username for which this token is created. If not specified, the token will be created for the current user. |

**Command Options:**

| Option          | Default                   | Description                                                                                                                                                                                                             |
| --------------- | ------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `--audience`    | N/A                       | A space-separated list of other instances or services that should accept this token identified by their Service-IDs.                                                                                                    |
| `--description` | N/A                       | Free text token description (up to 1024 characters). Useful for filtering and managing tokens.                                                                                                                          |
| `--expiry`      | Platform default (1 year) | The amount of time, in seconds, before the token expires. Must be non-negative. To specify a token that never expires, set to `0`. Non-admins may only set a value that is equal to or lower than the platform default. |
| `--grant-admin` | `false`                   | Grants admin privileges to the access token. Only available for administrators.                                                                                                                                         |
| `--groups`      | N/A                       | A list of comma-separated groups associated with the access token. Only available for administrators.                                                                                                                   |
| `--project`     | N/A                       | The project for which this token is created. Enter the project name.                                                                                                                                                    |
| `--reference`   | `false`                   | Generates a Reference Token (alias to Access Token) in addition to the full token. Available from Artifactory 7.38.10.                                                                                                  |
| `--refreshable` | `false`                   | If `true`, a refresh token will also be returned to generate a new token once it expires.                                                                                                                               |
| `--scope`       | N/A                       | The scope of access that the token provides. Only available for administrators.                                                                                                                                         |

#### Example Usage:

```shell
jf atc
jf atc toad
```

***

## Adding and Editing Configured Servers

#### Command Name: `config add` / `config edit`, `c add` / `c edit`

**Command Options:**

| Option                   | Default                        | Description                                                                                                                                                          |
| ------------------------ | ------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `--access-token`         | N/A                            | Access token.                                                                                                                                                        |
| `--artifactory-url`      | N/A                            | JFrog Artifactory URL (e.g., `https://acme.jfrog.io/artifactory`).                                                                                                   |
| `--basic-auth-only`      | `false`                        | Used for Artifactory authentication. If `true`, disables replacing username and password/API key with an automatically created access token that's refreshed hourly. |
| `--client-cert-key-path` | N/A                            | Private key file for the client certificate in PEM format.                                                                                                           |
| `--client-cert-path`     | N/A                            | Client certificate file in PEM format.                                                                                                                               |
| `--dist-url`             | N/A                            | Distribution URL (e.g., `https://acme.jfrog.io/distribution`).                                                                                                       |
| `--enc-password`         | `true`                         | If `true`, encrypts the configured password using Artifactory's encryption API before storage.                                                                       |
| `--insecure-tls`         | `false`                        | If `true`, skips TLS certificate verification while encrypting the Artifactory password.                                                                             |
| `--interactive`          | `true`, unless `$CI` is `true` | If `false`, the config command will not be interactive.                                                                                                              |
| `--mission-control-url`  | N/A                            | JFrog Mission Control URL (e.g., `https://acme.jfrog.io/ms`).                                                                                                        |
| `--password`             | N/A                            | JFrog Platform password.                                                                                                                                             |
| `--ssh-key-path`         | N/A                            | SSH key file path for authentication with Artifactory.                                                                                                               |
| `--url`                  | N/A                            | JFrog Platform URL (e.g., `https://acme.jfrog.io`).                                                                                                                  |
| `--user`                 | N/A                            | JFrog Platform username.                                                                                                                                             |
| `--xray-url`             | N/A                            | Xray URL (e.g., `https://acme.jfrog.io/xray`).                                                                                                                       |
| `--overwrite`            | `false`                        | Overwrites the instance configuration if an instance with the same ID already exists.                                                                                |

#### Example Usage:

```shell
jf c add
jf c edit
```

***

## Proxy Support

JFrog CLI supports using an HTTP/S proxy. Set `HTTP_PROXY` or `HTTPS_PROXY` environment variables with the proxy URL.

**Environment Variables:**

| Variable Name | Description                                                                                                                             |
| ------------- | --------------------------------------------------------------------------------------------------------------------------------------- |
| `HTTP_PROXY`  | Determines a URL to an HTTP proxy.                                                                                                      |
| `HTTPS_PROXY` | Determines a URL to an HTTPS proxy.                                                                                                     |
| `NO_PROXY`    | Bypasses the proxy for specified IPs, subnets, or domains. Uses a comma-separated list of hostnames or IPs without protocols and ports. |

***
