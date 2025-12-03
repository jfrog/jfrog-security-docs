# Certificate Verification

## Bypassing Certificate Verification (Optional)

{% hint style="info" %}
Carefully assess this option for production environments.
{% endhint %}

If using a self-signed certificate, modify the installation snippet:

```
--set tlsInsecureSkipVerify=true
```
