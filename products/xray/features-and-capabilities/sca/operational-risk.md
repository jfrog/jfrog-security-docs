# Operational Risk

Beyond security vulnerabilities and compliance issues, operational risks in software components can impact system reliability, maintainability, and overall software quality. These risks arise from outdated, deprecated, or unmaintained dependencies that may no longer receive updates, security patches, or community support.

JFrog Xray provides Operational Risk Analysis, enabling organizations to detect and mitigate risks before they affect production environments. By identifying software components with end-of-life (EOL) statuses, deprecated libraries, and maintenance concerns, teams can make informed decisions to maintain software stability and long-term viability.

### **What is Operational Risk in Software?**

Operational risk refers to non-security-related issues that can affect a software component’s performance, reliability, or maintainability.

**Currently supported**: NPM and Maven packages.&#x20;

Common operational risks include:

* **End-of-Life (EOL) Software** – Components that no longer receive updates or security patches.
* **Deprecated Dependencies** – Libraries marked as obsolete or replaced by newer versions.
* **Unmaintained Open-Source Projects** – Software that hasn’t been updated for a long period, increasing the risk of compatibility issues.
* **High-Impact Component Updates** – Major version changes that introduce breaking changes or API modifications.
* **Abandoned Projects** – Open-source components with no active contributors or maintainers.

### **How Xray Detects Operational Risks**

Xray continuously monitors software components in **repositories, builds, and release bundles**, identifying key operational risks based on:

* **Version Stability** – Detects if a component hasn’t been updated for an extended period.
* **End-of-Life Status** – Flags software that has reached EOL and no longer receives support.
* **Community and Maintenance Health** – Analyzes activity levels of open-source maintainers.
* **API and Compatibility Changes** – Identifies major version changes that may introduce breaking updates.
* **License Status Changes** – Notifies teams when license modifications impact compliance.

### Operational Risk Workflow in Xray

1. Create an Operational Risk Policy.
2. Attach Policy to Watch.
3. View Operational Risk Data in the Xray > Scans List.
4. View Operational Risk violations generated based on the Policy rules you set

### **Mitigating Operational Risks with Xray**

#### **1. Monitor Dependencies Continuously**

* Apply Operational Risk Policies to repositories and builds.
* Detect outdated and deprecated dependencies before they impact production.

#### **2. Enforce Governance in CI/CD Pipelines**

* Configure Xray to fail builds if they contain high-risk operational components.
* Require dependency reviews before promoting artifacts.

#### **3. Plan for End-of-Life Transitions**

* Track EOL software and migrate to actively maintained alternatives.
* Avoid dependencies that lack long-term maintenance support.

#### **4. Establish a Risk Management Strategy**

* Regularly audit software dependencies for compatibility and lifecycle health.
* Work with open-source communities to assess long-term viability.

### How Xray Determines Operational Risk Severity

Xray calculates the Operational Risk as High, Medium, Low, and None (no known risk) using the following criteria. For information on how Xray calculates operational risk effective severity, see the table **Calculating Operational Risk Effective Severity** further below.

| Risk                          | Type                          | Severity                                                                                                                                           | Notes                                                                                                                                                            |
| ----------------------------- | ----------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| End-of-Life                   | Boolean                       | <p>High = True</p><p>None = False</p>                                                                                                              |                                                                                                                                                                  |
| Version Age                   | Number                        | <p>Number of months since release / 10</p><p>High >= 4</p><p>Medium > 2 and &#x3C; 4</p><p>Low > 1 and &#x3C;= 2</p><p>None (no risk) &#x3C;=1</p> |                                                                                                                                                                  |
| Number of New Versions        | Number                        | <p>Number of versions since / 2</p><p>High >= 6</p><p>Medium >= 4 and &#x3C; 6</p><p>Low >= 2 and &#x3C; 4</p><p>None (no risk) &#x3C; 2</p>       |                                                                                                                                                                  |
| Health of Open Source Project |                               |                                                                                                                                                    |                                                                                                                                                                  |
|                               | Release cadence per year      | <p>Healthy >= 2 releases</p><p>Unhealthy &#x3C;= 1</p>                                                                                             | <p>This includes all releases. Including any dot releases and patch releases if they are GA releases.</p><p>When there is no data, it is presumed as healthy</p> |
|                               | Number of commits per year    | <p>Healthy >= 100 commits</p><p>Unhealthy &#x3C; 100 commits</p>                                                                                   |                                                                                                                                                                  |
|                               | Number of committers per year | <p>Healthy > = 5 committers</p><p>Unhealthy &#x3C; 5 c ommitters</p>                                                                               |                                                                                                                                                                  |

**Calculating Operational Risk Effective Severity**

| # | EOL  | Health    | # of new versions       | Version Age             | Combine Severity | Risk Reason                                                       |
| - | ---- | --------- | ----------------------- | ----------------------- | ---------------- | ----------------------------------------------------------------- |
| 1 | High | Any       | Any                     | Any                     | **High**         | **EOL**                                                           |
| 2 | None | High Risk | Any                     | Any                     | **High**         | **Health**                                                        |
| 3 | None | No Risk   | High                    | None, Low, Medium, High | **High**         | **Number of new versions and** **Version Age (only when High)**   |
| 4 | None | No Risk   | Medium                  | None, Low, Medium       | **Medium**       | **Number of new versions and** **Version Age (only when Medium)** |
| 5 | None | No Risk   | Low                     | None, Low               | **Low**          | **Number of new versions and** **Version Age (only when Low)**    |
| 6 | None | No Risk   | None                    | None                    | **None**         | **No given reason**                                               |
| 7 | None | No Risk   | None, Low, Medium, High | High                    | **High**         | **Version Age and number of new versions (only when High)**       |
| 8 | None | No Risk   | None, Low, Medium       | Medium                  | **Medium**       | **Version Age and number of new versions (only when Medium)**     |
| 9 | None | No Risk   | None, Low               | Low                     | **Low**          | **Version Age and number of new versions (only when Low)**        |
