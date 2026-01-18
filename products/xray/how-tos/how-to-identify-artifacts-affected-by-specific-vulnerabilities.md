# How to Identify Artifacts Affected by Specific Vulnerabilities

## Via UI

**Accessing Impact Search**

1. Navigate to **Xray** > **Scans**.
2. Open the **Impact Search** drawer.
3. Enter your search criteria and run the query.

**Search options**

You can search using one or more of the following parameters:

* **CVE ID** – Locate all resources affected by a specific vulnerability (for example, `CVE-2021-22946` or `XRAY-12345`).
* **Package Name** – Identify all artifacts containing a specific dependency (for example, `lodash`).
* **Package Type** – Filter results by ecosystem, such as `npm`, `maven`, or `pypi`.
* **Package Version** – Narrow results to a specific version of a component.

{% hint style="info" %}
**Note:** When searching by package, **both Package Name and Package Type are required** to avoid ambiguity across ecosystems where the same package name may exist.
{% endhint %}

**Search syntax**

Impact Search uses structured key-value queries, for example:

```json
"CVE ID": "CVE-2021-44228"
```

You can combine multiple conditions using `AND`:

```json
"Package Name": "log4j" AND "Package Type": "maven"
```

**Understanding the results**

Impact Search returns a table of **Affected Resources**, including:

* Resource name (with a direct link to the scanned artifact)
* Repository location
* Component details
* Last scan date
* Artifact path

## Via API

Impact Search is backed by the **Impacted Resources REST API**:

```json
/xray/ui/search/impactedResources
```
