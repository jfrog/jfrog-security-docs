# SBOM

The **SBOM (Software Bill of materials)** provides a comprehensive inventory of software components and dependencies. This report helps organizations:

* **Understand software composition** and dependencies.
* **Gain visibility into open-source licenses** and compliance requirements
* **Identify outdated components** or software reaching end-of-life.
* **Detect vulnerable components** and recently disclosed CVEs.
* **Enforce software security policies** based on risk factors.

## How JFrog Xray Generate SBOM's

The process of SBOM generation by JFrog Xray is comprised of the following steps:

1. **Recursively Scan Artifacts**: Identify the existence of software components, both source and binary, across [supported technologies](../../../supported-technologies.md).
2. **Extract Metadata**: For each software component, gather relevant metadata, including licenses, package identifiers, and dependencies information.
3. **Component Matching and Verification**: Perform matching against JFrog's external proprietary database to accurately identify components using a combination of parameters such as hashes, component identifiers, architecture and distribution identifiers and more.
4. **Store SBOM**: Save the generated artifact SBOM in Xray’s database for easy access, management and export.
