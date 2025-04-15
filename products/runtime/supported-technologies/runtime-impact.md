# Runtime Impact

### Database & Package Type Support

| Component    | Supported                |
| ------------ | ------------------------ |
| Database     | Postgres 16              |
| Package Type | Java, Go, OS executables |

### System Architecture & Platform Compatibility

| Technology           | Supported                           | Not Supported  |
| -------------------- | ----------------------------------- | -------------- |
| Node architecture    | X86-64, ARM64                       | ​              |
| Container technology | Kubernetes 1.21+, OpenShift 1.21+   | ​              |
| Computing platforms  | AWS, GCP, Azure, on-prem Kubernetes | ​              |
| Kernel OS            | Linux Kernel 4.18+                  | Windows Kernel |
| ​Protocol Support    | HTTP/2                              | ​              |

### Runtime Impact – Recommended PostgreSQL Database Sizing

Type of supported database: **PostgreSQL 16**\
Nodes are considered to run an average of 100 pods.

| Monitored Nodes                                                  | vCPUs                                          | Memory (GiB) | Storage Type | Storage Specs                           | Network Performance |
| ---------------------------------------------------------------- | ---------------------------------------------- | ------------ | ------------ | --------------------------------------- | ------------------- |
| Runtime Integrity (controller only setup) or 100 nodes and below | 2                                              | 10           | SSD          | 20 GiB, 600 IOPS, 500 MBps throughput   | 4750 Mbps           |
| 500 nodes and below                                              | 10                                             | 32           | SSD          | 100 GiB, 3000 IOPS, 500 MBps throughput | 4750 Mbps           |
| 1000 nodes and below                                             | Contact JFrog Support for sizing requirements. |              |              |                                         |                     |
