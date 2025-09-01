# Features and Capabilities

JFrog Catalog provides security, compliance, and operational risk analysis through various features:

**Search Capabilities:**

* **Package Search** – Find any supported package or Common Vulnerabilities and Exposures (CVEs).
* **CVE Search (Upcoming Feature)** – Identify and analyze vulnerabilities augmented by JFrog’s Security Research.

**Package Detail View:**

* **Vulnerabilities**:
  * **Non-transitive CVEs** – Risks related to the specific package.
  * **Transitive CVEs** – Risks inherited from dependencies.
  * **JFrog Enriched Data** – Additional insights on mitigating CVEs.
* **Dependencies Analysis**:
  * **Table View** – Lists direct and indirect dependencies.
  * **Graph View** – A visual dependency tree showing risk propagation.
* **Licensing Information**:
  * Displays OSS license requirements for compliance.
  * Helps legal teams assess software usage risks.&#x20;
  * Submit a review request for missing or incorrect package licenses directly from the Catalog UI. The JFrog research team validates the license, updates the Catalog, and notifies the user once the review is complete.
* **OpenSSF Score**:
  * Evaluates open-source project security risks.
  * Enables informed decisions on accepting dependencies.

**Comparison & Automation:**

* **Package Comparison** – Compare vulnerabilities, dependencies, and licenses across multiple packages or versions.
* **GraphQL API** – Retrieve bulk package information, automate workflows, and integrate external tools.
* **Catalog Labels** – Categorize and manage packages for curation policies.
