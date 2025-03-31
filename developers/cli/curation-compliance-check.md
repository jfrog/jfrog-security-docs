# Curation Compliance Check

JFrog Curation defends your software supply chain by enabling early detection and blocking of malicious or risky open-source packages before they enter your environment. It helps identify harmful, vulnerable, or non-compliant packages seamlessly, enhancing security, compliance, and developer productivity.

The `curation-audit` command checks the project to identify third-party dependencies that violate Curation service restrictions. It provides detailed insights into policy violations and may suggest compliant package alternatives.

Learn more about Curation Supported technologies [here](../../products/curation/supported-technologies.md).

**Command**: `curation-audit`, `ca`

## Configuration

* **Pass-Through Curation:** Required for package types except npm. Configure on remote repositories in Artifactory.
*   **Connect JFrog CLI to Platform:**

    ```
    jf c add
    ```

    Use an access token from Artifactory when prompted. Verify the connection:

    ```
    jf c show
    ```
* **Project Configuration:**
  * **NPM:** `jf npmc` inside the project directory.
  * **Maven:** `jf mvnc` inside the project directory.
  * **Pip:** `jf pipc` inside the project directory.
  * **Go:** `jf goc` inside the project directory.

### Commands Parameters

| Parameter             | Optional/Required | Description                                                                 |
| --------------------- | ----------------- | --------------------------------------------------------------------------- |
| `--format`            | Optional          | Defines the output format. Acceptable values: `table` (default) and `json`. |
| `--working-dirs`      | Optional          | A comma-separated list of directories to audit.                             |
| `--threads`           | Optional          | Number of parallel threads for checking package status. Default: `3`.       |
| `--requirements-file` | Optional          | \[Pip] Specifies the requirements file (e.g., `requirements.txt`).          |

## Examples

Audit the current directory:

```
jf curation-audit
```

Audit specific directories:

```
jf curation-audit --working-dirs="/path/to/project/npm_project1,/path/to/project/npm_project2"
```

Audit with multiple threads:

```
jf curation-audit --threads=5
```

Exclude specific packages or versions from policy restrictions using waivers:

1. Execute the `jf-curation-audit` command:

```
jf curation-audit
Found 4 blocked packages for project sample-node-project:1.0.0
Curation
┌────┬──────────────┬────────────┬──────────────┬─────────┬─────────┬──────────────┬──────────────┬──────────────┬──────────────┐
│ ID │ DIRECT       │ DIRECT     │ BLOCKED      │ BLOCKED │ PACKAGE │ VIOLATED     │ VIOLATED CON │ EXPLANATION  │ RECOMMENDATI │
│    │ DEPENDENCY   │ DEPENDENCY │ PACKAGE      │ PACKAGE │ TYPE    │ POLICY       │ DITION       │              │ ON           │
│    │ PACKAGE      │ PACKAGE    │ NAME         │ VERSION │         │ NAME         │ NAME         │              │              │
│    │ NAME         │ VERSION    │              │         │         │              │              │              │              │
├────┼──────────────┼────────────┼──────────────┼─────────┼─────────┼──────────────┼──────────────┼──────────────┼──────────────┤
│ 1  │ ansi-regex   │ 3.0.0      │ ansi-regex   │ 3.0.0   │ npm     │ High CVE     │ CVE with CVS │ Package vers │ Upgrade to t │
│    │              │            │              │         │         │              │ S score betw │ ion contains │ he following │
│    │              │            │              │         │         │              │ een 7.0 and  │ the followin │ version(s):  │
│    │              │            │              │         │         │              │ 8.9 (with or │ g vulnerabil │ CVE-2021-380 │
│    │              │            │              │         │         │              │ without a fi │ ity(s):      │ 7: 6.0.1; 5. │
│    │              │            │              │         │         │              │ x version av │ CVE-2021-380 │ 0.1; 4.1.1;  │
│    │              │            │              │         │         │              │ ailable)     │ 7: 7.5       │ 3.0.1        │
└────┴──────────────┴────────────┴──────────────┴─────────┴─────────┴──────────────┴──────────────┴──────────────┴──────────────┘
```

2. Enter `y` as an answer to whether or not you want a waiver:

```
Do you want to request a waiver for any of the listed packages? (y/n) [n]? y
```

3. Enter table row numbers representing packages you want to exclude from policy restrictions:

```
Please enter the row number(s) for which you want to request a waiver (comma-separated for multiple, range, or “all”) [all]: all
```

4. Enter the reason for requesting a waiver:

```
Please enter the reason for the waiver request: Required packages
```
