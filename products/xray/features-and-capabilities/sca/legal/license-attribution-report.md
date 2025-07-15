# License Attribution Report

{% hint style="info" %}
Attribution reports prerequisites:

1. Catalog service is required for self-hosted instances -[ catalog installation guide](https://jfrog.com/help/r/jfrog-installation-setup-documentation/installing-catalog)
2. Set feature flag `sbom.retrieveCopyrightsFromCatalog: "true"` in Xray  `system.yaml`&#x20;
3. Supported for REST API only: [Legal Attribution Report](https://jfrog.com/help/r/xray-rest-apis/legal-attribution-report)
{% endhint %}

The **License Attribution Report** (Starting from Xray version 3.124.x and above) is a compliance-focused document that lists all open-source components bundled in a specific artifact or release along with their respective license obligations and attribution requirements. It is designed to help organizations meet the legal obligations associated with using third-party open-source software.&#x20;

Most open-source licenses — such as **MIT**, **Apache-2.0**, or **BSD** — require that certain attribution information be included when software is redistributed. These obligations typically include preserving the license text, providing credit to original authors, and, in some cases, including additional notices or disclaimers.

The License Attribution Report automates the collection and formatting of this information into a single, easily shareable file to support compliance during distribution, audits, or legal reviews.

#### Supported Packages

The attribution report is currently available for the following package types:

* **NPM**
* **Maven**
* **Go (Golang)**
* **PyPI (Python)**

**Upcoming Package types:**

* **NuGet**

#### What’s Included in the Report

Each License Attribution Report includes the following elements for each component:

* **Component Identifier**: Includes package name, version, and package type (e.g., npm:lodash@4.17.21).
* **Associated Licenses**: Lists all licenses declared for the component (e.g., MIT, Apache-2.0).
* **Copyright Information**: Extracted from license files, source code headers, or manifest files.
* **Full License Text**: Complete, unmodified license text as provided in the original open-source package.
* **(Coming Soon)**: **Required Notices** – For licenses like Apache-2.0 that mandate a NOTICE file, this section will capture and display the content of that file.

> **Current Output Format**: The report is generated in **PDF format** only.

