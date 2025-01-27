# JFrog Security Research

## CVE Research and Enrichment

**The Issue**

Software artifacts typically have a very high number of CVEs, in some cases, security reviews have found over 1K CVEs, but handling all of these CVEs is practically impossible. Usually, the common way of deciding which CVEs to resolve is based on CVSS scoring, as well as published technical information on the relevant security advisories. This can be very challenging and an insufficient method for understanding the actual risk raised by a vulnerability for the following reasons:

* CVSS scoring provides very limited insight into the actual risk that the CVE poses.
* CVSS scoring does not contain a deep analysis on the chances of real-world exploitation.
* The values inserted into the CVSS formula do not represent either the common case or the preconditions that are needed for successful exploitation.
* The fixed weights of the CVSS formula do not reflect the actual risk in some cases.

In addition, the published technical information of CVEs in security advisories, is sometimes very limited. It would be very hard to understand these specific conditions that need to be met for the CVE to be applicable, as well as fixing solutions, which are not necessarily a software upgrade, but also code patches or any deployment or code mitigations.

**The Solution**

This is where JFrog Security CVE Research and Enrichment comes into play. JFrog security research and threat intelligence teams continuously review and analyze CVEs, existing and new ones, to determine if they are likely to be exploited by real-world attackers. Based on the analysis, the research team set a **JFrog Research Severity** score for CVEs, and provides detailed technical information on the specific conditions for the CVE to be applicable, as well as detailed fixing and mitigation options.

CVEs analyzed by the JFrog security research team are determined by the following criteria:

* The number of existing exploits (or creating an exploit is trivial).
* The number of documented real-world attacks.
* The potential impact of the exploitation.
* Having a high CVSS score.

After the deep analysis, CVEs are enriched with the following research information:

* What is the vulnerable function and what is considered as a vulnerable call, that makes the exploitation possible and puts the software artifact at risk?
* What are the cases where the function is disabled or not compiled?
* What are the configurations that make the vulnerability hard to exploit?
* Affected software components and versions.
* Existing patches to fix the vulnerability with or without upgrading the component.
* Deployment or development mitigations to mitigate or eliminate the riskof the vulnerability.
* Which CPU architecture is relevant to the vulnerability if only specific ones are exploitable.

**What should you do with JFrog research enriched CVEs?**

CVEs with the highest JFrog security severity are the most likely to be used by real-world attackers. This means that you should put effort into fixing them as soon as possible. After fixing those CVEs, the risk of the software artifact being exploited by a CVE becomes much lower.

To help you fix the issues, the JFrog security team provides you with detailed fix and mitigation options for the CVEs. In some cases, there are easier and harder ways to fix an issue.

## View JFrog Research Enriched CVEs

You can access the CVE data in **Xray > Scans List**\


<figure><img src="https://jfrog.com/help/api/khub/maps/6nte66fuu2ZQMB2dfriysg/resources/gGL_CN4kX7UHzdYiL8QiiA-6nte66fuu2ZQMB2dfriysg/content?v=df41a2a60eadaa59" alt=""><figcaption></figcaption></figure>

JFrog research enriched CVEs are indicated by an icon in the list.\


<figure><img src="../../../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

Once you click on the CVE, the CVE details are displayed in the right panel. The JFrog research enriched CVE will include the following additional details:

### JFrog Research Severity <a href="#uuid-dc0b29e7-6fa4-48f7-26c0-89dc94c89200_bridgehead-idm4599339924988833995481602854" id="uuid-dc0b29e7-6fa4-48f7-26c0-89dc94c89200_bridgehead-idm4599339924988833995481602854"></a>

The severity given by the JFrog security research team after the manual analysis by the team.

### Remediation <a href="#uuid-dc0b29e7-6fa4-48f7-26c0-89dc94c89200_bridgehead-idm4556731652539233995482266988" id="uuid-dc0b29e7-6fa4-48f7-26c0-89dc94c89200_bridgehead-idm4556731652539233995482266988"></a>

Displays fixed versions for the issue if any, or recommendations such as upgrading and mitigations.

<figure><img src="../../../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

### Research Summary <a href="#uuid-dc0b29e7-6fa4-48f7-26c0-89dc94c89200_bridgehead-idm4516531026246433995482647284" id="uuid-dc0b29e7-6fa4-48f7-26c0-89dc94c89200_bridgehead-idm4516531026246433995482647284"></a>

A summary of the issue in the CVE based on JFrog's security analysis .

<figure><img src="../../../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

### Research Details <a href="#uuid-dc0b29e7-6fa4-48f7-26c0-89dc94c89200_bridgehead-idm4556731672585633995483117023" id="uuid-dc0b29e7-6fa4-48f7-26c0-89dc94c89200_bridgehead-idm4556731672585633995483117023"></a>

A detailed description of the issue that provides more insights on the vulnerability, based on JFrog's security analysis.

<figure><img src="../../../../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

### JFrog Research Severity Reasons <a href="#uuid-dc0b29e7-6fa4-48f7-26c0-89dc94c89200_bridgehead-idm4516527383160033995483484104" id="uuid-dc0b29e7-6fa4-48f7-26c0-89dc94c89200_bridgehead-idm4516527383160033995483484104"></a>

The reasons behind the JFrog research severity.

<figure><img src="../../../../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

\
