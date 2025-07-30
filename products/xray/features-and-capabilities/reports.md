# Xray Reports

Xray reports allows you to generate an aggregarted view of JFrog Security products findings and results.

Current supported report types:

* Vulnerabilities
* Legal (Licensing and Copyright)
* Policy Violations
* Operational
* Exposures (Advanced Security customers only)&#x20;

### Vulnerabilities Report

The Vulnerabilities Report provides deep visibility into security issues across your software supply chain, including artifacts, builds, and release bundles. It supplements the vulnerability data shown in individual entity views with a centralized, flexible reporting tool.

The report is created using a guided wizard that lets you define the report scope—including repositories, builds, release bundles, and projects—and apply advanced filters such as vulnerability applicability or production environment status.

Key capabilities include:

* **Report scheduling** (daily, weekly, monthly)
* **Report sharing** via email
* **Interactive dashboards** that highlight vulnerability trends by severity and applicability, along with a top 10 vulnerabilities widget
* **Detailed table views** with search, sort, and filter options
* **Vulnerability drill-downs** with remediation guidance and contextual metadata

Reports can be accessed from the JFrog Platform UI or retrieved using the REST API.

### Legal Report

The Legal report provides you with a list of components and artifacts and their relevant licenses. This enables you to review and verify that the components and artifacts comply with the license requirements. This report provides due diligence license-related information on each component for a selected scope. Due diligence license information includes information such as unknown licenses and unrecognized licenses found in your components. You can define the information you want to see by defining a scope and advanced filters that provide you with a flexible due diligence report, that is available both through the JFrog Platform and REST API.

### Violations Report

> Violations report requires Artifactory version 7.10.6 and above.

The Violations report provides you with information on security and license violations for each component in the selected scope. Violations information includes information such as type of violation, impacted artifacts, and severity. You can define the information you want to see by defining a scope and advanced filters that provide you with a flexible violations report, that is available both through the JFrog Platform and REST API.

### Operational Risk Report

The Operational Risk report provides you with additional data on OSS components that will help you gain insights into the risk level of the components in use, such as; EOL, Version Age, Number of New Versions, and so on. For more information, see Components Operational Risk. You can define the information you want to see by defining a scope and advanced filters that provide you with a flexible violations report, that is available both through the JFrog Platform and REST API.
