# Scan Your Source Code

The `jf audit` command enables developers to perform **on-demand security scans** of their source code **directly from their terminal**, ensuring early detection of CVEs, licenses, operational risk, [SAST](../../products/advanced-security/features-and-capabilities/sast/), [misconfigurations](../../products/advanced-security/features-and-capabilities/misconfigurations-scans.md), and exposed [secrets](../../products/advanced-security/features-and-capabilities/secrets-scans/). By integrating seamlessly into the developer workflow, it helps catch security risks before code reaches production—reducing remediation costs and enhancing software integrity. The scan results are displayed in the terminal for immediate feedback and are also available in the **JFrog Platform’s On-Demand Scans pane**, providing centralized visibility.

{% hint style="info" %}
For SCA, the command automatically detects the package manager used by your project and uses it to construct the dependency graph.

If the project hasn’t been installed yet, the system will execute an install command to generate the dependency tree for scanning.

On-demand scan results are retained for seven days before being automatically deleted.

By default, the environment variable `ENABLE_CUSTOM_SECRETS_SCANNER` is set to `true`, enabling [custom secrets scanning](../../products/advanced-security/features-and-capabilities/secrets-scans/custom-secrets-scanner.md) automatically as part of the audit.

The grace period setting in the "fail build" policy is not applied during `​jf docker scan`​​ (on-demand Docker image scanning), resulting in the build failing immediately despite the configured grace period.
{% endhint %}

### Command Options

Command: `jf audit` (alias: `jf aud`)

| Option                        | Required | Default                                           | Description                                                                                                                                                                                                                                            |
| ----------------------------- | -------- | ------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| --dep-type                    | No       | all (npm only)                                    | Defines npm dependency types: all, devOnly, prodOnly.                                                                                                                                                                                                  |
| --exclude-test-deps           | No       | false (Gradle only)                               | Excludes Gradle test dependencies from Xray scanning.                                                                                                                                                                                                  |
| --exclusions                  | No       | .git, node\_modules, target, venv, test, and dist | Semicolon-separated list to exclude specific directories or files. Supports wildcards (\*, ?). You may override the default exclusions by explicitly setting your own list using the --exclusions flag.                                                |
| --extended-table              | No       | false                                             | When set to true, result table includes extended fields such as CVSS and Xray Issue Id. Must be executed with --format table.                                                                                                                          |
| --fail                        | No       | true                                              | Returns exit code 3 if a Fail Build rule is matched. Set to false to return exit code 0 with violations.                                                                                                                                               |
| --fixable-only                | No       | —                                                 | Displays only issues with available fixes.                                                                                                                                                                                                             |
| --format                      | No       | table                                             | Defines the output format: table , json, cyclonedx, simple-json, or sarif. The json format does not support the Advanced Security contextual analysis, Secrets, and misconfiguration scans.                                                            |
| --go                          | No       | false                                             | Audits a Go project.                                                                                                                                                                                                                                   |
| --gradle                      | No       | false                                             | Audits a Gradle project.                                                                                                                                                                                                                               |
| --help                        | No       | —                                                 | Displays information about the jf audit command options.                                                                                                                                                                                               |
| --iac                         | No       | false                                             | **Selective scanners mode** Executes Infrastructure as Code (IaC) scans. Can be combined with --sca, --secrets, and --sast.                                                                                                                            |
| --insecure-tls                | No       | false                                             | Set to true to skip TLS certificates verification.                                                                                                                                                                                                     |
| --licenses                    | No       | false                                             | Displays the list of licenses.                                                                                                                                                                                                                         |
| --min-severity                | No       | —                                                 | Minimum severity of issues to display: Low, Medium, High, Critical.                                                                                                                                                                                    |
| --mvn                         | No       | false                                             | Audits a Maven project.Note: The command requires a virtual repository that contains both your release and snapshot repositories.If this solution does not resolve the issue in your environment, please contact JFrog Support for further assistance. |
| --npm                         | No       | false                                             | Audits an npm project.                                                                                                                                                                                                                                 |
| --nuget                       | No       | false                                             | Audits a .NET project.                                                                                                                                                                                                                                 |
| --pac                         | No       | —                                                 |                                                                                                                                                                                                                                                        |
| --pip                         | No       | false                                             | Audits a Pip project.                                                                                                                                                                                                                                  |
| --pipenv                      | No       | false                                             | Audits a Pipenv project.                                                                                                                                                                                                                               |
| --pnpm                        | No       | false                                             | Audits a pnpm project.                                                                                                                                                                                                                                 |
| --project                     | No       | —                                                 | JFrog project key to identify security violations. Incompatible with --repo-path and --watches.                                                                                                                                                        |
| --repo-path                   | No       | —                                                 | Artifactory repository path for identifying violations. Incompatible with --project and --watches.                                                                                                                                                     |
| --requirements-file           | No       | — (Pip only)                                      | Specifies the pip requirements file (e.g., requirements.txt).                                                                                                                                                                                          |
| --sbom                        | No       | false                                             | Displays the Software Bill of Materials (SBOM) for the project when set to true. Only applicable if the --sca flag is also used and the output format is set to table. Supported formats: table and cyclonedx.                                         |
| --sca                         | No       | false                                             | **Selective scanners mode** Runs the Software Composition Analysis (SCA) scan. Can be combined with --secrets, --sast, and --iac.                                                                                                                      |
| --sast                        | No       | false                                             | **Selective scanners mode** Executes Static Application Security Testing (SAST) scans. Can be combined with --sca, --secrets, and --iac.                                                                                                               |
| --secrets                     | No       | false                                             | **Selective scanners mode** Executes Secrets Detection scans. Can be combined with --sca, --sast, and --iac.                                                                                                                                           |
| --server-id                   | No       | Default server                                    | JFrog server ID configured via jf c add.                                                                                                                                                                                                               |
| --threads                     | No       | 3                                                 | Number of parallel threads for scanning.                                                                                                                                                                                                               |
| --use-wrapper                 | No       | false (Gradle/Maven only)                         | Use Gradle or Maven wrapper.                                                                                                                                                                                                                           |
| --validate-secrets            | No       | false                                             | **Selective scanners mode** Validates detected secrets. Only applicable when using --secrets.                                                                                                                                                          |
| --vuln                        | No       | —                                                 | Displays all vulnerabilities, regardless of Xray policies.                                                                                                                                                                                             |
| --watches                     | No       | —                                                 | Comma-separated list of Xray watches to determine violations. Supported violations are CVEs, operational risk, and Licenses. Incompatible with --project and --repo-path.                                                                              |
| --without-contextual-analysis | No       | false                                             | **Selective scanners mode** Disables Contextual Analysis when using --sca.                                                                                                                                                                             |
| --working-dirs                | No       | Root directory                                    | Comma-separated list of directories to audit. Defaults to recursive scan from the project root.                                                                                                                                                        |
| --yarn                        | No       | false                                             | Audits a Yarn project.                                                                                                                                                                                                                                 |

### Working in Air-Gapped Environments?

Follow the [Working in Air-Gapped Environments](../../shift-left-on-security/working-in-air-gapped-environments.md) procedure.

#### Examples

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
