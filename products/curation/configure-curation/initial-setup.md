# Initial Setup

Before using JFrog Curation, ensure the system meets the following requirements:

1. **Validate Compatibility**:
   * Ensure the minimum versions of JFrog components are in use:
     * Xray: `3.78.2` (or `3.82.11` for proxy setups).
     * Artifactory: `7.63.5`.
   *   Use the following API to verify your Xray version:

       ```ruby
       rubyCopyEditcurl -u<username>:<password> https://<domain>/xray/api/v1/system/version
       ```
   *   Use this API to check the Artifactory version:

       ```ruby
       rubyCopyEditcurl -u<username>:<password> https://<domain>/artifactory/api/system/version
       ```
2. **Enable JFConnect Microservice**:
   * Open the `system.yaml` configuration file located at `$JFROG_HOME/xray/var/etc`.
   *   Add the following settings:

       ```yaml
       yamlCopyEditjfconnect:
         enabled: true
       ```
   *   If operating behind a proxy, include these proxy settings:

       ```yaml
       yamlCopyEditenv:
         http_proxy: "http://<proxy_address>"
         https_proxy: "http://<proxy_address>"
         no_proxy: "localhost,127.0.0.1"
       ```
   * Restart the JFrog Platform for changes to take effect.
3. **Validate JFConnect and Entitlements**:
   *   Call the entitlement endpoint to check for Curation availability:

       ```ruby
       rubyCopyEditcurl -u<username>:<password> https://<domain>/ui/api/v1/jfconnect/entitlements
       ```
   * Confirm that the response includes `"name": "curation"`. If not, contact JFrog support.
