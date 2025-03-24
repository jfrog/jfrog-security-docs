# List Image Tags

**Description:** Lists all image tags according to specified filters\
**Note**: The API returns vulnerabilities only if the image comes from a trusted registry. Filters by CVE and by components will only return images from trusted registries.\
**Security:** Requires a valid user with a "Read" permission\
**Usage:** POST `/runtime/api/v1/images/tags`\
**Consumes:** `application/json`\
**Produces:** `application/json`

#### Request body

| Name       | Type      | Required/Optional | Description                                                          |
| ---------- | --------- | ----------------- | -------------------------------------------------------------------- |
| `limit`    | int       | mandatory         | Key-based pagination - number of rows per request                    |
| `next_key` | string    | optional          | Id from the previous request, empty on the first request             |
| `order_by` | string    | optional          | Available options: `name`, `repository_path`, `registry`, `risks`    |
| `filters`  | filterObj | optional          | Filter the results by the available filters listed in filter\_object |

**filterObj:**

| Name            | Type                       | Required/Optional | Description                                                                                                                                                      |
| --------------- | -------------------------- | ----------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `time_period`   | string                     | optional          | Default: now Available options: now, 1 hour, 24 hours, 3 days, 7 days, 10 days                                                                                   |
| `cve_id`        | array\[string]             | optional          | CVE identifier                                                                                                                                                   |
| `risk`          | array                      | optional          | Available filters: `malicious`, `untrusted_registry`, `integrity_violation`, `critical_applicable`                                                               |
| `component`     | Array\[filterComponentObj] | optional          | You can only filter by the components of the image's vulnerabilities.                                                                                            |
| `applicability` | array\[string]             | optional          | Contextual Analysis result. Possible values: `not_scanned`, `applicable`, `not_applicable`, `undetermined`, `rescan_required`, `upgrade_required`, `not_covered` |
| `severity`      | array\[string]             | optional          | Severity level of the issue (e.g., "High")                                                                                                                       |

**filterComponentObj:**

| Name      | Type   | Required/Optional | Description                                                   |
| --------- | ------ | ----------------- | ------------------------------------------------------------- |
| `name`    | string | optional          | Component name                                                |
| `version` | string | optional          | Component version; if not provided, all versions are returned |

#### Response body

| Name          | Type          | Description                                                  |
| ------------- | ------------- | ------------------------------------------------------------ |
| `total_count` | int           | The total number of images tags that match the filter quarry |
| `pagination`  | paginationObj | Pagination info for the request                              |
| `images_tags` | imageTagsObj  | Images tags that match the filter quarry                     |

**paginationObj:**

| Name       | Type   | Description                                              |
| ---------- | ------ | -------------------------------------------------------- |
| `limit`    | int    | Key-based pagination - number of rows per request        |
| `next_key` | string | Id from the previous request, empty on the first request |

**imageTagsObj:**

| Name                 | Type                 | Description                                                                                       |
| -------------------- | -------------------- | ------------------------------------------------------------------------------------------------- |
| `name`               | string               | Image name                                                                                        |
| `tag`                | string               | Image tag                                                                                         |
| `architecture`       | string               | The image architecture (e.g., "amd64")                                                            |
| `registry`           | string               | The user environment (e.g., "jfrog.com")                                                          |
| `repository_path`    | string               | Path to the artifact (as expected to be found in Artifactory)                                     |
| `runtime_status`     | string               | Possible values: `running`, `stopped`, `unknown`                                                  |
| `scan_info`          | scanInfoObj          | Information on whether the image was scanned                                                      |
| `risks`              | Array of risk\_enum  | Possible values: malicious, untrusted\_registry, integrity\_violation, critical\_applicable\_cves |
| `vulnerabilities`    | Array\[vulnObj]      | An array of the vulnerabilities detected on the image tag                                         |
| `malicious_packages` | Array\[maliciousObj] | An array of malicious packages detected on the image tag                                          |
| `workloads`          | Array\[workloadObj]  |                                                                                                   |
| `image_digest`       | string               | Represents the cryptographic hash (SHA256) of the image, which includes image content.            |

**scanInfoObj\*\*:\*\***

| Name  | Type    | Description                                     |
| ----- | ------- | ----------------------------------------------- |
| `sca` | boolean | Indicates whether the image was scanned for sca |

**vulnObj\*\*:\*\***

| Name            | Type                 | Description                                                                                                                                                      |
| --------------- | -------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `cve_id`        | string               | CVE identifier                                                                                                                                                   |
| `xray_id`       | string               | Xray identifier                                                                                                                                                  |
| `severity`      | string               | Severity level of the issue (e.g., "High")                                                                                                                       |
| `cvss_v2`       | string               | CVSS version 2 score                                                                                                                                             |
| `cvss_v3`       | string               | CVSS version 3 score                                                                                                                                             |
| `applicability` | string               | Contextual Analysis result. Possible values: `not_scanned`, `applicable`, `not_applicable`, `undetermined`, `rescan_required`, `upgrade_required`, `not_covered` |
| `components`    | array\[componentObj] | The components information                                                                                                                                       |

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

**workloadObj:**

| Name        | Type   | Description        |
| ----------- | ------ | ------------------ |
| `name`      | string | Workload name      |
| `namespace` | string | Workload namespace |
| `cluster`   | string | Cluster name       |

**Response codes:**

| Status code | Description                               | Message |
| ----------- | ----------------------------------------- | ------- |
| 200         | OK                                        |         |
| 400         | Bad request - Required fields are missing |         |
| 403         | Permission denied                         |         |
| 404         | Not found                                 |         |
| 500         | Internal server error                     |         |

#### Examples

Example request

```json
{
  "limit": 1
}
```

Example request

```json
{
  "limit": 1,
  "next_key": "1"
}
```

Example request

```json
{
  "filters": {
    "component": [
      {
        "name": "rexml",
        "version": "3.2.5"
      }
    ]
  }
}
```

Example request

```json
{
  "filters": {
    "time_period": "now",
    "cve_id": [
      "CVE-2013-7285"
    ]
  }
}
```

Example request

```json
{
  "filters": {
    "severity": [
      "Critical",
      "High"
    ]
  }
}
```

Example request

```json
{
  "filters": {
    "risk": [
      "untrusted_registry",
      "integrity_violation"
    ]
  }
}
```

Example request

```json
{
  "filters": {
    "applicability": [
      "applicable"
    ]
  }
}
```

Example successful response

`200 OK`

```json
{
    "image_tags": [
        {
            "architecture": "amd64",
            "malicious_packages": [],
            "name": "webgoat",
            "registry": "jfrog.com",
            "repository_path": "docker-local/webgoat",
            "risks": [
                "critical_applicable_cves"
            ],
            "runtime_status": "running",
            "scan_info": {
                "sca": true
            },
            "tag": "latest",
            "vulnerabilities": [
                {
                    "applicability": "applicable",
                    "components": [
                        {
                            "id": "gav://com.thoughtworks.xstream:xstream:1.4.5",
                            "name": "com.thoughtworks.xstream:xstream",
                            "version": "1.4.5"
                        }
                    ],
                    "cve_id": "CVE-2013-7285",
                    "cvss_v2": "7.5",
                    "cvss_v3": "9.8",
                    "severity": "Critical",
                    "xray_id": "XRAY-60282"
                }
            ],
            "workloads": [
                {
                    "cluster": "runtime-cluster",
                    "name": "webgoat",
                    "namespace": "production"
                }
            ]
        }
    ],
    "pagination": {
        "limit": 1,
        "next_key": "1"
    },
    "total_count": 2
}
```

Example successful response

`200 OK`

```json
{
    "image_tags": [
        {
            "architecture": "arm64",
            "malicious_packages": [
                {
                    "components": [
                        {
                            "id": "pypi://ecopower:1.3",
                            "name": "ecopower",
                            "version": "1.3"
                        }
                    ],
                    "xray_id": "XRAY-198184"
                },
                {
                    "components": [
                        {
                            "id": "pypi://zlibsrc:1.1",
                            "name": "zlibsrc",
                            "version": "1.1"
                        }
                    ],
                    "xray_id": "XRAY-249065"
                }
            ],
            "name": "demo-security",
            "registry": "jfrog.com",
            "repository_path": "docker-local/jfrog",
            "risks": [
                "critical_applicable_cves",
                "malicious"
            ],
            "runtime_status": "running",
            "scan_info": {
                "sca": true
            },
            "tag": "latest",
            "vulnerabilities": [
                {
                    "applicability": "not_applicable",
                    "components": [
                        {
                            "id": "pypi://pycrypto:2.6.1",
                            "name": "pycrypto",
                            "version": "2.6.1"
                        }
                    ],
                    "cve_id": "CVE-2013-7459",
                    "cvss_v2": "7.5",
                    "cvss_v3": "9.8",
                    "severity": "Critical",
                    "xray_id": "XRAY-84306"
                }
            ],
            "workloads": [
                {
                    "cluster": "runtime-cluster",
                    "name": "demosecurity",
                    "namespace": "production"
                }
            ]
        }
    ],
    "pagination": {
        "limit": 1,
        "next_key": "1"
    },
    "total_count": 38
}
```

**Example error response:**

`400 Bad Request`

```json
{
    "message": "limit should be between 1 and 100"
}
```
