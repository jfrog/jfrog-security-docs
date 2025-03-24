# Trust Self Signed Certificates en

### Trust Self-Signed Certificates

When an Xray instance/node is configured to go through an **SSL proxy** that uses a **self-signed certificate**, you may encounter the following issue when performing tasks such as an [online database sync](https://about/document/preview/637838#UUID-34d31c76-0926-2715-c8aa-e25b0882dfaa):

2021-07-20T14:47:47.500Z \[33m\[jfxr ]\[0m \[1m\[31m\[ERROR]\[0m \[c080f44e606d159 ] \[samplers:91 ] \[main ] Failed to read response from jxrayUrl. Error: Get "https://jxray.jfrog.io/api/v1/system/ping": x509: certificate signed by unknown authority

1. To overcome this issue, you will need to import the **Proxy certificate** into **each** Xray instance/pod by placing it under the following path within the Xray machine/container/pods:/etc/ssl/certs/.
2. Next, you will need to restart Xray.

* The path shown above is the default directory used by Go applications (such as Xray) when importing SSL certificates.
