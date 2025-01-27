# Xray

JFrog Xray is a universal software composition analysis (SCA) solution that natively integrates with Artifactory, giving developers and DevSecOps teams an easy way to proactively identify vulnerabilities on open source and license compliance violations, before they manifest in production releases.

> Jfrog Xray is supported on the Cloud platform with an Enterprise X or Enterprise+ license, and on the Self-Hosted platform.

## Main Features

#### General

* **Flexible Deployment Options** : Available as self-hosted, cloud, hybrid, or multi-cloud solutions on AWS, Google Cloud, and Microsoft Azure.
* **Native Integration with Artifactory** : Provides enhanced analysis through integration with JFrog Artifactory, leveraging shared metadata.
* **On-Demand Binary Scan** : Enables instant vulnerability reports for specific binaries through local file system scans.
* **Aggregated Reporting Features** : Xray provides an integrated view of findings from JFrog Security products, enabling organizations to generate customizable reports that encompass vulnerabilities, licensing compliance, policy violations, and operational risks. Each report allows users to define specific scopes and apply advanced filters for tailored insights, ensuring a comprehensive understanding of security and compliance across artifacts, builds, and release bundles. All reports are accessible through the JFrog Platform and REST API, facilitating easy integration into existing workflows.
* **JIRA Integration**: Seamlessly integrates with JIRA to streamline issue tracking and resolution processes, allowing security vulnerabilities and policy violations detected by Xray to be automatically logged as JIRA tickets. This integration facilitates collaboration between development and security teams, ensuring timely remediation and enhanced project management.

#### SBOM

* **Vulnerability Detection -** Identifies security vulnerabilities inside your binaries - enriched by world-class database of OSS vulnerabilities from multiple sources, facilitating informed risk management.
* **License Detection and Management - Identify software licenses //TODO**
* **Operational Risk Insights** : Assesses OSS components to provide insights into their risk levels for informed decision-making.
* **Dependency Detection -** Understand dependency relationship between software components in your binaries - facilitating direct-source fixes and better contextual understanding of your software.
* **SBOM Standards Compliant Reports** : Generates Software Bill of Materials (SBOM) reports that comply with industry standards and are available in CycloneDX and SPDX formats. These reports can also incorporate Vulnerability Exploitability eXchange (VEX) information to provide detailed insights into the exploitability of identified vulnerabilities.

#### SDLC Policy Management

* **Comprehensive Rule-based Policy** : Implements customizable, rule-based policies to enforce security and compliance standards throughout the software development lifecycle, ensuring that builds meet organizational guidelines before deployment.
* **Extensible Policy Scoping (Watches)** : Allows users to define granular policy scopes, known as "Watches," that can monitor specific artifacts , repositories, builds and release bundles, enabling a tailored approach to policy enforcement based on organizational needs.
* **Intricate Waiver Mechanism (Ignore Rules)** : Provides a sophisticated waiver mechanism allowing teams to temporarily ignore certain policy violations under specific conditions, facilitating flexibility while maintaining overall compliance and security objectives.
