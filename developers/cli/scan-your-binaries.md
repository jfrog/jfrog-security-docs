# Scan Your Binaries

The `jf scan` and `jf docker scan` command enables developers to perform **on-demand security scans** of their binaries **directly from their terminal**, ensuring early detection of CVEs, licenses, operational risk, and exposed secrets. By integrating seamlessly into the developer workflow, it helps catch security risks of binaries before uploading them into JFrog Artifactory — reducing remediation costs and enhancing software integrity. The scan results are displayed in the terminal for immediate feedback and are also available in the **JFrog Platform’s On-Demand Scans pane**, providing centralized visibility.

However, it's important to note that on-demand scanning is not a best practice for overall binary security; it is typically used for specific cases where immediate feedback is needed. For comprehensive security, organizations should implement continuous scanning as part of their CI/CD pipeline, ensuring ongoing monitoring and threat detection throughout the software development lifecycle.

{% hint style="info" %}
On-demand scan results are retained for seven days before being automatically deleted.
{% endhint %}

## Scanning Files on the Local File System

Use the `jf scan` command to scan files on your local file system with JFrog Xray.

**Command**: `scan`, `s`

### Commands Parameters

| Parameter       | Optional/Default | Description                                                                                                                                                                |
| --------------- | ---------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `--server-id`   | Optional         | Server ID configured using `jf c add`. Defaults to the configured server if not specified.                                                                                 |
| `--spec`        | Optional         | Path to a file specifying files to scan. Cannot be used with the `pattern` argument.                                                                                       |
| `--project`     | Optional         | JFrog project key for security violations. Mutually exclusive with `--repo-path` and `--watches`.                                                                          |
| `--repo-path`   | Optional         | Artifactory repository path for determining violations. Mutually exclusive with `--project` and `--watches`.                                                               |
| `--watches`     | Optional         | Comma-separated list of Xray watches. Supported violations are CVEs and Licenses.  Mutually exclusive with `--project` and `--repo-path`.                                  |
| `--licenses`    | Default: `false` | Display license information.                                                                                                                                               |
| `--format=json` | Optional         | Outputs scan results in `json`, `table`, `simple-json`, and `sarif` format.                                                                                                |
| `--sbom`        | Default: `false` | Displays the Software Bill of Materials (SBOM) for the project when set to true. Only applicable if the `--sca` flag is also used and the output format is set to `table`. |
| `--vuln`        | Optional         | Display all vulnerabilities, regardless of Xray policy settings.                                                                                                           |

### **Arguments**

| Argument  | Description                                                      |
| --------- | ---------------------------------------------------------------- |
| `Pattern` | Specifies the file system path to artifacts. Supports wildcards. |

### Examples

**Scan with a specific watch:** Scans all files at `path/to/files/` using the `watch1` defined in Xray.

```
jf s "path/to/files/" --watches "watch1"
```

**Scan with multiple watches:** Scans files using `watch1` and `watch2` defined in Xray.

```
jf s "path/to/files/" --watches "watch1,watch2"
```

**Scan specific file types:** Scans `.zip` files using `watch1` and `watch2`.

```
jf s "path/to/files/*.zip" --watches "watch1,watch2"
```

**Scan with project policies:** Scans `.tgz` files using policies defined for `project-1`.

```
jf s "path/to/files/*.tgz" --project "project-1"
```

**Scan with repository path:** Scans `.tgz` files using policies for `libs-local/release-artifacts/`.

```
jf s "*.tgz" --repo-path "libs-local/release-artifacts/"
```

**Scan without specific policies:** Shows all known vulnerabilities for `.tgz` files.

```
jf s "*.tgz"
```

## Scanning Docker Containers on the Local File System

Use `jf docker scan` to scan Docker containers locally using the Docker client and JFrog Xray.

### Commands Parameters

| Parameter            | Optional/Default | Description                                             |
| -------------------- | ---------------- | ------------------------------------------------------- |
| `--server-id`        | Optional         | Configured server ID.                                   |
| `--project`          | Optional         | JFrog project key for security violations.              |
| `--repo-path`        | Optional         | Artifactory repository path for determining violations. |
| `--watches`          | Optional         | Comma-separated list of Xray watches.                   |
| `--licenses`         | Default: `false` | Display license information.                            |
| `--validate-secrets` | Default: `false` | Validate detected secrets.                              |
| `--format=<format>`  | Optional         | Outputs scan results in `json` format.                  |
| `--vuln`             | Optional         | Show all vulnerabilities.                               |

### **Arguments**

| Argument  | Description                                                      |
| --------- | ---------------------------------------------------------------- |
| `Pattern` | Specifies the file system path to artifacts. Supports wildcards. |

### **Examples**

**Scan all vulnerabilities:** Scans `img1:1.0.0` and displays all known vulnerabilities.

```
jf docker scan reg1/repo1/img1:1.0.0
```

**Scan with project policies:** Displays violations for `my-project`.

```
jf docker scan reg1/repo1/img1:1.0.0 --project my-project
```

**Scan with Xray watch:** Shows violations based on `my-watch`.

```
jf docker scan reg1/repo1/img1:1.0.0 --watches my-watch
```

**Scan with repository path:** Displays violations for `releases-local/app1/`.

```
jf docker scan reg1/repo1/img1:1.0.0 --repo-path releases-local/app1/
```

## Scanning Image Tarballs on the Local File System

Use the `scan` command to scan tarballs of Docker and OCI images saved on the local file system.

It requires saving the image as a tar file using a compliant tool and then scanning it with the `jf s` command.&#x20;

### Examples

#### **Using Docker**

**Save and scan an image:**

```
docker save --output my-image-docker.tar my-image:1.0.0
jf s my-image-docker.tar
```

#### **Using Skopeo**

**Scan Docker format:**

```
skopeo copy docker-daemon:my-image:1.0.0 docker-archive:my-image-docker.tar
jf s my-image-docker.tar
```

**Scan OCI format:**

```
skopeo copy docker-daemon:my-image:1.0.0 oci-archive:my-image-oci.tar
jf s my-image-oci.tar
```

#### **Using Podman**

**Scan Docker format:**

```
podman save --format=docker-archive -o my-image-docker.tar my-image:1.0.0
jf s my-image-docker.tar
```

**Scan OCI format:**

```
podman save --format=oci -o my-image-oci.tar my-image:1.0.0
jf s my-image-oci.tar
```

#### **Using Kaniko**

**Build and scan an image:**

```
docker run -it --rm -v $(pwd):/workspace gcr.io/kaniko-project/executor:v1.8.1-debug -f Dockerfile --no-push --tarPath my-image.tar -d my-image:1.0 -c . --cleanup
jf s my-image.tar
```
