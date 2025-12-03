# Export Scan Results

JFrog Xray allows you to export scan results for various security, compliance, and operational use cases. This enables organizations to analyze vulnerabilities, enforce policies, and generate detailed reports for auditing and compliance.

#### **Use Cases for Exporting Scan Results**

You can export scan results for multiple scenarios, including:

* **Security Analysis** – Identify vulnerabilities and security risks.
* **Secret Detection** _(Available in JFrog Advanced Security)_ – Detect sensitive data leaks.
* **Application Misconfigurations** _(Available in JFrog Advanced Security)_ – Identify security weaknesses.
* **Legal Compliance** – Review and manage your software licenses and legal obligations.
* **SBOM (Software Bill of Materials)** – Gain visibility into software components and dependencies.
* **Policy Violations** – Export violations related to security, compliance, and operational policies.
* **Operational Risk** – Assess the **stability, maintenance, and lifecycle** of software components.

### **How to Export Scan Results**

1. Navigate to the **Scans List** in Xray.
2. Select a resource version scan from the list.
3. Click the **\[...] (More Options) button**.
4. Select **"Export Scan Data"** and choose the desired **export type**.

### **Types of Scan Result Exports**

#### **1. Security Export**

The Security Export report provides details about detected vulnerabilities in scanned artifacts.

**Included Fields:**

* **CVE ID** – Unique identifier for the vulnerability.
* **Severity** – The standard CVSS-based severity rating.
* **JFrog Research Severity** – Adjusted severity based on JFrog’s advanced security research.
* **Component Physical Path** – The exact location of the affected component.
* **Infected Component** – The specific package or library impacted.
* **Infected Version** – The version of the affected component.
* **Edited Time** – The timestamp of the latest scan result update.
* **Applicability** _(For JFrog Advanced Security Users)_ – Indicates whether the vulnerability is actually exploitable in real-world scenarios.

#### **2. Legal Compliance Report**

This report provides an overview of software licenses associated with your components, including internally detected and externally enriched licenses.

**Included Fields:**

* **Component Name** – Name of the software component.
* **Licenses** – Detected open-source licenses associated with the component.
* **License Links** – Links to legal references for each license.
* **Package Type** – The software package format (e.g., npm, Maven, PyPI).
* **Component ID** – A unique identifier for the component.
* **Package ID** – The ID of the package in the repository.
* **Version** – The specific version of the component.

#### **3. Violations Report**

The Violations Report provides a detailed list of policy violations associated with the SCA (Software Composition Analysis) scan of an artifact.

**Included Fields:**

* **Violation Summary** – A brief description of the policy violation.
* **Severity** – Risk level of the violation (e.g., Minor, Major, Critical).
* **Violation Type** – The category of violation (e.g., Security, License, Operational Risk).
* **Watch Name** – The policy scope applied to the violation.
* **Component Physical Path** – Location of the affected artifact.
* **Component** – The specific component that triggered the violation.
* **Created Date** – Timestamp of when the violation was detected.
* &#x20;**Policy Triggered** – The policy rule that caused the violation.
* **Applicability** _(For JFrog Advanced Security Users)_ – Indicates whether the violation is **applicable in the current environment**.

#### **4. SBOM (Software Bill of Materials) Report**

The SBOM report provides a comprehensive inventory of software components and dependencies. This report helps organizations:

* **Understand software composition** and dependencies.
* **Gain visibility into open-source licenses** and compliance requirements.
* **Identify outdated components** or software reaching end-of-life.
* **Detect vulnerable components** and recently disclosed CVEs.
* **Enforce software security policies** based on risk factors.<br>

**How to Export an SBOM Report**

After an Xray scan, you can export an SBOM report using one of two industry-standard formats:

#### **Supported SBOM Formats**

**1. SPDX (Software Package Data Exchange)**

SPDX is an industry-standard format for communicating software components and license metadata.

* Useful for license management and compliance tracking.
* Supports open-source compliance reporting.

**SPDX Export Formats:**

* **Tag:Value**
* **JSON**
* **XLSX (Excel format)**

**2. CycloneDX**

CycloneDX is a lightweight SBOM format designed for software security and risk analysis.

* Focuses on security, vulnerability tracking, and exploitability.
* As of Xray version 3.67.x and above, CycloneDX SBOMs also include VEX (Vulnerability Exploitability Exchange) data, providing:
  * **Vulnerability details**
  * **Exploitability status**
  * **Technical analysis of risks**

**CycloneDX Export Formats:**

* **JSON**
* **XML**
