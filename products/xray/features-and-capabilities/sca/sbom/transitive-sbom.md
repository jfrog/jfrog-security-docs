# Transitive SBOM

The Transitive Dependencies Feature in JFrog Xray provides comprehensive visibility into the complete dependency tree of your software artifacts. While traditional SBOM (Software Bill of Materials) analysis focuses on direct dependencies, this feature goes deeper by automatically discovering and analyzing the relationships between all components in your software supply chain.

### Transitive SBOM for Binary Artifacts

#### Technical Limitations

The Transitive Dependencies Feature currently works exclusively with **bundled artifacts -** bundled artifacts are artifacts that contain all their dependencies inside the filesystem/archive. This means:

* **Supported**: Docker Images, Builds, and Release Bundles that contain their dependencies within the package.
* **Supported:** SBOM (CycloneDX, SPDX)  files whose own dependency graphs are already resolved (provided dependencies)
* **Not Supported**: Artifacts that reference external dependencies without bundling them.

#### How It Works

1\. Declaration Extraction

The system begins by extracting dependency declarations from your artifacts. This process involves:

* **Package Analysis**: The system analyzes various package types to identify dependency specifications.
* **Declaration Parsing**: It reads dependency files (like `package.json`, `pom.xml`, `requirements.txt`, etc.) to understand what dependencies each component declares.
* **Metadata Processing**: The system processes package metadata to build a comprehensive dependency map.

2\. Dependency Resolution

Once declarations are extracted, the system resolves the complete dependency tree:

* **Graph Construction**: Creates a dependency graph showing relationships between all components
* **Relationship Mapping**: Maps direct, transitive, and first-party relationships

#### Binary Dependency Resolution

The Transitive Dependencies Feature supports binary dependency resolution for specific programming languages with their respective dependency metadata files:

| Programming Language | Package Manager | Dependency Metadata File       |
| -------------------- | --------------- | ------------------------------ |
| Java                 | Maven           | `pom.xml`                      |
| Python               | PyPI            | `pyproject.toml`, `PKG-INFO`   |
| .NET                 | NuGet           | `*.deps.json`                  |
| Go                   | Go              | extracted from compiled binary |

### Transitive SBOM for SBOM Artifacts (CycloneDX, SDPX)

The Feature leverages SBOM files' dependency fields  (CycloneDX's "dependsOn", SDPX's "dependency relationship") to construct the dependency graph of the artifact.

SBOM Transitive SBOM is not constrained by a specific package type and is dependent on the quality of the data provided in the input CycloneDX

### Features That Use Transitive SBOM

#### 1. SBOM Tree View (Advanced Security)

The SBOM Tree View provides an interactive, hierarchical visualization of your complete dependency tree:

* **Interactive Navigation**: Expand and collapse dependency levels to explore the tree
* **Relationship Visualization**: See direct vs. transitive dependencies clearly marked

#### 2. [Remediation](../../../../advanced-security/features-and-capabilities/smart-remediation/) (Advanced Security)

#### 3. Dependency Information in SBOM Export (Security Essentials)

Including the dependency relationship in your Software Bill of Materials (SBOM) is an important aspect of its completeness. This information, which maps how all software components are connected, is mandated by numerous cybersecurity frameworks to ensure supply chain transparency. An SBOM without this relational data is considered incomplete and fails to meet foundational compliance standards.

Dependency information is supported in both SPDX and CycloneDX formats.

#### Examples of Regulatory Frameworks Requiring Dependency Relationships:

*   NTIA "The Minimum Elements for an SBOM": NTIA's SBOM guidelines for EO-14028 ("Improving the Nation's Cybersecurity")

    > Requirement: The SBOM must include the "Dependency Relationship" to characterize "the relationship that an upstream component X is included in software Y".
*   OpenChain Telecom Industry  SBOM Guide:&#x20;

    > Requirement: An SBOM "SHALL contain all open source software that is delivered with the product including all of the transitive dependencies." It must also define the relationships between elements, specifying at a minimum "DESCRIBES and CONTAINS."
*   IMDRF and FDA Medical Device Regulations:&#x20;

    > Requirement: Manufacturers must provide a complete list of all software components, including commercial, open-source, and off-the-shelf items. This includes detailing all dependencies to effectively manage cybersecurity risks throughout the device's total product lifecycle.
*   Germany's BSI TR-03183:  Germany's Federal Office for Information Security (BSI) CRA-response criteria for software security in critical infrastructure.

    > Requirement: The guideline requires a comprehensive inventory of all used libraries and components, including their versions and dependencies, to enable robust vulnerability management and ensure the integrity of the software supply chain.
