# IDEs

{% hint style="info" %}
Local SAST _MCP is available with the Unified Security Bundle or the Ultimate Security Bundle_
{% endhint %}

This section provides documentation on integrating JFrog Security with popular IDEs. By embedding security analysis directly into the development workflow, developers can identify vulnerabilities, misconfigurations, and exposed secrets in real time. The guides cover installation, setup, and how to leverage JFrog's advanced security features for seamless, in-editor security scanning and remediation.

### Before You Begin

It is essential that you:

* Meet the [system requirements](../#system-requirements)

### Key Security Capabilities

* Software Composition Analysis (SCA) with Contextual Analysis
* Secrets Detection and Token Validation
* Infrastructure as Code (IaC) Scanning
* Static Application Security Testing (SAST)

### Choosing Between JFrog Extension and JFrog SAST MCP

#### Use JFrog Extension

Use JFrog extension if you want the full security experience—including **SCA, Secrets, IaC**, **Contextual Analysis**, and **SAST** and have the ability to view all findings, rerun scans, and get a richer UI. This setup is recommended for ongoing, in-depth use.

#### Use JFrog SAST MCP

Use [JFrog SAST MCP](local-sast-mcp/) if you're looking for a quick and simple experience focused only on **SAST** findings, and already have your IDE AI assistant installed. This approach requires MCP setup.
