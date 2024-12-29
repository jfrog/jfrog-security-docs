# JFrog Advanced Security

### JFrog Advanced Security <a href="#uuid-68bf1ec7-16fe-4a88-dbe0-a860e26711a0" id="uuid-68bf1ec7-16fe-4a88-dbe0-a860e26711a0"></a>

| ![\[Note\]](../.gitbook/assets/note.png)                                                                           | ![Doc.svg](<../.gitbook/assets/uuid 8ae7a916 aa8d e6fc 31e6 90271590f307.svg>)Subscription Information |
| ------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------ |
| This feature is supported with the **Enterprise X** or **Enterprise+** license, with the Advanced Security Add-on. |                                                                                                        |

JFrog Security Advanced Security (JAS) is based on deep security research by JFrog's Security Research team that delivers extended insights into security issues, their impact on your software, and advice on how to remediate them. It helps sharpen developers with prioritized, contextual remediation advice that identifies what matters most to ensure you’re protected. JFrog Xray previously released a powerful capability, the JFrog Security CVE Research and Enrichment feature, that helps you with enhanced analysis on CVE findings in a way that allows you to focus on the most important issues with the capability of finding the best resources invested in fixing them.&#x20;

To learn more about what our research team is up to, see [https://research.jfrog.com/](https://research.jfrog.com/).

**How does JAS help you?**

When Xray scans your packages, it can potentially find thousands of vulnerabilities. Thus, developers will have to sift through these long lists of vulnerabilities to identify their relevance and in some cases, it can be hard to pinpoint where to start, as many of these vulnerabilities may not affect your artifacts. This process is erroneous and time-consuming.&#x20;

In addition, when it comes to non-code-related security issues, they are often overlooked in an organization as a potential security threat, since they are the smallest and easiest issues to fix. This leaves your software potentially exposed to security threats due to security malpractices (e.g., missing authentication), insecure configurations (e.g., excessive privileges), weak authentication, and so on. &#x20;

JAS helps you solve these issues with the capabilities it offers:

* [Vulnerability Contextual Analysis](https://about/document/preview/552327#UUID-fe348cca-cbb2-4e32-b87f-ecf6754ab2d5): Understand the applicability of CVEs in your application and reduce false positives and vulnerability noise with smart CVE analysis.&#x20;
* [Exposures](https://about/document/preview/551969#UUID-a0bf61fb-873e-f10d-b1b1-3bb8cf92cf16): Detect potential security issues in your configurations and the usage of open-source libraries in your code with end-to-end supply chain security to cover different forms of software supply chain attacks.
* [SAST](https://docs.jfrog-applications.jfrog.io/jfrog-security-features/sast): Hunt, fix, and learn about security issues in your code. JFrog SAST scans mainly for specific sensitive operations (DB queries, OS commands, outgoing connection destinations, etc) that can be controlled by an external attacker without proper sanitation injections.

The JFrog Research team provides prioritized, contextual remediation advice identifying what CVEs matter most and enhanced CVE data for developer-friendly step-by-step remediation.

| ![\[Tip\]](../.gitbook/assets/tip.png)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | Tip |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --- |
| <p>JFrog Research Request</p><p>The JFrog Security Research team continuously identifies CVEs that are a priority and provides advanced security information for each. JFrog Security is also giving you the opportunity to request advanced security data for CVEs that you would like more details about. Use our JFrog Research Request feature to request enriched CVE and Contextual Analysis data.</p><p><img src="../.gitbook/assets/uuid 9a9a955f 791d cb9c e004 25cce68ce42a.png" alt="JFrog_Research_Request.png" data-size="original"></p> |     |

#### Get Started <a href="#bridgehead-idm4599339899182433995535505698" id="bridgehead-idm4599339899182433995535505698"></a>

**New to Xray?**&#x20;

Read our [docs](https://about/document/preview/360459#UUID-bd6f9908-7b9b-b0a7-e051-b93cfed7cedf) to learn more about what Xray offers and how to get started with Xray.

**Trial Version**

JAS is available in JFrog’s Trial version for Cloud and Self Hosted, if you would like to try it out in your existing environment contact our support team and request a trial.&#x20;

**Cloud**

Request JAS to be enabled by your Administrator.

**Self-Hosted**

JAS requires an Xray version 3.67.x and above. Follow the instructions here depending on your installation requirements.

**JFrog Security in your IDE**

**Supported IDEs**: Click the link for instructions on installing and using the extension in your relevant IDE.&#x20;

* [Visual Studio Code](https://github.com/jfrog/jfrog-idea-plugin/blob/787b2aea81cc47d4b3e92f6b9be172499ba341e7/README.md)
* [IntelliJ](https://github.com/jfrog/jfrog-idea-plugin)
