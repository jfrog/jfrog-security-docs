# Prevent the Use of Unsecured ML Models

ML models can be a hidden source of security risk—especially when serialized in formats like Pickle (`.pkl`) or sourced from unverified origins. These files can contain malicious code, leak sensitive data, or behave unpredictably in production.

To protect your pipeline, you may define security policies specifically for ML model package types. With these policies, you can:

* **Block risky formats** like Pickle or Dill.
* **Allow only approved model versions**.
* **Automate responses** like alerts, ticket creation, or blocking downloads.

### What to Configure

[Create a policy](../configure-advanced-security/create-advanced-security-policies/ml-model-policy.md) targeting the `ML Model` package type and set rules based on package name (e.g., `*.pkl`) and version.&#x20;

Apply actions such as:

* **Block download or distribution**
* **Generate violations**
* **Trigger webhooks or notifications**

Attach the policy to watches monitoring your key repositories. Once active, Xray will scan for risky or unapproved models and respond automatically.

This approach helps secure your ML supply chain from development through deployment—closing gaps that traditional security tools often miss.
