# SCA

Software Composition Analysis (SCA) identifies and manages open-source and third-party components within software applications. SCA solutions help organizations detect security vulnerabilities, malicious packages, license compliance issues, and operational risks associated with external dependencies.

JFrog Xray is a universal SCA solution that integrates natively with JFrog Artifactory to provide deep visibility into the composition of software artifacts, ensuring security and compliance throughout the software development lifecycle.

**Key Capabilities:**

* **Automated Dependency Scanning:** Analyzes all layers of software, including direct and transitive dependencies.
* **Multi-Language Support:** Covers **Maven, npm, Docker, PyPI, NuGet, Go, and more**.
* **Integration with JFrog Artifactory:** Seamless scanning of artifacts stored in repositories.

Xray scans software components against its continuously updated vulnerability database, including:

* **Public CVE databases** (National Vulnerability Database, MITRE, and more)
* **JFrog Security Research Team’s enriched vulnerability insights**
* **Malicious package detection for compromised open-source libraries**
