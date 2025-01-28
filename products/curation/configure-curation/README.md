# Configure Curation

Key configuration tasks required for JFrog Curation:

{% stepper %}
{% step %}
[**Configure Curation Service**](broken-reference) **for Self-Hosted**:

* Ensure compatibility with Xray and Artifactory versions.
* Validate entitlements using the JFConnect microservice.
* Set up Catalog Central service credentials and whitelist necessary services.
{% endstep %}

{% step %}
[**Initial Setup**](initial-setup.md):

*
{% endstep %}

{% step %}
[**Manage Repositories**](manage-repositories.md):

* Connect remote repositories to the Curation service.
* Enable pass-through on specific repositories if needed.
{% endstep %}

{% step %}
[**Create Policies**](create-policies.md):

* Define policy scope, conditions, and waivers.
* Configure actions (e.g., block or dry-run) and notifications.
{% endstep %}

{% step %}
**Health Checks**:

* Use the Curation health-check endpoint to verify component availability.


{% endstep %}
{% endstepper %}

