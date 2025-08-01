# Contextual Analysis of CVEs

When scanning for vulnerabilities, traditional tools often flag a large number of CVEs, overwhelming developers with irrelevant results. Developers must then sift through extensive lists to determine which vulnerabilities are relevant, a process that can be both time-consuming and error-prone. In many cases, vulnerabilities may not even impact your artifacts, making it difficult to know where to start.

**Vulnerability Contextual Analysis** leverages the context to eliminate false positives, ensuring that only relevant vulnerabilities are flagged. This is achieved through automated scanners that analyze how the 1st party code is using the 3rd party OSS libraries, identifying reachable paths for detected vulnerabilities. The analysis produces justification on why the CVE was flagged with the determined status, including information on what the scanner looks for, so developers can be educated, learn, and examine their code.

Our automated scanners are built by the JFrog Research group, and with the JFrog Advanced Security license **you can request research from our dedicated team, if a CVE lacks a contextual analysis scanner**, the team will prioritize building support for it.

### Research Team’s Approach to CVE Prioritization

The JFrog Security Research group which continuously performs CVE Research and Enrichment and Contextual Analysis features, considers several factors when deciding which CVEs to build a scanner for:

* **Relevant technologies for JFrog clients**: We prioritize CVEs affecting the technologies most commonly used by our clients.
* **Severity**: We focus mainly on “high” and “critical” severity CVEs (CVSS score >= 7.5), but also consider machine-learning-based severity prediction for CVEs without a CVSS score.
* **Exploits in the wild**: Vulnerabilities exploited in the wild or those with high media attention are prioritized, even if their public severity rating is lower (e.g., “medium”).

This ensures that our clients receive timely and relevant protection against the most significant security risks, with already more than 1,600+ high-profile CVEs.

### Key Benefits

* **Reduces false positives** – Filters out vulnerabilities that don’t impact your software today.
* **Provides actionable insights** – Highlights vulnerabilities with real-world impact. In the case of binary analysis, there is more context that allows for the analysis of the complete codebase from an attacker's perspective, identifying which issues are truly exploitable and what their potential impact is.
* **Actionable remediation:** Enables targeted mitigation based on the actual code, artifact, build, or Release Bundle.
* **Seamless integration for developers** – View results directly in your IDE, CLI, PR decoration (Frogbot), and the JFrog Platform.

#### Version-Specific Support

* **Rust binaries in Docker containers**: Supported in Xray **3.79.x and later**
* **.NET binaries in Docker containers**: Supported in Xray **3.95.4 and later**

### Contextual Analysis Statuses and Results

#### Vulnerability Contextual Analysis Statuses

* **Not Scanned**: Initial state—the scan wasn't invoked for the CVE or in case of unsupported technology.
* **Applicable**: The vulnerability can be exploited in the context of the scanned code or artifact.
* **Not Applicable**: The vulnerability cannot be exploited in the context of the scanned code or artifact.
* **Undetermined:** The applicability cannot be determined by static analysis (e.g. the exploitation requires user interaction).
* **Rescan Required**: A new scanner for this CVE is available, you need to rescan to retrieve applicability results.
* **Not Covered**: Scanner isn't available.
* **Technology Unsupported**: The vulnerability’s package type is currently not supported.
* **Missing Context**: Reachability analysis cannot determine the vulnerability’s applicability due to missing context. Applicability can be determined by scanning the artifact in a Docker repository in the JFrog Platform.
* **Upgrade Required**: _(Primarily for Self-Hosted)_ The Xray version needs to be updated to receive a new scanner for this CVE. A rescan is required after the upgrade is complete.\
  &#xNAN;_(SaaS)_ In rare cases, SaaS customers might see this status before the new scanner version is fully deployed to the environment. No action is required from the customer side—the scanner will operate automatically once the update is available.

#### Vulnerability Contextual Analysis Results

CVE Contextual Analysis results are available in:

* **Scans List** in the JFrog Platform from Scans List.
* **Inline** in your IDE
* **CLI** for immediate feedback
* **Pull Request Decoration** with Frogbot



