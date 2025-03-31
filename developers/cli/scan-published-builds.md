# Scan Published Builds

JFrog CLI is integrated with JFrog Xray and JFrog Artifactory, allowing you to have your build artifacts and dependencies scanned for vulnerabilities and license violations.

**Command**: `build-scan`, `bs`

The `build-scan` command scans published builds for security vulnerabilities and license compliance issues.

### Commands Parameters

| Parameter     | Optional/Default | Description                                                                                                                                                   |
| ------------- | ---------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `--server-id` | Optional         | Server ID configured by the `jf c add` command. If not specified, the default configured server is used.                                                      |
| `--vuln`      | Optional         | Set if you'd like to receive all vulnerabilities, regardless of the policy configured in Xray.                                                                |
| `--fail`      | Default: true    | When using `--watches`, `--project`, or `--repo-path` and a Fail build rule is matched, returns exit code 3. Set to false to see violations with exit code 0. |
| `--format`    | Default: table   | Defines the output format of the command. Accepted values: `table` and `json`.                                                                                |
| `--project`   | Optional         | JFrog project key.                                                                                                                                            |
| `--rescan`    | Default: false   | Set to true when scanning an already successfully scanned build, e.g., after adding an ignore rule.                                                           |

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

**Scan with repository path:**\
Scans build `18` of `my-build-name` using policies from `libs-release-local/`.

```
jf bs my-build-name 18 --repo-path libs-release-local/
```

**Scan with Xray watches:**\
Scans build `18` using defined Xray watches `watch1` and `watch2`.

```
jf bs my-build-name 18 --watches watch1,watch2
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
