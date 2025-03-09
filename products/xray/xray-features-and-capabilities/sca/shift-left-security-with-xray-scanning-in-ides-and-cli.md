---
hidden: true
---

# Shift-Left Security with Xray Scanning in IDEs and CLI

### **Xray Scanning in IDE**

**Supported IDEs:**

* **IntelliJ IDEA**
* **VS Code**
* **Eclipse**

**Key Capabilities:**

* **Real-time vulnerability detection**: Detects vulnerabilities and license violations as developers code.
* **Inline security insights**: Developers receive **instant feedback** on affected dependencies.
* **Dependency tree scanning**: Visualizes **direct and transitive dependencies** with security risks.
* **Fix suggestions**: Provides **remediation guidance** and **alternative safe versions** for affected dependencies.

#### **Example: Xray in IntelliJ IDEA**

1. Open a project in **IntelliJ IDEA**.
2. Use the **JFrog IntelliJ Plugin** to scan dependencies.
3. View **security vulnerabilities** and their impact in the IDE's **dependency tree**.
4. Select a vulnerability to see **detailed risk information**.
5. Automatically **upgrade to a safer package version** suggested by Xray.

**Why it matters:**

* Prevents **security risks from being introduced into code** at an early stage.
* Saves **developer time** by providing **quick fixes**.
* Reduces **security bottlenecks** in later CI/CD stages.

***

### **Xray Scanning in CLI**

#### **Key Capabilities:**

* **Security and compliance scanning via command-line**
* **Support for multiple package managers** (npm, Maven, PyPI, Go, Docker, etc.)
* **CI/CD integration** with scripts and automation pipelines
* **Offline scanning support** (useful for air-gapped environments)

#### **Example CLI Commands**

1.  **Scan a single artifact:**

    ```sh
    shCopyEditjfrog xr scan my-artifact.jar
    ```
2.  **Scan an entire project repository:**

    ```sh
    shCopyEditjfrog xr scan --repo=my-maven-repo
    ```
3.  **Scan a Docker image:**

    ```sh
    shCopyEditjfrog xr scan my-docker-image:latest
    ```
4.  **Generate a detailed security report:**

    ```sh
    shCopyEditjfrog xr scan --output=json > security-report.json
    ```

**Why it matters:**

* Provides **security scanning at the developer level**, **before** pushing to a repository.
* Supports **DevSecOps automation** by integrating into build scripts and CI/CD workflows.
* Works **both online and offline**, making it ideal for **secure and regulated environments**.

***

### **Shift-Left Security: Prevent Issues Before Deployment**

* **Traditional security approaches** detect vulnerabilities **after deployment**, making remediation costly.
* **Shift-left security with Xray** catches issues **before they reach production**, reducing risk early.
* **Developers take ownership of security** by fixing vulnerabilities **inside their IDEs or CLI** instead of waiting for security teams.

#### **Developer Workflow with Xray Shift-Left Scanning**

1. **Write code** in the IDE.
2. **Xray automatically scans dependencies** and **flags security risks**.
3. **Inline suggestions** provide **alternative secure versions**.
4. **Developers fix vulnerabilities before pushing code**.
5. **JFrog CLI scans before merging changes** in CI/CD pipelines.

