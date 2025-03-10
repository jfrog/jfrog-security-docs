# How to Compare and Select the Best OSS Package for Your Project

**Use Case:** A developer needs to choose between multiple versions of an OSS library and wants to compare **security, dependencies, and licensing information** before making a decision.

**Steps:**

1. **Search for the Package**
   * Open **JFrog Catalog** and enter the package name.
   * View **all available versions** of the package.
2. **Compare Package Versions**
   * Click on the **Compare Packages** button.
   * Select multiple versions of the same package (or compare entirely different packages).
   * Review the differences in:
     * **Vulnerabilities** – Are there security risks in newer versions?
     * **Dependencies** – Does one version introduce risky dependencies?
     * **License Type** – Does one version have a more permissive license?
3. **Make an Informed Decision**
   * If a newer version has fewer vulnerabilities and a compatible license, **recommend upgrading**.
   * If security risks exist, discuss **patching options** or consider alternative OSS packages.
4. **Integrate Secure OSS into the Build Pipeline**
   * Once the best package is selected, **update your dependency manager** (e.g., `package.json`, `pom.xml`, `requirements.txt`).
   * Document the rationale for selecting the package to support compliance audits.
