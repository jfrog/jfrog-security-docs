# Configure Curation for Self Hosted

### Configure Curation for Self Hosted <a href="#uuid-85e52c1f-4cff-e905-384d-2c78ad3f0085" id="uuid-85e52c1f-4cff-e905-384d-2c78ad3f0085"></a>

The following steps will help you validate if your self hosted JFrog Platform is correctly configured and ready with the JFrog Curation service.

In case it is not ready the below document will help you configure your JFrog platform and have the  JFrog Curation service ready.

|                                                                           | Note |
| ------------------------------------------------------------------------- | ---- |
| JFrog Curation in SaaS is automatically deployed and configured by JFrog. |      |

JFrog Curation is installed as part of the Xray installation. There are no additional Curation installation steps needed. This document assumes you have a running JFrog Platform instance with Xray service installed and running, where you wish to enable Curation service on.

|                                                                       | Note |
| --------------------------------------------------------------------- | ---- |
| In the case of an Xray cluster apply the steps for each cluster node. |      |

#### Validate your Curation Readiness <a href="#bridgehead-idm4648426719136034000966786087" id="bridgehead-idm4648426719136034000966786087"></a>

Starting in Xray version 3.86.x we have added a dedicated Curation health check page which will help you see the aspects working as needed or missing for your Curation service to run.

Use this URL to see your Curation health state:

[https://your.domain/xray/ui/curation/internal/health](https://your.domain/xray/ui/curation/internal/health)

Indications you will see:

*   JFConnect service health

    To troubleshoot see: Troubleshooting jfconnect micro service JFConnect service is up and running
*   Curation entitlements health

    To troubleshoot see: Ensure your JFrog Platform instance is entitled for Curation
*   Central Catalog service availability&#x20;

    To troubleshoot see: Configuring JFrog Catalog Central for the First Time

If everything works you could skip the below sections. Your Curation service is ready to go. Otherwise please follow the below sections to add the needed configuration.

#### Pre-configuration Requirements <a href="#bridgehead-idm4524929761630433995544389135" id="bridgehead-idm4524929761630433995544389135"></a>

**JFrog Curation service compatibility**

JFrog Curation is currently available for the following JFrog subscriptions:

* Enterprise X
* Enterprise +

**Ensure Xray minimal version with Curation is in use**

The Xray version (that includes Curation) is:

* Without a proxy: 3.78.2
* Behind a proxy: 3.82.11

It is highly recommended to use the latest version of Xray to ensure the latest Curation version is in use. To get the available official Xray versions please refer to

To get your Xray version in use please go to https://your\_env\_domain/**xray/api/v1/system/version**

Example of a valid result:

```
{
   "xray_version":"3.82.6",
    "xray_revision":"38d6f6d"
}
```

**Ensure Artifactory minimal version that supports Curation is in use**

Make sure the minimal Artifactory version in use is: 7.63.5

To get your JFrog platform version in use please go to this URL:How to know which JFrog platform version is in use: https://domain/artifactory/api/system/version

Example of a valid result:&#x20;

```
{
    "version" : "7.69.1",
    "revision" : "76901900",
    …..
   }
```

**Configuring JFrog Catalog Central for the First Time**

This section assumes JFrog Catalog Central service was not yet configured in your JFrog Platform instance.

The below configurations should be done in the Xray system.yaml (usually under $JFROG\_HOME/xray/var/etc).  In this configuration step you will be asked to use the Catalog credentials asked at the previous section.

```
catalog:
  enabled: true
  central:
    enabled: true
    url: https://jfrogxraycatalog.jfrog.io/xray
    username: <USERNAME>
    password: <PASSWORD>
```

1. Save the Xray system.yaml file
2. Restart the Xray service
3. Verify the JFrog Catalog Central is working as expected(Available only in Xray version 3.86.x or later) in URL:https://domain/xray/ui/curation/internal/health.
4. Whitelist the following services in the firewall
   * `jes.jfrog.io` JFrog license service
   * `jcs.jfrog.io` JFrog license service
   * `https://Jfrogxraycatalog.jfrog.io` JFrog Catalog service

**Have the needed JFrog Catalog Central service credentials at hand**

JFrog Curation is using the JFrog Catalog Central service as a critical component for its package blocking assessment. To be able to communicate with the JFrog Catalog Central service the JFrog platform admin should have a username and password for the instance to be able to communicate with it.

If you do not have these credentials at hand please, contact your JFrog sales representative.

**Ensure your JFrog Platform instance is entitled for Curation**

Perform the following steps to check that Curation is available in your JFrog Platform environment:

1.  Call https://your.domain/ui/api/v1/jfconnect/entitlements

    Expected result is an array with entitlements including the Curation one
2.  To look for the Curation entitlements section in the returned information please search for ‘Curation’ in the response:

    Example:

    ```
    {
          "name": "curation",
          "value": 1,
          "expiryDate": "2026-07-20T00:00:00.000Z",
          "productExpiryDate": "2026-07-20T00:00:00.000Z",
          "isTrial": true,
          "customerId": "",
          "blockingQuantity": 1,
          "dependentOnAction": ""
        }
    ```

If you got an empty result please refer to:troubleshooting jfconnect micro service section.

If you got the entitlement information but you are lacking the Curation one in the returned data, it probably means you were not assigned the needed Curation entitlement by JFrog. Please contact your JFrog sales representative or JFrog support

**Troubleshooting jfconnect micro service JFConnect service is up and running**

JFConnect microservice acts as the JPD (JFrog Deployment) entitlements service and enables dynamic entitlement allocation for the connected products, based on account/subscription changes in JFrog’s main entitlements server.

For more information on the service, see JFConnect Microservice.

1.  Make sure jfconnect is enabled in your JFrog platform system.yaml setting file.

    Allocate JFConnect in JFrog platform system.yaml, at the global level and make sure it is enabled:

    ```
    jfconnect:
      enabled: true
    ```
2.  If you run behind a proxy add jfconnect proxy settings. Make sure the below additional settings are in place:

    ```
    jfconnect: enabled: true
    env:
      http_proxy: "http://yourproxyaddress/"
      https_proxy: "http://yourproxyaddress"
      no_proxy: "localhost,127.0.0.1"
    ```
3. Restart your JFrog system and re check if jfconnect is running as expected now. To Verify that JFConnect micro service is running as expected please follow the below step
   1.  Call: https://your.domain//ui/api/v1/jfconnect/entitlements

       Expected result is an array with entitlements information (not an empty result)

       Expected result: An not empty array of entitlements "entitlements":\[{......},{.....}]
4.  If you didn’t get the expected results please refer to the jfconnect help center page for more information.

    If the array is empty, it indicates that JFConnect is not running as expected.

    In case the service is not running as expected please contact your JFrog technical support representative

#### Curation Health-Check Endpoint <a href="#bridgehead-idm4582704491404834049508728909" id="bridgehead-idm4582704491404834049508728909"></a>

This endpoint checks the availability of all components that Curation integrates with and which Curation cannot be started without:

* **JF Connect** : Checks the JFConnect health-check endpoint.
* **Entitlement** : Checks that Curation is entitled, and the entitlement process is working.
* **Catalog** : Checks that Catalog is up and the Curation service can connect catalog

Run the following command:

```
curl -u<username>:<password> https://yourdomain.ext/xray/ui/curation/internal/health 
```

Expected responses:

Error message

```
{
  "JFConnect": "JFConnect is disabled!" OR "JFConnect ping has failed!",
  "Entitlements": "Curation is not entitled!",
  "Catalog": "Catalog is not accessible"
}
```

Curation ready status

```
{
  "JFConnect": "OK",
  "Entitlements": "OK",
  "Catalog": "OK"
}
```
