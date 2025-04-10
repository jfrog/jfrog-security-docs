# Developers

The Developers section includes documentation for the JFrog Security CLI and integrations, providing developers and administrators with the tools to automate security workflows and enhance the development experience. The guides offer comprehensive instructions and best practices to help secure your software development lifecycle using:

* JFrog Security [CLI](cli/)
* Code Security within Your [IDEs](ides/)
* Scanning Source Code Repositories with [Frogbot](frogbot/)

### Source vs. State: How Scans Differ

The developers' tools scans work directly on the source files, such as Terraform configurations, representing the intended infrastructure setup. In contrast, platform scans analyze the state files—JSON files that capture the actual deployed state of your infrastructure. This means the developers' tools provide insights based on the code you write, while the platform reflects the real-world implementation.&#x20;

### System Requirements

The system requirements for enabling security scans using the JFrog Security CLI, IDE plugins, and Frogbot are:

| Operating System | Supported Versions  | Minimum Required Version |
| ---------------- | ------------------- | ------------------------ |
| RHEL             | 8 and above         | 8                        |
| CentOS           | 9 and above         | 9                        |
| Ubuntu           | 18.04, 20.04, 22.04 | 18.04                    |

### Air-Gapped Environments

[Air-gapped environments](working-in-air-gapped-environments.md) are physically isolated systems disconnected from unsecured networks, used to protect sensitive data from cyber threats, malware, and remote hacking.
