# Xray Reports
Xray reports allows you to generate an aggregarted view of Jfrog Security products findings and results.

Current supported report types: 

* Vulnerabilities

* Legal (Licensing and Copyright) 

* Policy Violations 

* Operational 

## Vulnerabilities Report
The Vulnerabilities report provides information about vulnerabilities in your artifacts, builds, and release bundles. In addition to the information provided in the JFrog Platform on each of these entities, the report gives you a wider range of information such as vulnerabilities in multiple repositories, builds and release bundles. Criteria such as vulnerable component, CVE, cvss score, and severity are available in the report. You can define the information you want to see by defining a scope and advanced filters that provide you with a flexible vulnerabilities report, that is available both through the JFrog Platform and REST API.

## Legal Report
The Legal report provides you with a list of components and artifacts and their relevant licenses. This enables you to review and verify that the components and artifacts comply with the license requirements. This report provides due diligence license-related information on each component for a selected scope. Due diligence license information includes information such as unknown licenses and unrecognized licenses found in your components. You can define the information you want to see by defining a scope and advanced filters that provide you with a flexible due diligence report, that is available both through the JFrog Platform and REST API.

## Violations Report

 > Violations report requires Artifactory version 7.10.6 and above.

The Violations report provides you with information on security and license violations for each component in the selected scope. Violations information includes information such as type of violation, impacted artifacts, and severity. You can define the information you want to see by defining a scope and advanced filters that provide you with a flexible violations report, that is available both through the JFrog Platform and REST API.

## Operational Risk Report

The Operational Risk report provides you with additional data on OSS components that will help you gain insights into the risk level of the components in use, such as; EOL, Version Age, Number of New Versions, and so on. For more information, see Components Operational Risk. You can define the information you want to see by defining a scope and advanced filters that provide you with a flexible violations report, that is available both through the JFrog Platform and REST API.