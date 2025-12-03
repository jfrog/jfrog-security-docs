# Scan Published Builds

JFrog CLI is integrated with JFrog Xray and JFrog Artifactory, allowing you to have your build artifacts and dependencies scanned for vulnerabilities and license violations.

**Command**: `build-scan`, `bs`

The `build-scan` command scans published builds for security vulnerabilities and license compliance issues.\
**Note:** For the `build-scan` command to return meaningful results, the scanned build must be included in the scope of a Watch that is associated with a Policy containing a **Fail Build** action. This requirement applies to all command parameters **except for `--vuln`**, which can return vulnerability data independently of policy evaluation.

### Commands Parameters

| Parameter        | Optional/Default | Description                                                                                                               |
| ---------------- | ---------------- | ------------------------------------------------------------------------------------------------------------------------- |
| `--server-id`    | Optional         | Server ID configured by the `jf c add` command. If not specified, the default configured server is used.                  |
| `--vuln`         | Optional         | Set if you'd like to receive all vulnerabilities, regardless of the policy configured in Xray.                            |
| `--insecure-tls` | Default: false   | Set to true to skip TLS certificates verification.                                                                        |
| `--fail`         | Default: true    | If fail build violations are found, it will return exit code of `3`. Set to `false` to see violations with exit code `0`. |
| `--format`       | Default: table   | Defines the output format of the command. Accepted values: `table`, `cyclonedx`, and `json`.                              |
| `--project`      | Optional         | JFrog project key.                                                                                                        |
| `--rescan`       | Default: false   | Set to true when scanning an already successfully scanned build, e.g., after adding an ignore rule.                       |

### **Arguments**

| `Build Name`   | Build name to be scanned.   |
| -------------- | --------------------------- |
| `Build Number` | Build number to be scanned. |

## Examples

**Scan a specific build:**\
Scans build number `18`, corresponding to the build name `my-build-name`.

```
jf bs my-build-name 18
```

**Scan with project policies:**\
Scans build `18` of `my-build-name` using policies defined for `project-1`.

```
jf bs my-build-name 18 --project project-1
```

**Scan showing all vulnerabilities:**\
Displays all vulnerabilities for build `18`.

```
jf bs my-build-name 18 --vuln
```

**Scan with license information:**\
Scans and displays license compliance details.

```
jf bs my-build-name 18 --licenses
```
