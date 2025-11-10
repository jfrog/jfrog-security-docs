# Smart Remediation

The **Smart Remediation** feature provides automated, intelligent remediation guidance directly from your SBOM and Security Views.

It supports:

* **CVE-specific remediation**: Smart, context-aware remediation for a vulnerability
* **Component-based remediation**: prioritized package upgrades that reduce overall risk —even when not focusing on a single CVE.

By leveraging JFrog’s security insights, Xray pinpoints vulnerabilities in both direct and transitive dependencies, maps their impact, and recommends optimal remediation paths.

### Prerequisites:

**Self Hosted - JFrog Catalog Access**:  - To use Xray Remediation, you must have access to the **JFrog Catalog**.

**Self-Hosted  - SBOM - Remediation requires the following feature flags  in Xray's `system.yaml` :**&#x20;

* &#x20;**`sbom.enabled : true`** &#x20;
* &#x20;**`sbom.dependenciesEnabled : true`**&#x20;

### Why Transitive CVEs Matter

Most vulnerabilities in modern applications reside deep within transitive dependencies—packages that are included indirectly through other dependencies.

These issues are difficult to detect and fix because:

* Vulnerabilities may be several layers down the dependency tree.
* The impact path can be complex to trace, stemming from multiple packages that request the dependency
* Fixes require deciding between patching a transitive dependency or upgrading a direct dependency.

Xray Remediation automates this process, highlighting the most effective fix path and allowing you to choose between quick, minimal-disruption patches or broader upgrades that resolve multiple vulnerabilities at once.

### Key Use Cases

**CVE-Based Remediation**\
Identify the most effective fix version to resolve a specific CVE.

**Component-Based Remediation**\
Surface upgrades that deliver the largest overall security improvement, independent of a specific CVE.

### Challenges Addressed

* **Complex Dependency Trees** – Vulnerabilities buried in transitive dependencies require in-depth analysis to locate and remediate.
* **Manual Overhead** – Researching secure versions, generating configuration changes, and validating compatibility and policy compliance is time-consuming.
* **Lack of Strategic Context** – Without guidance, it’s difficult to know which upgrades yield the highest overall security gain.

### Core Capabilities

{% hint style="info" %}
Remediation outputs are suggestions generated from multiple information sources, including JFrog’s research information, the Resource Dependency graph, and available package and vulnerability data. Software Dependency Graphs are extremely complex objects, and not every possible scenario is viable for calculation. Remediation Suggestions represent best-effort recommendations and may not be complete or fully accurate in every case.
{% endhint %}

#### 1. Component-Based Remediation (Upgrade Suggestions)&#x20;

A general, multi-vulnerability approach that highlights upgrades with maximum security payoff.

#### 2. CVE-Based Remediation

CVE-based remediation provides targeted fixes derived from **i**mpact path analysis of the SBOM. For each vulnerability, Xray determines whether the CVE is introduced through a direct dependency or through one or more transitive dependencies, and maps the full resolution path.

Remediation suggestions are generated using ecosystem-specific resolution logic. For example, in Maven projects, Xray accounts for dependency management and override mechanisms. This ensures that the fix recommendation is valid and reproducible within the package manager’s constraints.

Xray also applies semantic versioning awareness and JFrog’s vulnerability intelligence to select the most suitable upgrade option. The engine weighs multiple candidate versions, considering:

* whether a direct upgrade resolves the vulnerable transitive component,
* whether a transitive override is required,
* and whether the resulting dependency tree introduces additional known CVEs.

This combination of transitive context analysis and ecosystem-specific upgrade logic ensures that the suggested fix is not only secure but also technically correct for the package manager in use.&#x20;

<table><thead><tr><th>Strategy</th><th width="225.15625">Description</th><th width="158.359375">Best For</th><th data-type="content-ref">Algorithm Deep Dive</th></tr></thead><tbody><tr><td><strong>Quickest Fix</strong></td><td>Chooses the nearest secure version to minimize time to patch.</td><td>Time-sensitive patches</td><td><a href="version-selection-strategies.md#strategy-1-quickest-fix-strategy">#strategy-1-quickest-fix-strategy</a></td></tr><tr><td><strong>Least Vulnerable</strong></td><td>Selects versions with the overall security posture.</td><td>Maximizing   Security Posture</td><td><a href="version-selection-strategies.md#strategy-2-least-vulnerable-fix-strategy">#strategy-2-least-vulnerable-fix-strategy</a></td></tr><tr><td><strong>Best Version (Coming Soon)</strong></td><td>Chooses the JFrog Algorithm Best version for the upgrade</td><td>General Purpose</td><td><a href="version-selection-strategies.md#strategy-3-best-version-strategy">#strategy-3-best-version-strategy</a></td></tr></tbody></table>

### Remediation Approaches

<table><thead><tr><th width="273.59765625">Approach</th><th>Description</th></tr></thead><tbody><tr><td><strong>Override Remediation (In-Lock)</strong></td><td>Forces a secure version of a transitive dependency without upgrading direct dependencies.</td></tr><tr><td><strong>Direct Dependency Fixes</strong></td><td>Upgrades direct dependencies to secure versions that remove vulnerable transitive components.</td></tr></tbody></table>

### Package Manager Support

<table><thead><tr><th>Ecosystem</th><th width="171.6484375">In-Lock</th><th width="164.359375">Direct</th><th>Code Snippet Support</th></tr></thead><tbody><tr><td>Maven</td><td>✅</td><td>✅</td><td><code>maven</code></td></tr><tr><td>NPM</td><td>✅</td><td>✅</td><td><code>npm</code>, <code>yarn</code> ,<code>pnpm</code></td></tr><tr><td>PyPI</td><td>✅</td><td>✅</td><td><code>pip</code>, <code>pdm</code>, <code>uv</code></td></tr><tr><td>Go</td><td>✅</td><td>Coming soon</td><td><code>go.mod</code></td></tr><tr><td>NuGet</td><td>✅</td><td>Coming soon</td><td>Coming soon</td></tr><tr><td>Conan</td><td>✅</td><td>Coming soon</td><td>Coming soon</td></tr></tbody></table>

### Smart Remediation Badges

| Badge                              | Meaning                                                                        |
| ---------------------------------- | ------------------------------------------------------------------------------ |
| **Non-Breaking**                   | Upgrade respects semantic versioning constraints, minimizing breakage risk.    |
| **Solve More CVEs**                | Suggested version resolves additional vulnerabilities beyond the targeted CVE. |
| **Policy Approved**  - Coming soon | Suggested version is approved to download by JFrog Curation policies           |
