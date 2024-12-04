# What is Xray?

JFrog Xray is a universal software composition analysis (SCA) solution that natively integrates with Artifactory, giving developers and DevSecOps teams an easy way to proactively identify vulnerabilities on open source and license compliance violations, before they manifest in production releases.

Main Features and Functionality
Early Detection: Xray identifies security vulnerabilities and license violation as early as the dependency declaration stage and blocks builds with security issues from development. Automated and continuous governance and auditing of software artifacts and dependencies throughout the software development lifecycle from code to production.

Self-hosted, Cloud, Hybrid or Multi-Cloud Solution: Xray is available self-hosted (self-managed) and on the cloud. Xray Cloud is hosted on your choice of Amazon Web Services, Google Cloud Platform, or Microsoft Azure, allowing you to maintain infrastructure with automated server backups, free updates and guaranteed uptime.

Deep Recursive Scanning: Xray recursively scans artifacts, builds and Release Bundles in your system, drilling down to analyze even the smallest binary component that affects your software. For example, when analyzing a Docker image, if Xray finds that it contains a Java application it will also analyze all the .jar files used in this application.

Continuous Impact Analysis: Xray analyzes how an issue in one component affects all others in your company and displays the chain of impact in a component graph, allowing you to have a clear understanding of the impact one component has on another. It is continuously updated with new security vulnerabilities, performing an impact analysis to determine all artifacts affected by the issue.

Native Integration with Artifactory: Xray is the only security scanning tool that is natively integrated with JFrog Artifactory. As a complementary product to JFrog Artifactory, Xray has access to the wealth of metadata Artifactory stores which, combined with deep recursive scanning, puts Xray in a unique position to analyze the relationships between binary artifacts and provide radical transparency into your component architecture to reveal the impact that a vulnerability in one component has on any other.

Vulnerability Database: Xray comes with JFrog’s vulnerabilities database on OSS components, to which integrates data from Vulnerability databases and security advisories including NVD, GitHub, Ubuntu, Debian, Red Hat, PHP and enriched by the JFrog Security Research team to give more specific and detailed information on the vulnerability, its use cases and options for mitigations.

Custom API-Driven Automation: Through an open REST API, Xray lets you define a custom regimen of automated analysis for all components in your system.

Dependencies Scan: Scan your sources' dependenciesusing the JFrog CLI for vulnerabilities and licenses violations.

On-Demand Binary Scan: Point to a binary in your local file system and receive a report that contains a list of vulnerabilities and licenses for that binary using the JFrog CLI.

SBOM: Enable DevSecOps engineers to understand and analyze the dependencies of their components. To learn more, see Xray SBOM Report

JFrog Security CVE Research and Enrichment: JFrog's security research team helps you with enhanced analysis on CVE findings in a way that allows you to focus on the most important issues with the capability of finding the best resources invested in fixing them. For more information, see JFrog Security CVE Research and Enrichment

Component's Operational Risk: Provides you with additional data on OSS components that will help you gain insights into the risk level of the components in use. For more information, see Components Operational Risk

JFrog Advanced Scans: Includes IaC security, secrets detection, contextual analysis and detection of OSS library and services misconfiguration or misuse. For more information, see JFrog Advanced Security

Universal Artifact Analysis: In line with JFrog’s universal approach, JFrog Xray performs artifact analysis for all major package formats across the CI/CD pipeline. Xray understands each package type, knows how to unpack it and what every underlying layer contains.

Xray currently supports the following package formats with new formats added regularly.

| Package             | Extensions                             | Description                                                                                                       |
|---------------------|----------------------------------------|-------------------------------------------------------------------------------------------------------------------|
| **Go**              | None                                   | Scans and indexes Go Registries, Modules, and packages; includes recursive analysis and component graph integration. |
| **Conda**           | conda                                  | Scans Conda packages for security vulnerabilities and operational risks.                                         |
| **PHP**             | All archive types                      | Recursively scans Composer packages and their dependencies for potential issues.                                  |
| **Maven**           | jar, war, ear, nupkg, sar, har, hpi, cpa, jpi, all archive types | Scans Maven project dependencies directly within IntelliJ IDE.                                                  |
| **Bower**           | All archive types                      | Scans packages, performing impact analysis to monitor compliance.                                               |
| **Gradle**          | jar, war, ear, nupkg, sar, har, hpi, cpa, jpi, all archive types | Recursively scans Gradle packages and integrates with the component graph.                                       |
| **Ivy**             | jar, war, ear, nupkg, sar, har, hpi, cpa, jpi, all archive types | Conducts recursive scans and impact analysis on Ivy packages.                                                    |
| **SBT**             | jar, war, ear, nupkg, sar, har, hpi, cpa, jpi, all archive types | Scans packages and monitors for new vulnerabilities.                                                             |
| **npm**             | All archive types                      | Analyzes JavaScript files within npm packages to ensure usage safety.                                           |
| **NuGet**           | nupkg, DLL, exe, all archive types     | Scans NuGet packages and their dependencies for vulnerabilities.                                                |
| **PyPI**            | whl, egg, all archive types            | Recursively checks Python packages for vulnerabilities.                                                          |
| **Docker**          | Not identified by extension            | Identifies components in Docker images and layers for vulnerabilities.                                          |
| **OCI**             | Not identified by extension            | Scans components in OCI images similar to Docker.                                                                |
| **Debian**          | deb                                    | Detects and scans Debian packages for issues in Docker/OCI containers.                                          |
| **RPM**             | rpm                                    | Identifies RPM packages in containers and checks for vulnerabilities.                                           |
| **RubyGems**        | gem                                    | Scans RubyGems packages for security issues recursively.                                                         |
| **Alpine**          | apk                                    | Scans Alpine’s repositories and packages for vulnerabilities.                                                    |
| **Conan**           | conanmanifest.txt                     | Scans Conan packages for vulnerabilities.                                                                        |
| **Cargo**           | crate                                  | Scans Rust Cargo packages, providing insights on vulnerabilities.                                               |
| **CRAN**            | All archive types                      | Scans R packages for security vulnerabilities and risks.                                                        |
| **Hugging Face ML** | Not identified by extension            | Scans ML models for licenses and malicious content.                                                              |
| **Terraform State** | Not identified by extension            | Scans Terraform state for cloud service configuration issues.                                                    |
| **Chainguard Images** | Not identified by extension          | Scans Chainguard images for SBOM and SCA.                                                                       |
| **CycloneDX SBOM**  | cdx.json, cdx.xml                    | Scans CycloneDX files and populates vulnerability data.                                                          |
| **Machine Learning Model** | Various binary formats         | Scans various ML model binaries for vulnerabilities in Docker and Generic repositories.                          |
| **CocoaPods**       | podspec                               | Scans CocoaPods packages for security vulnerabilities and compliance.                                            |


| Type                          | Supported                                    |
|-------------------------------|----------------------------------------------|
| **Supported Archive Types**    | 7zip, Zip, TAR, VMDK, OVA, CPIO, ISO, RAR, AAR |
| **Supported Compression Types** | gz, xz, bz2, zstd, lzma                    |