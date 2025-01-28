# Configure Curation

Key configuration tasks required for JFrog Curation:

{% stepper %}
{% step %}
[**Configure Curation Service for Self-Hosted**](initial-setup/configure-curation-for-self-hosted.md)

* Ensure compatibility with Xray and Artifactory versions.
* Validate entitlements using the JFConnect microservice.
* Set up Catalog Central service credentials and whitelist necessary services.
{% endstep %}

{% step %}
[**General**](initial-setup/general.md)

* Enable the Curation Service
* Configure Notifications
* Set the Policy Engine Behavior
{% endstep %}

{% step %}
[**Configure Repositories**](configure-repositories/)

* Connect remote repositories to the Curation service.
* Enable pass-through on specific repositories if needed.
{% endstep %}

{% step %}
### [Create Custom Conditions](create-custom-conditions.md)


{% endstep %}

{% step %}
[**Create Policies**](create-policies/)

* Define policy scope, conditions, and waivers.
* Configure actions (e.g., block or dry-run) and notifications
{% endstep %}
{% endstepper %}

