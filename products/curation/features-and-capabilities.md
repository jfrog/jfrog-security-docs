# Features and Capabilities

JFrog Curation includes several core features to enhance security, compliance, and operational control:

{% stepper %}
{% step %}
**Policy-Driven Package Governance**:

Define curation policies to enforce security, licensing, and operational rules on package downloads. Policies are evaluated at the repository level to ensure compliance.
{% endstep %}

{% step %}
**Conditions, Custom Conditions, and Condition Templates**:

* **Predefined Conditions**: Out-of-the-box rules provided by JFrog to address common security, operational, and legal risks (e.g., block malicious packages, outdated versions, or licenses).
* **Custom Conditions**: Admins can create tailored conditions using condition templates. These allow organizations to address specific needs, such as blocking packages vulnerable to a specific CVE or requiring certain operational thresholds.
* **Condition Templates**: Templates provide flexible detection logic (e.g., identifying packages with specific vulnerabilities or licensing issues) and enable admins to customize threshold values.
* **Usage in Policies**:
  * Each policy contains a single condition that defines its enforcement criteria.
  * Custom conditions provide granularity and adaptability for unique organizational requirements.
  * Conditions are pivotal to determining which packages are approved or blocked during evaluations.
{% endstep %}

{% step %}
**Waivers**:

Exclude specific packages or versions from policy restrictions using waivers applied via catalog labels or manual configuration.
{% endstep %}

{% step %}
**Curation Pass-Through**:

Enable package downloads for audit purposes without storing them in Artifactory. Ensures violating packages are only temporarily accessible for evaluation without impacting the repository cache.
{% endstep %}

{% step %}
**Audit and Reporting**:

* View blocked/approved package events.
* Run dry-run evaluations to simulate policy enforcement without blocking downloads.
* Access detailed audit logs for compliance and troubleshooting.
{% endstep %}

{% step %}
**Integration with JFrog CLI**:

Developers can use the CLI to

* Check curation violations for a project.
* View detailed policy decisions for specific packages.
{% endstep %}

{% step %}
**Curation-Catalog Integration**:

* The Global Catalog serves as a metadata repository for package evaluation, enabling the Curation service to assess and block/approve packages in real time.
* Dynamic metadata updates ensure packages are evaluated against the latest security and licensing data.
* Organizations can manage both public and private metadata through the catalog for tailored curation capabilities.
* Use labels in the JFrog Catalog to group and manage packages based on organizational requirements. These labels can be applied to:
  * **Allowlists**: Accept only pre-verified packages for use.
  * **Blocklists**: Block specific packages or versions at scale.
  * **Waivers**: Exclude labeled packages from curation restrictions.
{% endstep %}

{% step %}
**Seamless Integration with Xray**:

Leverages Xray vulnerability and license data to ensure consistent and thorough package evaluation.
{% endstep %}

{% step %}
**Operational Metrics**:

Minimal performance impact, with average evaluation times of \~100ms per package request
{% endstep %}
{% endstepper %}



