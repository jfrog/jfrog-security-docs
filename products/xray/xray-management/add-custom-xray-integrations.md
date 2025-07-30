---
hidden: true
---

# Add Custom Xray Integrations

Xray integrations are configured in the **Administration** module in the **Integrations** page and displays the integrations you have configured and connected to.

### Build the Integration Endpoints for Xray Integrations

In order to enable your custom integration, you need to build and run two REST endpoints, as follows:

**Check Authentication**

Request an indication to whether a provided api key is valid. This API should be exposed by the feed provider.

Request header

apiKey: “some-api-key-which-is-unique-for-a-specific-customer”

GET /api/checkauth

**Valid API Key Response Example (Status code: 200)**

```
{
    "valid": true,
    "error": ""
}
```

**Invalid API Key Response Example (Status code : 401)**

```
{
    "valid": false,
    "error": "User api key is invalid"
}
```

**Request for Components Information**

This API will allow Xray to request for information about one or more components, each identified by a unique component id, from the feed provider. The API will be implemented by the feed provider.

**Request**

The request payload will contain unique identifiers of the components Xray would like to get information about.

In addition Xray will provide a context to the request, this can be a project id or another identifier. If the 3rd party service allows its users to define policies per project, this will allow to answer the request in the context of those policies. For example, if the 3rd party service allows creating policies for OSS license compliance per project, Xray may get a response with a license vulnerability if the queried component is violating the policy.

POST /api/componentinfo

**Request header**

**Request payload**

```
apiKey: "some-api-key-which-is-unique-for-a-specific-customer"
{
    "components": [
        {
            "component_id": "gav://ant:ant:1.6.5",
            "blobs": [
                "97282a3b066de4ee4c9409979737f3911f95ceab"
            ]
        }
    ],
    "context": "project_id"
}
```

**Response**

**The response will contain a list of security vulnerabilities or other issues**

```
{
    "components": [
        {
            "component_id": "gav://ant:ant:1.6.5",
            "licenses": [
                "Apache 2.0"
            ],
            "provider": "the feed provider",
            "vulnerabilities": [
                {
                    "cve": "CVE-2012-2098",
                    "type": "security",
                    "source_id": "unique id of the reported issue",
                    "summary": "Algorithmic complexity vulnerability",
                    "description": "Algorithmic complexity vulnerability in the sorting algorithms in bzip2 compressing stream",
                    "cvss_v2": "7.9",
                    "url": "http://more.info",
                    "publish_date": "2015-11-03T07:30:51.991+00:00",
                    "references": [
                        "http://archives.neohapsis.com/archives/bugtraq/2012-05/0130.html"
                    ]
                }
            ]
        }
    ]
}
```

### **Configure the Integration Endpoints for Xray Integrations**

To configure your endpoints, go to the **Administration** module in the **Xray | Integrations** page and click **New Integration**.

To add and connect to a custom provider, set the **Enabled** checkbox and enter the following parameters:

* The **Integration Vendor** name
* A **Description** for the vendor
* The **API Key** you received from the provider
*   The **URL** Xray uses to check if a component it is scanning is registered with the provider.

    The URL should lead to the **request for components information** REST endpoint
*   The **Test URL** you can use to test your API key with the provider using the "_Test_" button.

    The Test URL should lead to the **Check Authentication** REST endpoint
* The **URL to an icon** you can optionally display for the vendor

\
