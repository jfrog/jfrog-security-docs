# Features and Capabilities

JFrog Curation includes several core features to enforce security, compliance, and operational control:

{% stepper %}
{% step %}
**Policy-Driven Package Governance**:

Define curation policies to enforce security, licensing, and operational rules on package downloads. Policies are evaluated at the repository level to ensure compliance. \
Policies are based on different "Conditions", custom and predefined.&#x20;

Policy actions: A policy can be blocking, blocking the developer from using the violation package, or dry-run policies. Dry-run policies are used to assess the policy impact on the organization before becoming blocking policies.&#x20;
{% endstep %}

{% step %}
**Conditions, Custom Conditions, and Condition Templates**:

* **Predefined Conditions**: Out-of-the-box rules provided by JFrog to address common security, operational, and legal risks (e.g., block malicious packages, outdated versions, or licenses).
* **Custom Conditions**: Templates allow admins to create tailored conditions. These allow organizations to address specific needs, such as blocking packages vulnerable to a specific CVE or requiring certain operational thresholds.&#x20;
* Advanced Condition settings: Some templates support more advanced configurations that create a relaxed condition. Relaxed conditions can decrease the False positive impact of the broad policies and block only packages that answer multiple parameters.\

* **Usage of conditions in Policies**:
  * Each policy contains a single condition that defines its enforcement criteria.
  * Custom conditions provide granularity and adaptability for unique organizational requirements.
  * Conditions are pivotal to determining which packages are approved or blocked during evaluations.
{% endstep %}

{% step %}
**Waivers**:

Exclude specific packages or versions from policy restrictions using waivers applied via catalog labels or manual configuration.

Waivers can be applied in 2 manners: \
1\. Package version directly applied to the policy \
2\. Catalog labels are used to mark the desired package versions, and then the label is attached to one or more policies. In case you intend to use waivers on a broader spectrum, this approach is your favorite, as it supports bulk actions and the re-usage of labels on other policies.&#x20;
{% endstep %}

{% step %}
**Audit and Reporting**:\
Audit is a crucial function of Curation. Every package inspected in Curation has an audit event log. If the package is blocked or bypassed due to a policy relaxation condition, it is mentioned in the event log.&#x20;

* View blocked/approved package events.
* Run dry-run evaluations to simulate policy enforcement without blocking downloads.
* Access detailed audit logs for compliance and troubleshooting.

Curation User Audit: Any user action that occurs in Curation is lagged for regulations and documentation. &#x20;
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
**Operational stats**:

Minimal performance impact, with average evaluation times of \~100ms per package request
{% endstep %}
{% endstepper %}



