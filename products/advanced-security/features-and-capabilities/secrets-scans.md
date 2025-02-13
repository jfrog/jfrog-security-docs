# Secrets Scans

JFrog **Secrets Scans** provide comprehensive protection against exposed credentials, supporting a wide range of platforms, tools, and secret types. It detects exposed secrets in artifacts stored in **Artifactory**, preventing accidental leaks of internal tokens or credentials.

## Supported Scenarios

Secrets detection currently supports the following environments:

### JFrog Platform

* **Package Types:** Docker, Maven, npm, PyPI, NuGet, Gradle, RPM, Debian, Alpine, Go, RubyGems, Generic
* **Scan Targets:** Both binaries and text files

## Supported Secret Types

### Access Tokens (Keys)

Detects structured access tokens in text or binary files. For example:

| Platform | Example Token                                                               |
| -------- | --------------------------------------------------------------------------- |
| AWS      | `AKIAIOSFODNN7EXAMPLE`                                                      |
| GitHub   | `gho_16C7e42F292c6912E7710c838347Ae178B4a`                                  |
| GitLab   | `gplat-234hcand9q289rba89dghqa892agbd89arg2854`                             |
| npm      | `npm_1234567890abcdefgh`                                                    |
| Slack    | `xoxp-123234234235-123234234235-123234234235-adedce74748c3844747aed48499bb` |

### **Token Validation**

Enable **Token Validation** to verify the validity of detected tokens, distinguishing between active and inactive tokens by authenticating against the token provider.

* Available through both the **JFrog Platform** and **Xray’s REST API**.
* To enable in the **JFrog Platform**:
  * Navigate to **Administration > Xray Settings > General > Advanced Security**
  * Check the **Enable dynamic token validation** checkbox
* To enable via **REST API**, use the "Enable Token Validation for Secrets" API.

### **Validation Results**

Once enabled, results appear under **Findings** in violation details. The **Token Validation** column indicates:

* **Active:** Token is valid and poses a security risk if compromised.
* **Inactive:** Token is no longer in use.
* **Unsupported:** Token provider does not support validation.
* **Unavailable:** Unable to validate due to unknown reasons.

Some providers attach metadata to secrets (e.g., AWS includes a **Token ID** with the **Token Secret**). This metadata is displayed in the **Metadata** column.

#### Supported Providers

Below are supported providers and whether they support **Token Validation**:

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

#### Detection Exceptions

Some access keys will not trigger alerts:

* **Public example keys** (e.g., AWS example: `ANPAI65L554VRJ33ECQS6`)
* **Keys in documentation directories** (e.g., `/usr/local/share/`)
* **Keys matching common test patterns:**
  * `.*xxxx.*`, `.*test.*`, `.*sample.*`, `.*example.*`
  * `.*token.*`, `.*123456.*`, `.*abcdef.*`, `.*foobar.*`

### Certificate & Private Key Detection

Detects issues in **X.509 PEM (text) and DER (binary) certificates**, including:

* Certificates **containing private keys**
* **Expired certificates**
* **Self-signed certificates**

### High Entropy Textual Secrets

Detects identifies high-entropy secrets in textual files (e.g., source code, config files) when:

* The **key** is indicative of a secret (e.g., `password`, `secret`)
* The **value** has high randomness (e.g., `d#@B2xN,Y}`, not `123123123`)

**Example:**

```yaml
my_password: "CorrectHorseBatteryStaple123!"
```

### Detection Exceptions

False positives are minimized using heuristics. Secrets will **not** raise alerts if:

* **Key is exactly "key"** (e.g., `key = d#@B2xN,Y}`)
* **Value matches test patterns** (`.*xxxx.*`, `.*123456.*`, etc.)
* **Value contains repeated/sequential characters** (e.g., `123456`)
* **Secret is in documentation directories**
* **Secret is in third-party files** (e.g., a third-party npm package)

### URL Secrets Detection

Detects secrets embedded in URLs (e.g., `https://myuser:mypass@somedomain.com`).

#### Detection Exceptions

Some URLs will not trigger alerts:

* **URLs matching test patterns:** `.*example.*`, `.*foo.*`, `.*bar.*`
* **Authentication parts with common placeholders:** `.*user:pass.*`, `.*username.*`, `.*anonymous.*`
* **URLs referencing image files** (e.g., `.jpg`)

## Developer Tools

### IDEs

Only text files are scanned.

### Command-Line Interface (CLI)

Different commands scan different file types:

* `jf audit` scans source code for secrets in text files
* `jf docker scan` scans both binary and text files

### Git (Frogbot)

Only text files are scanned.
