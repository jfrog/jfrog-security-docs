# On-Demand Curation

On-Demand Curation extends JFrog Curation coverage to repositories and packages that are not part of the Public Catalog. When enabled, it applies curation policies in real time by retrieving package data from the On-Demand Catalog via Xray scans.

This ensures security and compliance for internal, private, and specialized packages while maintaining developer productivity.

On-demand Curation works for repositories that are not cataloged, within ecosystems already supported (e.g., Docker, Maven).

### Business Value

* **Addresses Customer Need** – Curates internal/private packages previously not covered by security policies.
* **Closes Security Gaps** – Applies consistent policies to all repositories.
* **Improves Compliance** – Ensures all components are evaluated for vulnerabilities and licenses.
* **Streamlined Management** – Single global toggle to control on-demand coverage.

### How to Enable

1. Go to **Administration → Curation Settings**.
2.

### How to Use

1. **Automatic Connection** – When enabled, all eligible uncataloged repositories are curated automatically.
2. **Package Retrieval Flow**:
   * Curation checks the Public Catalog for package data.
   * If not found, it checks the On-Demand Catalog.
   * If still not found, it triggers a real-time Xray scan and stores the results in the On-Demand Catalog.
3. **Policy Application** – Applies Vulnerabilities, Licenses, Malicious Packages, Labels, and Waivers policies.
4. **UI Indicators** – “On-demand” tags mark repositories and packages under on-demand curation.

***

### UI Reference

**Curation Settings**

* Global **Curation On-Demand** toggle.

**Repository List**

* On-demand repositories marked with tags.

**Tooltips & Color Indicators**

* Show inactive repositories or disabled package types.

**Policy Page**

* Info banners explain when certain conditions are unavailable due to scope limitations.
