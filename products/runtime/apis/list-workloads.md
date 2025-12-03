# List Workloads

**Description:** List of Workloads

**Security:** Requires a valid user with a "Read" permission

**Usage:** `POST /runtime/api/v1/workloads`

**Consumes:** `application/json`

**Produces:** `application/json`

**Request Body:**

| Name       | Type      | Required/Optional | Description                                                                              |
| ---------- | --------- | ----------------- | ---------------------------------------------------------------------------------------- |
| `limit`    | int       | optional          | Key-based pagination - number of rows per request. Default: 10                           |
| `next_key` | string    | optional          | Id from the previous request, empty on the first request                                 |
| `order_by` | string    | optional          | Available options: name, cluster,runtime\_status ,vulnerabilties\_count, registry, risks |
| `filters`  | filterObj | optional          | Filter the results by the available filters listed in filter\_object                     |

**filterObj:**

| Name            | Type                       | Required/Optional | Description                                                                                                                                                           |
| --------------- | -------------------------- | ----------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `time_period`   |                            | optional          | <p>Default - now<br>Options: now, 1 hour, 24 hours, 3 days, 7 days, 10 days</p>                                                                                       |
| `cve_id`        | array\[string]             | optional          | CVE identifier                                                                                                                                                        |
| `risk`          | array                      | optional          | malicious, untrusted\_registry, integrity\_violation, critical\_applicable                                                                                            |
| `component`     | Array\[filterComponentObj] |                   | - all components                                                                                                                                                      |
| `applicability` | Array of app\_enum         | optional          | <p>Contextual Analysis result.</p><p>Possible values: not_scanned, applicable,</p><p>not_applicable, undetermined, rescan_required, upgrade_required, not_covered</p> |
| `severity`      | array\[string]             | optional          | <p>Contextual Analysis result.</p><p>Possible values: not_scanned, applicable,</p><p>not_applicable, undetermined, rescan_required, upgrade_required, not_covered</p> |
| `workloads`     | Array\[filterWorkloadObj]  | optional          | If added return data only on workloads that are in the list                                                                                                           |
| `namespace`     | array\[string]             | optional          | Filters the results by namespace. Returns only images that belong to any of the namespaces listed.                                                                    |

**filterComponentObj:**

| Name      | Type   | Required/Optional | Description                                                   |
| --------- | ------ | ----------------- | ------------------------------------------------------------- |
| `name`    | string | required          | Component name                                                |
| `version` | string | optional          | Component version; if not provided, all versions are returned |

**filterWorkloadObj:**

| Name        | Tyoe   | Required/Optional | Description                                                                       |
| ----------- | ------ | ----------------- | --------------------------------------------------------------------------------- |
| `name`      | string | required          |                                                                                   |
| `namespace` | string | optional          | Name of name space; if not provided all matches the other params (name & cluster) |
| `cluster`   | string | optional          | Name of cluster; if not provided all matches the other params (name & namespace)  |

#### Response body <a href="#z3w3i3z4ksgi" id="z3w3i3z4ksgi"></a>

| Name          | Type                 | Description                                                  |
| ------------- | -------------------- | ------------------------------------------------------------ |
| `total_count` | int                  | The total number of images tags that match the filter quarry |
| `pagination`  | paginationObj        | Pagination info for the request                              |
| `workloads`   | Array \[workloadObj] |                                                              |

paginationObj:

| Name       | Type   | Description                                              |
| ---------- | ------ | -------------------------------------------------------- |
| `limit`    | int    | Key-based pagination - number of rows per request        |
| `next_key` | string | Id from the previous request, empty on the first request |

**workloadObj:**

| Name                    | Type                | Description                                                                                                                                                                                               |
| ----------------------- | ------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `name`                  | string              | Workload name                                                                                                                                                                                             |
| `namespace`             | string              |                                                                                                                                                                                                           |
| `cluster`               | string              |                                                                                                                                                                                                           |
| `runtime_status`        | string              | Possible values: running, stopped, unknown                                                                                                                                                                |
| `nodes`                 | Array of string     |                                                                                                                                                                                                           |
| `architecture`          | string              | arch\_names                                                                                                                                                                                               |
| `risks`                 | Array\[ risk\_enum] | <p>Possible values: malicious, untrusted_registry, integrity_violation, critical_applicable_cves</p><p>untrusted_registry, integrity_violation inherent from images and rest aggregation from process</p> |
| `vulnerabilities_count` | int                 | The sum of all vulnerabilities of the process                                                                                                                                                             |
| `processes`             | Array\[processObj]  |                                                                                                                                                                                                           |

**processesObj:**

| Name                 | Type                 | Description                                                                |
| -------------------- | -------------------- | -------------------------------------------------------------------------- |
| `name`               | string               |                                                                            |
| `runtime_status`     | enum                 | running / stopped / unknown                                                |
| `risks`              | Array of risk\_enum  | Malicious/ untrusted\_registry/ integrity\_violation/ critical\_applicable |
| `vulnerabilities`    | Array\[vulnObj]      | An array of the vulnerabilities detected on the process                    |
| `malicious_packages` | Array\[maliciousObj] | An array of malicious packages detected on the image tag                   |
| `arguments`          | string               |                                                                            |
| `path`               | string               | File system path                                                           |
| `process_hash`       | string               | The SHA-256 hash of the process executable file                            |
| `image_digest`       | string               | The SHA-256 digest of the container image the process is running from      |

**vulnObj:**

| Name            | Type                 | Description                                                                                                                                                           |
| --------------- | -------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `cve_id`        | string               | CVE identifier                                                                                                                                                        |
| `xray_id`       | string               | Xray identifier                                                                                                                                                       |
| `severity`      | string               | Severity level of the issue (e.g., "High")                                                                                                                            |
| `cvss_v2`       | string               | CVSS version 2 score                                                                                                                                                  |
| `cvss_v3`       | string               | CVSS version 3 score                                                                                                                                                  |
| `applicability` | string               | <p>Contextual Analysis result.</p><p>Possible values: not_scanned, applicable,</p><p>not_applicable, undetermined, rescan_required, upgrade_required, not_covered</p> |
| `components`    | array\[componentObj] | The components information                                                                                                                                            |

**maliciousObj:**

| Name         | Type                 | Description               |
| ------------ | -------------------- | ------------------------- |
| `xray_id`    | string               | Xray identifier           |
| `components` | array\[componentObj] | The component information |

**componentObj:**

| Name           | Type   | Description                                                                                        |
| -------------- | ------ | -------------------------------------------------------------------------------------------------- |
| `component_id` | string | The component identifier in the Xray format (e.g., "gav://com.thoughtworks.xstream:xstream:1.4.5") |
| `name`         | string | Component name                                                                                     |
| `version`      | string | Component version                                                                                  |

**Response Codes:**

| Status code | Description                               |
| ----------- | ----------------------------------------- |
| 200         | OK                                        |
| 400         | Bad request - Required fields are missing |
| 403         | Permission denied                         |
| 404         | Not found                                 |
| 500         | Internal server error                     |

#### Examples <a href="#a9zq3fyw3mh7" id="a9zq3fyw3mh7"></a>

**Example request**

```json
{
  "limit": 50,
  "last_key": "id123",
  "filters": {
    "severities": [
      "Critical",
      "High"
    ],
    "workloads": [
      {
        "name": "corends",
        "namespace": "jfs-production",
        "cluster": "jfs-production"
      }
    ]
  }
}
```

**Example successful response**

```
{
  "pagination": {
    "total_count": 105,
    "next_key": "87319827319827",
    "limit": 1
  },
  "workloads": [
    {
      "name": "demo-security",
      "namespace": "my-namespace",
      "cluster": "my-cluster",
      "runtime_status": "running",
      "nodes": [
        "10-0-0-1",
        "10-0-0-2"
      ],
      "architecture": "amd64",
      "risks": [
        "critical_applicable_cves"
      ],
      "vulnerabilities_count": 1,
      "processes": [
        {
          "name": "my-process",
          "arguments":"my-process-args",
          "path":"/bin/my-process",
          "runtime_status": "running",
          "risks": [
            "critical_applicable_cves"
          ],
          "vulnerabilities": [
            {
              "cve_id": "CVE-2022-1471",
              "applicability": "applicable",
              "components": [
                {
                  "id": "gav://org.yaml:snakeyaml:1.26",
                  "name": "org.yaml:snakeyaml",
                  "version": "1.26"
                }
              ],
              "cve_id": "CVE-2022-1471",
              "cvss_v2": "",
              "cvss_v3": "9.8",
              "severity": "Critical",
              "xray_id": "<XRAY_ID>"
            }
          ],
          "malicious_packages":[],
          "image_digest":"<image_sha256>",
          "process_hash":"<process_executable_sha256>"
        }
      ]
    }
  ]
}
```

**Example error response:**

```
404 Not Found
{
    "error": "error message"
}
```
