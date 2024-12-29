# Secrets Scans

#### Secrets Scans <a href="#uuid-f780f7a6-4776-ff09-3ef1-b60e8908dd36" id="uuid-f780f7a6-4776-ff09-3ef1-b60e8908dd36"></a>

Detects any secret left exposed in the artifacts stored in Artifactory to stop any accidental leak of internal tokens or credentials. Xray scans your configuration, text, and binary files for plaintext credentials, private keys, tokens, and similar secrets. Xray uses a constantly updated list of more than 150 specific types of credentials. In addition, Xray uses a proprietary generic secrets matcher, for the best coverage possible. Xray also scans for issues in the certificates used in the software, such as expired or weak certificates.

**Supported Scenarios**

JFrog Secret detection currently supports the following scenarios:

* JFrog Platform: Docker, Maven, npm, PyPI, NuGet, Gradle and Generic. Additional supported Package types are coming soon.
* Developer tools: [IDE](https://docs.jfrog-applications.jfrog.io/jfrog-applications/ide), [CLI](https://docs.jfrog-applications.jfrog.io/jfrog-applications/jfrog-cli/cli-for-jfrog-security), [Git (Frogbot)](https://docs.jfrog-applications.jfrog.io/jfrog-applications/frogbot).

|                                                                                                                                                                                                                                                                                                                                                       | Note |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---- |
| <p>In the JFrog Platform both binaries and text files are being scanned for secrets.</p><p>In the IDE and Frogbot only text files are scanned.</p><p>In the CLI there are commands such as ‘jf audit’ that scan source code and look for secrets in text files, and other commands such as ‘jf docker scan’ that scan both binary and text files.</p> |      |

**Supported Secrets Types**

JFrog Secrets detection can detect the following types of secrets:

* [Access tokens (keys)](about:blank/UUID-f780f7a6-4776-ff09-3ef1-b60e8908dd36.html#UUID-f780f7a6-4776-ff09-3ef1-b60e8908dd36_N1722188830347)
* [Certificates/private keys](about:blank/UUID-f780f7a6-4776-ff09-3ef1-b60e8908dd36.html#UUID-f780f7a6-4776-ff09-3ef1-b60e8908dd36_N1722188840357)
* [High entropy secrets](about:blank/UUID-f780f7a6-4776-ff09-3ef1-b60e8908dd36.html#UUID-f780f7a6-4776-ff09-3ef1-b60e8908dd36_N1722188849592)
* [URL secrets](about:blank/UUID-f780f7a6-4776-ff09-3ef1-b60e8908dd36.html#UUID-f780f7a6-4776-ff09-3ef1-b60e8908dd36_N1722188859111)

**Access Tokens**

This scanner detects access tokens with a well-defined structure, in either text or binary files. For example:

| Platform | Example Token                                                               |
| -------- | --------------------------------------------------------------------------- |
| AWS      | `AKIAIOSFODNN7EXAMPLE`                                                      |
| GitHub   | `gho_16C7e42F292c6912E7710c838347Ae178B4a`                                  |
| GitLab   | `gplat-234hcand9q289rba89dghqa892agbd89arg2854`                             |
| npm      | `npm_1234567890abcdefgh`                                                    |
| Slack    | `xoxp-123234234235-123234234235-123234234235-adedce74748c3844747aed48499bb` |

**Token Validation**

Verify the validity of detected tokens by enabling Token Validation. This feature allows you to distinguish between active and inactive tokens by authenticating against the token provider.

The Dynamic Token Validation feature can be enabled both through the JFrog Platform and through Xray’s REST API.

To enable this feature from the JFrog Platform navigate to **Administration > Xray Settings > General > Advanced Security** and check the **Enable dynamic token validation** checkbox.

![Screenshot\_2024-12-10\_at\_12\_47\_26.png](<../../.gitbook/assets/uuid f9429f9e 278f 13c9 3fe2 73fa4f68eb31.png>)

To enable through REST API, run the following REST API: [Enable Token Validation for Secrets](https://about/document/preview/733722#UUID-8dd54c7b-d9d2-8dda-8894-d468d91e6007).

Once enabled, the results are presented in the violation's details under the **Findings** tab. To learn more about results, see View Exposure Scan Statuses and Results.

![TokenValidation.png](<../../.gitbook/assets/uuid d4e470bf 03d4 7d6d 3680 8d0db4152e35.png>)

The **Token Validation** column statuses are:

* **Active**: Token is valid and usable. It poses a potentially higher security risk if compromised.
* **Inactive**: Token is inactive. For tokens associated with Self Hosted providers, our validation cannot determine their activity status.
* **Unsupported**: Token provider is currently unsupported for validation.
* **Unavailable**: Cannot validate due to unknown reasons.

The **Metadata** column:

For several providers, additional identification is coupled to the secret token (AWS has a Token ID associated with the Token Secret). Our scanners detect this additional identification and output it to the Metadata column.

**Supported Providers**

These are all the providers currently supported by this scanner. Some providers also support JFrog’s Token Validation.

| Supported Provider  | Token Validation Support |
| ------------------- | ------------------------ |
| Adobe               | Yes                      |
| Age File Encryption | No                       |
| Alibaba             | Yes                      |
| Artifactory         | No                       |
| AWS                 | Yes                      |
| Azure               | Yes                      |
| Clojars             | No                       |
| Cloudflare          | No                       |
| Contentful          | Yes                      |
| Databricks          | No                       |
| DigitalOcean        | Yes                      |
| Doppler             | Yes                      |
| Dropbox             | Yes                      |
| Duffel              | Yes                      |
| Dynatrace           | No                       |
| Elastic             | No                       |
| Fastly              | Yes                      |
| Finicity            | No                       |
| Flutterwave         | Yes                      |
| GitHub              | Yes                      |
| GitLab              | Yes                      |
| Google              | Yes                      |
| Heroku              | Yes                      |
| Hubspot             | No                       |
| Intercom            | No                       |
| Jenkins             | No                       |
| Linear              | Yes                      |
| Mailchimp           | Yes                      |
| Mailgun             | Yes                      |
| Mapbox              | Yes                      |
| Messagebird         | No                       |
| New Relic           | No                       |
| npm                 | Yes                      |
| NuGet               | No                       |
| Okta                | No                       |
| PayPal              | Yes                      |
| Planetscale         | No                       |
| Postman             | Yes                      |
| Postmark            | Yes                      |
| Pulumi              | Yes                      |
| PyPI                | No                       |
| Rubygems            | Yes                      |
| Sauce               | No                       |
| Searchgaurd         | No                       |
| Sendgrid            | Yes                      |
| Sendinblue          | Yes                      |
| Sentry              | No                       |
| Shippo              | Yes                      |
| Shodan              | Yes                      |
| Shopify             | No                       |
| Slack               | Yes                      |
| Snyk                | Yes                      |
| Sonar               | No                       |
| Square              | No                       |
| StackHawk           | Yes                      |
| Stripe              | Yes                      |
| Telegram            | Yes                      |
| Terraform           | Yes                      |
| Travis CI           | No                       |
| Trello              | No                       |
| Twilio              | Yes                      |
| Typeform            | Yes                      |
| Ubidots             | Yes                      |

**Detection Exceptions**

The following access keys will not raise an alert by the scanners

* Public example keys (AWS example -  ANPAI65L554VRJ33ECQS6)
* Keys in files residing in documentation directories (ex. "/usr/local/share/")
* Keys that match any of the following case-insensitive patterns
  * .\*xxxx.\*
  * .\*test.\*
  * .\*sample.\*
  * .\*example.\*
  * .\*token.\*
  * \*123456.\*
  * .\*abcdef.\*
  * .\*foobar.\*
  * .\*deadbeef.\*
  * .\*xxxxxx.\*
  * .\*1111111.\*
  * .\*0000000.\*

**Certificates/Private keys**

JFrog Secret detection can detect issues in X.509 PEM (textual) and DER (binary) certificates and private keys :

* Certificates containing private keys or standalone PEM/DER private keys
* Expired certificates
* Self-signed certificates

**High Entropy Textual Secrets**

JFrog Secret detection can detect secrets in the general form of  “key = value” in textual files (incl. source files and configuration files) where:

* “key” is a variable name indicative of a secret (for example “secret” or “password”)
* “value” is a string with high entropy/randomness (ex. “d#@B2xN,Y}” and not “123123123”)

For example:

```
my_password: "CorrectHorseBatteryStaple123!"
```

**Detection exceptions**

JFrog employs several heuristics to avoid false positive results. The following textual secrets will not raise an alert by the scanners:

* The key completely matches the string “key” (ex. “key = d#@B2xN,Y}”)
* The value matches any of the following case-insensitive patterns
  * .\*xxxx.\*
  * .\*test.\*
  * .\*sample.\*
  * .\*example.\*
  * .\*123456.\*
  * .\*abcdef.\*
  * AKIA.\*
* The value contains a 6-character long sequence of the same character or consecutive characters (ex. “123456”)
* Secrets in files residing in documentation directories (ex. "/usr/local/share/")
* Secrets in 3rd-party files (ex. A file belonging to a 3rd-party npm package)
* Secrets in files where the file path matches any of the following case-insensitive patterns
  * .\*example.\*
  * .\*sample.\*

**URL Secrets**

JFrog Secret detection can detect secrets in textual files where the secret is embedded in a URL (for example; https://myuser:mypass@somedomain.com)

**Detection exceptions**

The following URLs will not raise an alert by the scanners:

* URLs that match any of the following case-insensitive patterns
  * .\*example.\*
  * .\*foo.\*
  * .\*bar.\*
  * .\*example.\*
  * .\*sample.\*
  * .\*some.host.\*
  * .\*some.url.\*
  * .\*site.com.\*
  * .\*google.com.\*
  * .\*url.com.\*
  * .\*xyz.\*
  * .\*abc.\*
  * .\*domain.com.\*
  * .\*host.com.\*
  * .\*host.page.\*
  * .\*codecov.\*
  * .\*deepsource.\*
  * .\*shields.io.\*
* URLs where the authentication part matches any of the following case-insensitive patterns
  * .\*user:pass.\*
  * .\*username.\*
  * .\*anonymous.\*
  * .\*test.\*
  * .\*foo.\*
  * .\*bar.\*
  * .\*example.\*
  * .\*myuser.\*
  * .\*baz.\*
* URLs that reference an image file (ex. URL ends with “.jpg”)
