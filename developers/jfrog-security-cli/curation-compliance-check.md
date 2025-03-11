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

| `--format`            | Optional | Defines the output format. Acceptable values: `table` (default) and `json`. |
| --------------------- | -------- | --------------------------------------------------------------------------- |
| `--working-dirs`      | Optional | A comma-separated list of directories to audit.                             |
| `--threads`           | Optional | Number of parallel threads for checking package status. Default: `3`.       |
| `--requirements-file` | Optional | \[Pip] Specifies the requirements file (e.g., `requirements.txt`).          |

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
