# How-Tos

## Analyze Your Results

### Viewing Vulnerabilities

The JFrog extension features a file tree displaying all vulnerabilities detected within the project. Each affected file appears as a tree node.

* **Descriptor files** (e.g., `pom.xml` in Maven, `go.mod` in Go) outline available direct dependencies. If a direct dependency contains vulnerable child dependencies, the tree will display those, denoted with an **'(indirect)'** postfix.
* Additional vulnerability nodes, such as **Contextual Analysis Vulnerabilities** (when applicable), **hard-coded secrets**, and **SAST,** may appear in other source files.

Each file node is interactive—click to expand and navigate to the corresponding file in the IDE. The extension highlights vulnerable lines for better visibility.

* Locations with vulnerabilities are marked in the editor.
* Click the **light bulb** icon next to a vulnerable line to jump to its entry in the tree view.
* Clicking on a **CVE entry** will open the issue’s location in the editor along with a **vulnerability details view** that includes impacted components, fixed versions, and impact paths.

#### **CVE Research and Enrichment**

For selected security issues, the JFrog Security [Research team](https://research.jfrog.com/) provides enriched CVE data to help prioritize fixes:

* **JFrog Severity**: JFrog Security’s assessment of the CVE’s likelihood of exploitation.
* **Research Summary**: Detailed conditions explaining CVE applicability.
* **Remediation Steps**: Fix and mitigation options.

#### **Vulnerability Contextual Analysis**

* Requires Xray v3.66.5+ and Enterprise X/Enterprise+ subscription with Advanced DevSecOps.

Xray automatically analyzes high-impact vulnerabilities to determine their real-world applicability. This includes:

* **Contextual Analysis Status**: Indicates if a CVE is applicable to your application.
* **Breakdown**: Explanation of why a CVE is relevant or not.
* **Remediation Guidance**: Contextual mitigation steps for fixing vulnerabilities.

#### **Static Application Security Testing (SAST)**

* Requires Xray v3.66.5+ and Enterprise X/Enterprise+ subscription with Advanced DevSecOps.

JFrog SAST scans detect vulnerabilities such as:

* **Injection Attacks** (SQL, Command, Code, SSRF)
* **Unsafe API Usage** (encryption, cryptographic signing, file operations)

SAST findings help developers track vulnerabilities efficiently:

* **Data Flow Analysis**: Maps the vulnerability’s lifecycle from entry to execution.
* **Fix Steps**: Provides recommended fixes and mitigation strategies.
* **Risk Assessment**: Severity classification to prioritize fixes effectively.

#### **Secrets Detection**

* Requires Xray v3.66.5+ and Enterprise X/Enterprise+ subscription with Advanced DevSecOps.

Detect exposed secrets (e.g., API tokens, credentials) within code to prevent accidental leaks.

* To ignore a detected secret, add a comment with **`jfrog-ignore`** above the affected line.

#### **Infrastructure as Code (IaC) Scan**

* Requires Xray v3.66.5+ and Enterprise X/Enterprise+ subscription with Advanced DevSecOps.

Scan **Infrastructure as Code (Terraform)** files for early detection of cloud and infrastructure misconfigurations.

## Resolve Issues

Update a vulnerable direct dependency to a fixed version directly from the vulnerable location in the editor using the **quick fix** feature.

## Ignore Findings

If **Xray watches** are used, a **closed eye icon** will appear next to a vulnerability line. Clicking on it allows you to create an **Ignore Rule** in Xray.
