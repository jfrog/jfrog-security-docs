# Exposures Scans

### Exposures Scans <a href="#uuid-a0bf61fb-873e-f10d-b1b1-3bb8cf92cf16" id="uuid-a0bf61fb-873e-f10d-b1b1-3bb8cf92cf16"></a>

|                                                                                                                    | Subscription Information |
| ------------------------------------------------------------------------------------------------------------------ | ------------------------ |
| This feature is supported with the **Enterprise X** or **Enterprise+** license, with the Advanced Security Add-on. |                          |

In addition to Xray's software composition analysis and scanning for vulnerabilities in packages, Xray now enables you to perform scans for multiple categories that cover security issues in your configurations and the usage of open source libraries in your code. Along with other Xray capabilities, such as CVE Enrichment, ContextualAnalysis, and Operational Risk, Xray now provides end-to-end supply chain security to cover different forms of software supply chain attacks.

**The Issue**

When it comes to non-code-related security issues, they are often overlooked in an organization as a potential security threat, since they are the smallest and easiest issues to fix. This leaves your software potentially exposed to security threats due to security malpractices (e.g., missing authentication), insecure configurations (e.g., excessive privileges), weak authentication, and so on.

**The Solution**

Xray conducts an automated security scan to detect these potential security exposures in the analyzed artifact. The scan is performed via automated scanning of the artifact using static analysis scanners, which are continuously enhanced by the JFrog research team. The following sections describe the scanning categories in detail.

|                                                                                                                                                                                                                           | Note |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---- |
| <p>Exposures supports the following package types:</p><ul><li>Docker</li><li>OCI (Xray version 3.59.4)</li><li>Maven (Xray version 3.78.9)</li><li>npm (Xray version 3.78.9)</li><li>PyPI (Xray version 3.78.9)</li></ul> |      |
