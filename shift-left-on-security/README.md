# Shift Left on Security

JFrog’s shift-left approach to security empowers developers to catch and fix issues early, long before software reaches production. By moving security checks to the left of the development timeline — during coding, pull requests, and local builds — teams can detect vulnerabilities, secrets, malware, and license risks when they’re easiest and cheapest to resolve. Tools like the JFrog **Security CLI**, **IDE plugins**, and **Frogbot** make it seamless to integrate security into everyday workflows: scanning code and artifacts locally, surfacing issues directly in the IDE, and automating PR reviews for dependency health.

This guide offers comprehensive instructions and best practices to help secure your software development lifecycle using:

* JFrog Security [CLI](../developers/cli/)
* Code security within your [IDEs](ides/)
* Repository scanning with [Frogbot](frogbot/)

### System Requirements

The system requirements for enabling security scans using the JFrog Security CLI, IDE plugins, and Frogbot are:

| Operating System | Supported Versions  | Minimum Required Version |
| ---------------- | ------------------- | ------------------------ |
| RHEL             | 8 and above         | 8                        |
| CentOS           | 9 and above         | 9                        |
| Ubuntu           | 18.04, 20.04, 22.04 | 18.04                    |

### Air-Gapped Environments

[Air-gapped environments](working-in-air-gapped-environments.md) are physically isolated systems disconnected from unsecured networks, used to protect sensitive data from cyber threats, malware, and remote hacking.
