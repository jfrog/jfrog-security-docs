# Advanced Security Reports

Advanced Security Reports allows you to generate an aggregated view of Exposures findings and results.

### Exposures Report

The Exposures report identifies where components in your **code and binaries** are actively invoked, allowing you to focus on real, exploitable risks, not just theoretical vulnerabilities. By detecting actual usage paths of vulnerable functions and insecure libraries, it helps you prioritize the exposures that pose the greatest threat to your applications.

Unlike static vulnerability listings, this report shows where an exposure occurs in the context of your software’s execution, enabling more informed decisions about remediation. It includes severity ratings, impacted components, and evidence of invocation across your artifacts, builds, and release bundles.

Read more about [Reports](../../xray/features-and-capabilities/reports.md) in the JFrog Security platform.

The following REST APIs support Advanced Security Reports:

* [Generate Exposures Report](https://jfrog.com/help/r/xray-rest-apis/generate-exposures-report)
* [Get Exposures Report Content](https://jfrog.com/help/r/xray-rest-apis/get-exposures-report-content?tocId=67CfJez5W9FKYlQK9gLMNQ)
* [Export](https://jfrog.com/help/r/xray-rest-apis/export)
* [Delete](https://jfrog.com/help/r/xray-rest-apis/delete)
* [Abort](https://jfrog.com/help/r/xray-rest-apis/abort)
