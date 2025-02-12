# Scan Published Builds

JFrog CLI is integrated with JFrog Xray and JFrog Artifactory, allowing you to have your build artifacts and dependencies scanned for vulnerabilities and license violations. Please notice that the build in the below example had already been published to Artifactory using the [build-publish command](https://docs.jfrog-applications.jfrog.io/jfrog-applications/jfrog-cli/binaries-management-with-jfrog-artifactory#publishing-build-info).

**Command**: `build-scan`, `bs`

### Commands Parameters

| Parameter     | Optional/Default | Description                                                                                                                                                                                                   |
| ------------- | ---------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `--server-id` | Optional         | Server ID configured by the _`jf c add`_ command. If not specified, the default configured server is used.                                                                                                    |
| `--vuln`      | Optional         | Set if you'd like to receive all vulnerabilities, regardless of the policy configured in Xray.                                                                                                                |
| `--fail`      | Default: `true`  | When using one of the flags `--watches`, `--project`, or `--repo-path` and a Fail build rule is matched the command will return exit code 3. Set to `false` if you'd like to see violations with exit code 0. |
| `--format`    | Default: `table` | Defines the output format of the command. The accepted values: `table` and `json`.                                                                                                                            |
| `--project`   | Optional         | JFrog project key                                                                                                                                                                                             |
| `--rescan`    | Default: `false` | Set to `true` when scanning an already successfully scanned build, for example after adding an ignore rule.                                                                                                   |

### **Arguments**

| Build name   | Build name to be scanned.   |
| ------------ | --------------------------- |
| Build number | Build number to be scanned. |

## Examples

Scan build number 18, corresponding to the following build name: 'my-build-name'.

```
jf bs my-build-name 18
```
