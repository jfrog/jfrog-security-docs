# Scan Your Binaries

The `jf scan` and `jf docker scan` commands enable developers to perform **on-demand security scans** of their binaries **directly from their terminal**, ensuring early detection of CVEs, licenses, operational risk, and exposed secrets. By integrating seamlessly into the developer workflow, it helps catch security risks of binaries before uploading them into JFrog Artifactory — reducing remediation costs and enhancing software integrity. The scan results are displayed in the terminal for immediate feedback and are also available in the **JFrog Platform’s On-Demand Scans pane**, providing centralized visibility.

However, it's important to note that on-demand scanning is not a best practice for overall binary security; it is typically used for specific cases where immediate feedback is needed. For comprehensive security, organizations should implement continuous scanning as part of their CI/CD pipeline, ensuring ongoing monitoring and threat detection throughout the software development lifecycle.

{% hint style="info" %}
On-demand scan results are retained for seven days before being automatically deleted.
{% endhint %}

{% hint style="info" %}
C++ components might not be detected in on-demand scans
{% endhint %}
