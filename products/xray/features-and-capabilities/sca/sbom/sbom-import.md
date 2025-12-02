# SBOM Import

### Overview

Xray allows you to import SBOMs into the platform — enabling multiple use cases:

* Enrich SBOMs generated from external tools with vulnerability (VEX) and license obligation information.
* Enrich artifacts with SBOM data for aggregated SBOM and scan results.

### How to Import SBOMs to Xray

1. Upload an SBOM file in one of the supported formats to an indexed generic repository:
   * **CycloneDX**: `.cdx.json` or `.cdx.xml`
   * **SPDX**: `.spdx.json` or `.spdx.xml`
2. Once uploaded, Xray automatically indexes and scans the SBOM file.

The scanned SBOM will now appear in your **Scans List**.

### How to Aggregate Artifacts with SBOM Data

1. Add the SBOM file (`.cdx.json`, `.cdx.xml`, `.spdx.json`, or `.spdx.xml`) to the scanned artifact (for example, a Docker image or archive).
2. The referenced information from the SBOM is automatically added to the artifact's scan results.

&#x20;The artifact scan now includes all SBOM-referenced components.

### How to Enrich SBOM Data Using the JFrog CLI

Follow the procedure in [Enrich Your SBOM](../../../../../developers/cli/enrich-your-sbom-jsons-and-xmls.md) to add Xray’s vulnerability and license data to an external SBOM using the JFrog CLI.

