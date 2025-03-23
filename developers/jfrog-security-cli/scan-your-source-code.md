# Scan Your Source Code

The `jf audit` command enables developers to perform **on-demand security scans** of their source code **directly from their terminal**, ensuring early detection of CVEs, licenses, operational risk, [SAST](../../products/advanced-security/features-and-capabilities/sast/), [misconfigurations](../../products/advanced-security/features-and-capabilities/misconfigurations-scans.md), and exposed [secrets](../../products/advanced-security/features-and-capabilities/secrets-scans.md). By integrating seamlessly into the developer workflow, it helps catch security risks before code reaches production—reducing remediation costs and enhancing software integrity. The scan results are displayed in the terminal for immediate feedback and are also available in the **JFrog Platform’s On-Demand Scans pane**, providing centralized visibility.

**Note**:&#x20;

* For SCA, the command automatically detects the package manager used by your project and uses it to construct the dependency graph.
* If the project hasn’t been installed yet, the system will execute an install command to generate the dependency tree for scanning.
* On-demand scan results are retained for seven days before being automatically deleted.

## **Command Options**

Command: `jf audit` (alias: `jf aud`)

| `--help`                        | No | —                                    | Displays information about the `jf audit` command options.                                                                                                                                                |
| ------------------------------- | -- | ------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `--server-id`                   | No | Default server                       | JFrog server ID configured via `jf c add`.                                                                                                                                                                |
| `--project`                     | No | —                                    | JFrog project key to identify security violations. Incompatible with `--repo-path` and `--watches`.                                                                                                       |
| `--repo-path`                   | No | —                                    | Artifactory repository path for identifying violations. Incompatible with `--project` and `--watches`.                                                                                                    |
| `--watches`                     | No | —                                    | Comma-separated list of Xray watches to determine violations. Incompatible with `--project` and `--repo-path`.                                                                                            |
| `--licenses`                    | No | `false`                              | Displays the list of licenses.                                                                                                                                                                            |
| `--format`                      | No | `table`                              | Output format: `table` or `json`.                                                                                                                                                                         |
| `--extended-table`              | No | `false`                              | When set to `true`, result table includes extended fields such as `CVSS` and `Xray Issue Id`. Must be executed with `--format table`.                                                                     |
| `--fail`                        | No | `true`                               | Returns exit code `3` if a Fail Build rule is matched. Set to `false` to return exit code `0` with violations.                                                                                            |
| `--use-wrapper`                 | No | `false` (Gradle/Maven only)          | Use Gradle or Maven wrapper.                                                                                                                                                                              |
| `--dep-type`                    | No | `all` (npm only)                     | Defines npm dependency types: `all`, `devOnly`, `prodOnly`.                                                                                                                                               |
| `--exclude-test-deps`           | No | `false` (Gradle only)                | Excludes Gradle test dependencies from Xray scanning.                                                                                                                                                     |
| `--requirements-file`           | No | — (Pip only)                         | Specifies the pip requirements file (e.g., `requirements.txt`).                                                                                                                                           |
| `--working-dirs`                | No | Root directory                       | Comma-separated list of directories to audit. Defaults to recursive scan from the project root.                                                                                                           |
| `--exclusions`                  | No | `.git;node_modules;target;venv;test` | Semicolon-separated list to exclude specific directories or files. Supports wildcards (`*`, `?`).                                                                                                         |
| `--fixable-only`                | No | —                                    | Displays only issues with available fixes.                                                                                                                                                                |
| `--min-severity`                | No | —                                    | Minimum severity of issues to display: `Low`, `Medium`, `High`, `Critical`.                                                                                                                               |
| `--threads`                     | No | `3`                                  | Number of parallel threads for scanning.                                                                                                                                                                  |
| `--go`                          | No | `false`                              | Audits a Go project.                                                                                                                                                                                      |
| `--gradle`                      | No | `false`                              | Audits a Gradle project.                                                                                                                                                                                  |
| `--mvn`                         | No | `false`                              | Audits a Maven project.                                                                                                                                                                                   |
| `--npm`                         | No | `false`                              | Audits an npm project.                                                                                                                                                                                    |
| `--pnpm`                        | No | `false`                              | Audits a pnpm project.                                                                                                                                                                                    |
| `--nuget`                       | No | `false`                              | Audits a .NET project.                                                                                                                                                                                    |
| `--pip`                         | No | `false`                              | Audits a Pip project.                                                                                                                                                                                     |
| `--pipenv`                      | No | `false`                              | Audits a Pipenv project.                                                                                                                                                                                  |
| `--yarn`                        | No | `false`                              | Audits a Yarn project.                                                                                                                                                                                    |
| `--sca`                         | No | `false`                              | <p><strong>Selective scanners mode</strong></p><p>Runs the Software Composition Analysis (SCA) scan. Can be combined with <code>--secrets</code>, <code>--sast</code>, and <code>--iac</code>.</p>        |
| `--without-contextual-analysis` | No | `false`                              | <p><strong>Selective scanners mode</strong></p><p>Disables Contextual Analysis when using <code>--sca</code>.</p>                                                                                         |
| `--iac`                         | No | `false`                              | <p><strong>Selective scanners mode</strong></p><p>Executes Infrastructure as Code (IaC) scans. Can be combined with <code>--sca</code>, <code>--secrets</code>, and <code>--sast</code>.</p>              |
| `--secrets`                     | No | `false`                              | <p><strong>Selective scanners mode</strong></p><p>Executes Secrets Detection scans. Can be combined with <code>--sca</code>, <code>--sast</code>, and <code>--iac</code>.</p>                             |
| `--validate-secrets`            | No | `false`                              | <p><strong>Selective scanners mode</strong></p><p>Validates detected secrets. Only applicable when using <code>--secrets</code>.</p>                                                                      |
| `--sast`                        | No | `false`                              | <p><strong>Selective scanners mode</strong></p><p>Executes Static Application Security Testing (SAST) scans. Can be combined with <code>--sca</code>, <code>--secrets</code>, and <code>--iac</code>.</p> |
| `--vuln`                        | No | —                                    | Displays all vulnerabilities, regardless of Xray policies.                                                                                                                                                |

## Working in Air-Gapped Environments

Follow the W[orking in Air-Gapped Environments](../working-in-air-gapped-environments.md) procedure.

The environment variable to set the source code scan is `JFROG_CLI_RELEASES_REPO`.

**Examples**

A basic audit that shows all vulnerabilities, regardless of the policies set in Xray:

```bash
jf audit
```

Audit for Maven & npm projects that shows all vulnerabilities, regardless of the policies set in Xray:

```bash
jf audit --mvn --npm
```

Audit using a defined Watch in Xray:

```bash
jf audit --watches "watch1"
```

Audit using numerous defined Watches in Xray:

```bash
jf audit --watches "watch1,watch2"
```

Audit using defined policies in a specific project:&#x20;

```bash
jf audit --project "project-1"
```

Audit using defined policies in a specific Artifactory path:

```bash
jf audit --repo-path "libs-local/release-artifacts/"
```

Excluding from audit all files inside a directory (`node_modules`) and files with a specific suffix (`to_exclude`):

```bash
jf audit --exclusions "*node_modules*;*to_exclude"
```
