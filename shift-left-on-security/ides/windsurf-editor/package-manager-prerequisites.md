# Package Manager Prerequisites

### Go Projects

**Prerequisite:** Ensure that the Go CLI is installed and accessible in your system `PATH`.

The JFrog Windsurf Editor Extension scans all project dependencies, both direct and transitive, even if they are not explicitly declared in `go.mod`. To construct the Go dependencies tree, it runs `go mod graph` and intersects the results with `go list -f '{{with .Module}}{{.Path}} {{.Version}}{{end}}' all`.

### Maven Projects

The extension builds the Maven dependencies tree by executing `mvn dependency:tree`. It enables developers to view licenses and top-issue severities directly from the `pom.xml`.

{% hint style="info" %}
Ensure Maven is installed and that the `mvn` command is available in your system `PATH`.

If your project includes the Maven Dependency Plugin with include/exclude configurations, scanning will be disabled.
{% endhint %}

For example:

```
      <plugins>
        <plugin>
          <groupId>org.apache.maven.plugins</groupId>
          <artifactId>maven-dependency-plugin</artifactId>
          <configuration>
            <includes>org.apache.*</includes>
          </configuration>
        </plugin>
      </plugins>
```

### Npm Projects

The extension builds the npm dependencies tree using `npm list`. It provides insights into licenses and top-issue severities directly from `package.json`.

**Prerequisite:**

* Ensure the npm CLI is installed and in your system `PATH`.
* Dependencies must be installed using `npm install` before scanning.

### Yarn v1 Projects

The extension builds the Yarn dependencies tree using `yarn list`, displaying license and security issue details from `yarn.lock`.

**Prerequisite:**

* Ensure the Yarn CLI is installed and in your system `PATH`
* Yarn v2 is not yet supported

### Pypi Projects

The extension constructs the PyPi dependencies tree using `pipdeptree` your Python virtual environment. It also relies on the Python interpreter path configured in the Windsurf Editor Python extension.

**Prerequisites:**

* Install the Windsurf Editor Python extension.
* Ensure Python (2 or 3) is available in your system `PATH`.
* Set up and activate a virtual environment following Windsurf Editor documentation:
  * **Mac/Linux:** `source <venv-dir>/bin/activate`
  * **Windows:** `.<venv-dir>\Scripts\activate`
* Install your project dependencies within the activated virtual environment.

### .NET Projects

For .NET projects using NuGet packages, the extension visualizes the NuGet dependencies tree along with relevant details.

**Prerequisites:**

* If your project defines NuGet dependencies in `packages.config`, ensure the `nuget` CLI is installed and available in your system `PATH`.
* Restore project dependencies using `nuget restore` or `dotnet restore` before scanning.
* Click the **Refresh** button after restoring dependencies to update the tree view.
