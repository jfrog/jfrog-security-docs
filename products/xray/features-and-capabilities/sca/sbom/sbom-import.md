# SBOM Import

## Overview

Xray allows you to import SBOM's into the platform - allowing multiple use cases:

* Enriching SBOM generated from external tools with Vulnerability information (VEX) and Legal Obligations.
* enriching  Artifacts with SBOM data for aggregated SBOM & Scan results.

> SBOM Import is currently supported for CycloneDX format only



## How Import SBOM to Xray

1. Upload a CycloneDX file with ".cdx.json" / ".cdx.xml" suffix to a indexed generic repository
2. Done! the scanned sbom will now appear in your scan list



## How to Aggregate Artifacts with SBOM data&#x20;

1. add the ".cdx.json" or ".cdx.xml" SBOM file to the scanned artifact (Docker,Archive etc.)
2. Done! the refernced information in the SBOM will now be added to your artifact scan results

