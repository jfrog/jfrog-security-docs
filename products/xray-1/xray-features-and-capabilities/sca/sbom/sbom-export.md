# SBOM Export

## **How to Export an SBOM Report**

After an Xray scan, you can export an SBOM using one of two industry-standard formats:

### **Supported SBOM Formats**

#### **1. SPDX (Software Package Data Exchange)**

SPDX is an industry-standard format for **communicating software components and license metadata**.

* Useful for license management and compliance tracking.
* Supports open-source compliance reporting.

**SPDX Export Formats:**

* **Tag:Value**
* **JSON**
* **XLSX (Excel format)**

#### **2. CycloneDX**

CycloneDX is a lightweight SBOM format designed for software security and risk analysis.

* Focuses on security, vulnerability tracking, and exploitability.
* As of Xray version 3.67.x and above, CycloneDX SBOMs also include VEX (Vulnerability Exploitability Exchange) data, providing
  * **Vulnerability details**
  * **Exploitability status**
  * **Technical analysis of risks**

**CycloneDX Export Formats:**

* **JSON**
* **XML**
