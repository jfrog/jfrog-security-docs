# JFrog Security Research

### **CVE Research and Enrichment in JFrog Security**

#### **The Challenge**

Modern software artifacts often contain **hundreds or even thousands of CVEs**, making it **impractical** to address every single one. Security teams typically rely on **CVSS scores** and **technical security advisories** to prioritize vulnerabilities, but this approach has several **limitations**:

* **Limited risk insight**: CVSS scores alone do not provide a clear picture of **real-world risk**.
* **No exploitability analysis**: They do not assess the **likelihood of exploitation** in actual attack scenarios.
* **Generic scoring formulas**: The fixed weights in CVSS calculations may not accurately reflect the **true risk** of a CVE.
* **Incomplete technical advisories**: Security bulletins often lack **detailed conditions for exploitation** or **alternative mitigation options** beyond upgrading the affected software.

Given these challenges, organizations struggle to determine **which vulnerabilities pose an actual threat** and how to **efficiently prioritize fixes**.

***

#### **The JFrog Solution: CVE Research and Enrichment**

JFrog’s **Security Research and Threat Intelligence teams** continuously analyze both **new and existing CVEs** to assess their **real-world exploitability** and impact. This analysis results in a **JFrog Research Severity Score**, which provides **deeper insights** into each CVE, including:

✔ **Exploitability analysis** – How likely is the vulnerability to be weaponized?\
✔ **Real-world attack data** – Has this CVE been used in documented cyberattacks?\
✔ **Impact assessment** – What is the potential damage if exploited?\
✔ **Severity refinement** – Adjustments based on deeper technical evaluation, beyond just the CVSS score.

***

#### **How JFrog Research Enhances CVEs**

After a thorough analysis, JFrog **enriches CVEs** with critical insights that help security teams make **informed decisions**:

* **Vulnerable Function Identification** – Pinpoints **which function(s) are at risk** and what type of calls make them exploitable.
* **Non-Exploitable Scenarios** – Highlights **cases where the function is disabled or not compiled**, making the vulnerability ineffective.
* **Hard-to-Exploit Configurations** – Identifies settings or conditions that **reduce exploitability**.
* **Impacted Software Components & Versions** – Specifies **exact software versions** affected.
* **Fix and Mitigation Options** – Includes **patches, workarounds, and configuration changes** to reduce risk, even if upgrading is not an option.
* **Deployment-Level Mitigations** – Security strategies that can be applied **without modifying the source code**.
* **Relevant CPU Architectures** – Clarifies if a vulnerability **only affects specific processor architectures**.

***

#### **What Should You Do with JFrog Research-Enriched CVEs?**

**Prioritize the highest-risk vulnerabilities first.** CVEs with the **highest JFrog Security Severity Score** are **most likely** to be targeted by real-world attackers. These should be addressed **immediately** to **drastically lower the risk** of exploitation.

**Leverage JFrog’s Fix and Mitigation Options:**

* Some fixes are **quick and easy**, while others may require more effort.
* JFrog provides **alternative mitigation strategies**, including **patching, code fixes, configuration changes, or deployment-level protections**.

By utilizing **JFrog’s CVE Research and Enrichment**, organizations can **prioritize threats more effectively**, allocate resources efficiently, and **secure their software with confidence**.
