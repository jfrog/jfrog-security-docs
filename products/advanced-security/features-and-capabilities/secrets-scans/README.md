# Secrets Scans

JFrog Advanced Security helps prevent the accidental exposure of secrets such as API keys, passwords, and tokens through its comprehensive secrets detection and token validation capabilities. By scanning both source code and binary artifacts, it ensures sensitive data is never exposed to unauthorized users, making it a powerful secrets prevention solution.

Learn how to create a [Custom Secrets Scanner](custom-secrets-scanner.md)

For developers and security experts, secrets detection is integrated into your IDE, CLI, Frogbot, and the JFrog Platform, providing real-time feedback to identify and address exposed secrets across the development pipeline.

### Supported Secret Types

* **Access Tokens (Keys)**: Detects structured access tokens in both text and binary files, such as API keys, OAuth tokens, and private tokens.&#x20;
  * **Token Validation** (supports public SaaS endpoints only, e.g., `github.com`, `gitlab.com`) enhances secret detection by verifying the validity of detected tokens and distinguishing between active and inactive tokens by authenticating against the token provider.
* **Certificate & Private Key Detection**: Identifies issues in X.509 PEM and DER certificates, including:
  * Certificates containing private keys
  * Expired certificates
  * Self-signed certificates
* **High Entropy Textual Secrets**: Detects high-entropy secrets in source code and config files, such as passwords and secret keys with high randomness.
* **URL Secrets Detection**: Detects embedded credentials in URLs (e.g., `https://username:password@mydomain.com`).

### Token Validation

Enable **Token Validation** to verify the validity of detected tokens, distinguishing between active and inactive tokens by authenticating against the token provider.

* Available through both the **JFrog Platform** and **Xray’s REST API**.
* To enable in the **JFrog Platform**:
  * Navigate to **Administration > Xray Settings > General > Advanced Security**
  * Check the **Enable dynamic token validation** checkbox
* To enable via **REST API**, use the "Enable Token Validation for Secrets" API.

### Validation Results

Once enabled, results appear under **Findings** in violation details. The **Token Validation** column indicates:

* **Active:** Token is valid and poses a security risk if compromised.
* **Inactive:** Token is no longer in use.
* **Unsupported:** Token provider does not support validation.
* **Unavailable:** Unable to validate due to unknown reasons.

Some providers attach metadata to secrets (e.g., AWS includes a **Token ID** with the **Token Secret**). This metadata is displayed in the **Metadata** column.

### Details about Supported Secret Types

#### Access Tokens (Keys)

Detects structured access tokens in text or binary files. **For example**:

<table><thead><tr><th width="374">Platform</th><th>Example Token</th></tr></thead><tbody><tr><td>GitHub</td><td>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</td></tr><tr><td>GitLab</td><td>glpat-cV-J-ZMnAy4Ge6GWqGeX</td></tr><tr><td>npm</td><td>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</td></tr><tr><td>Slack</td><td>xoxp-6654659592213-6680360740176-6657496465043-78439636fa8af05cb14c83a0527a17f5</td></tr></tbody></table>

#### Supported Providers for token validation

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

#### Access Tokens (Keys) Detection False positives Reduction

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

#### High Entropy Textual Secrets Detection False positives Reduction

False positives are minimized using heuristics. Secrets will **not** raise alerts if:

* **Key is exactly "key"** (e.g., `key = d#@B2xN,Y}`)
* **Value matches test patterns** (`.*xxxx.*`, `.*123456.*`, etc.)
* **Value contains repeated/sequential characters** (e.g., `123456`)
* **Secret is in documentation directories**
* **Secret is in third-party files** (e.g., a third-party npm package)

### URL Secrets Detection

Detects secrets embedded in URLs (e.g., `https://myuser:mypass@somedomain.com`).

#### URL Secrets Detection False positives Reduction

Some URLs will not trigger alerts:

* **URLs matching test patterns:** `.*example.*`, `.*foo.*`, `.*bar.*`
* **Authentication parts with common placeholders:** `.*user:pass.*`, `.*username.*`, `.*anonymous.*`
* **URLs referencing image files** (e.g., `.jpg`)
