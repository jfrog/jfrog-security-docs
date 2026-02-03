# Get Cluster

**Description:** Retrieve a list of nodes and cluster information for a given ID

**Security:** Admin

**Usage:** `GET /runtime/api/v1/cluster/{id}`

**Produces:** `application`/`json`

#### Response body <a href="#id-52825iys1ugq" id="id-52825iys1ugq"></a>

| **Name**  | **Type**   | **Description**                                      |
| --------- | ---------- | ---------------------------------------------------- |
| `cluster` | clusterObj | A cluster object containing details of each cluster. |

**paginationObj:**

| **Name**   | **Type** | **Description**                                                |
| ---------- | -------- | -------------------------------------------------------------- |
| `limit`    | int      | Key-based pagination - number of rows per request. Default: 10 |
| `next_key` | string   | Id from the previous request, empty on the first request       |

**clusterObj:**

| **Name**                  | **Type**          | **Description**                                                                    |
| ------------------------- | ----------------- | ---------------------------------------------------------------------------------- |
| `monitored_at`            | string (ISO 8601) | Timestamp when the monitoring of the cluster started                               |
| `id`                      | string            | Unique identifier for the cluster in the system. (this is the cluster\_identifier) |
| `name`                    | string            | The name of the cluster.                                                           |
| `controller_version`      | string            | The version of the cluster controller.                                             |
| `controller_status`       | string            | Possible options: running, stopped                                                 |
| `controller_last_updated` | string            | Date of last update                                                                |
| `provider`                | string            | The cloud provider where the cluster is hosted (e.g., aws).                        |
| `regions`                 | Array\[string]    | List of regions in which the cluster is deployed.                                  |
| `nodes_count`             | int               | The total number of nodes in the cluster.                                          |
| `nodes`                   | Array\[nodeObj]   | A list of associated node objects for the cluster.                                 |

**nodeObj:**

| **Name**              | **Type**          | **Description**                                                                                  |
| --------------------- | ----------------- | ------------------------------------------------------------------------------------------------ |
| `id`                  | int               | Unique identifier for the node.                                                                  |
| `monitored_at`        | string (ISO 8601) | Timestamp when the monitoring of node started                                                    |
| `name`                | string            | The hostname of the node.                                                                        |
| `sensor_installed`    | boolean           | Indicates whether the sensor is installed on the node.                                           |
| `sensor_last_updated` | string (ISO 8601) | Timestamp of when the sensor was last updated.                                                   |
| `sensor_version`      | string            | Version of the installed sensor.                                                                 |
| `region`              | string            | Region where the node is located.                                                                |
| `architecture`        | string            | The architecture of the node (e.g., amd64).                                                      |
| `hostname`            | string            | The hostname of the node.                                                                        |
| `internal_dns`        | string            | Internal DNS name of the node.                                                                   |
| `internal_ip`         | string            | Internal IP address of the node.                                                                 |
| `status`              | string            | nodes status: monitored \| monitored\_with\_sensor \| failed \| installation\_failed \| disabled |

**Response codes:**

| **Status code** | **Description**                           |
| --------------- | ----------------------------------------- |
| 200             | OK                                        |
| 400             | Bad request - Required fields are missing |
| 403             | Permission denied                         |
| 404             | Not found                                 |
| 500             | Internal server error                     |

#### Request URL : <a href="#id-2a69rfaw96qy" id="id-2a69rfaw96qy"></a>

```
GET /runtime/api/v1/cluster/{id}
```

Example successful response

```
200 OK
{
   "cluster": {
       "controller_last_updated": "2024-12-31T11:30:20.377448Z",
       "controller_status": "running",
       "controller_version": "0.0.0",
       "disabled_nodes_count": 0,
       "failed_nodes_count": 0,
       "failed_to_install_nodes_count": 0,
       "id": 2,
       "monitored_at": "2024-12-25T12:28:13.438479Z",
       "name": "z0runtime",
       "nodes": [
           {
               "architecture": "amd64",
               "hostname": "ip-10-90-99-192",
               "id": 10,
               "internal_dns": "",
               "internal_ip": "10.90.99.192",
               "monitored_at": "2024-12-25T12:28:13.586002Z",
               "name": "ip-10-90-99-192",
               "region": "",
               "sensor_installed": true,
               "sensor_last_updated": "2024-12-31T11:30:23.579048Z",
               "sensor_version": "0.0.0-20241224065042-65402c9bec33-43",
               "status": "running_with_sensors"
           },
           {
               "architecture": "amd64",
               "hostname": "ip-10-90-110-75",
               "id": 7,
               "internal_dns": "",
               "internal_ip": "10.90.110.75",
               "monitored_at": "2024-12-25T12:28:13.555669Z",
               "name": "ip-10-90-110-75",
               "region": "",
               "sensor_installed": true,
               "sensor_last_updated": "2024-12-31T11:30:25.450216Z",
               "sensor_version": "0.0.0-20241224065042-65402c9bec33-43",
               "status": "running_with_sensors"
           },
           {
               "architecture": "arm64",
               "hostname": "ip-10",
               "id": 9,
               "internal_dns": "",
               "internal_ip": "10.90.98.85",
               "monitored_at": "2024-12-25T12:28:13.576732Z",
               "name": "ip-10-90-98-85",
               "region": "",
               "sensor_installed": true,
               "sensor_last_updated": "2024-12-31T11:30:27.109623Z",
               "sensor_version": "0.0.0",
               "status": "running_with_sensors"
           },
           {
               "architecture": "amd64",
               "hostname": "ip-10",
               "id": 8,
               "internal_dns": "",
               "internal_ip": "10.90.124",
               "monitored_at": "2024-12-25T12:28:13.566903Z",
               "name": "ip-10-90-124-154",
               "region": "",
               "sensor_installed": true,
               "sensor_last_updated": "2024-12-31T11:30:24.598452Z",
               "sensor_version": "0.0.0",
               "status": "running_with_sensors"
           }
       ],
       "nodes_count": 4,
       "provider": "kubernetes",
       "regions": [],
       "running_nodes_count": 4
   }
}
```

Example error response:

```
404 Not Found
{
    "error": "error message"
}
```
