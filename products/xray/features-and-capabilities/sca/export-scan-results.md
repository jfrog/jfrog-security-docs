# Export Scan Results

Xray allows you to export your artifact scan results for multiple use cases including:

* Security&#x20;
  * Vulnerabilities&#x20;
  * Secret detection (JFrog Advanced Security)
  * Application misconfigurations (JFrog Advanced Security)
* Legal Compliance&#x20;
* General SBOM&#x20;
* Policy Violations
* Operational risk of software components



## How to Export Scan Result

Press the \[...] Button at the scan result screen and press "Export Scan Data" and choose your export type.

<figure><img src="../../../../.gitbook/assets/Screenshot 2025-01-20 at 10.11.24.png" alt=""><figcaption></figcaption></figure>

## Security Export

The Security Export Include the following fields about your artifact detected vulnerabilities:

* CVE
* Severity
* JFrog Severity
* Component Physical Path
* Infected Component
* Infected Version
* Edited Time
* Applicability (For JFrog Advanced Security Users)

## Legal Compliance Report

The legal compliance report allows users to review their software components licenses - including local-file detected licenses and 3rd-party externally enriched licenses.

the Supported fields for the legal compliance report are :&#x20;

* Component Name
* Licenses
* License Links
* Package Type
* Component ID
* Package ID
* Version



## Violations Report

The Violations report allows you to export all policy violations associated with your artifact SCA scan .

The violations report fields are:&#x20;

* Violation Summary
* Severity
* Violation Type&#x20;
* Watch Name (Policy Scope)
* Component Physical Path
* Component
* Created Date
* Policy which created the violation
* Applicability (For JFrog Advanced Security Users)

## SBOM Report

SBOM is a readable inventory of software components and dependencies. The report will include SBOM data of your components, including unidentified components and open-source software. This enables you to:

* Understand components and code dependencies.
* Gain visibility into open-source licenses for the components in use.
* Be aware of the end-of-life of components, and which components need to be updated.
* Identify vulnerable components or recently identified vulnerabilities.
* Enforce organizational compliance and policies.

### How it Works

After performing an Xray scan, you can export the scan data as an SBOM report using one of the two supported SBOM formats:

* **SPDX**: Software Package Data Exchange (SPDX) is a standard format for communicating the components of software packages, including information about license copyrights. It includes several mechanisms that are especially useful for open-source software.
  * Supported formats:
    * tag:value
    * JSON
    * xlsx
* **CycloneDX**: CycloneDX is a lightweight SBOM specification designed specifically for software security requirements and related risk analysis. Starting with Xray version 3.67.x and above, the SBOM also includes VEX information, such as vulnerability details, exploitability, and detailed analysis. CycloneDX designed to be flexible, easily adaptable, with implementations for popular build systems.
  * Supported formats:
    * JSON
    * XML







