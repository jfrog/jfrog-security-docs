Xray system requirements depend on the size of your environment.

| **Number of Indexed Artifacts**                   | **Processor**                               | **Memory**                       | **Disk Space**                        |
|--------------------------------------------------|---------------------------------------------|----------------------------------|---------------------------------------|
| Up to 100k indexed artifacts, and 1K artifacts/builds per day | Xray and DB: 6 cores                       | JFrog Advanced Security: 24 GB   | Xray and DB: 500 GB (SSD, 3000 IOPS) |
| Up to 1M indexed artifacts, and 10k artifacts/builds per day | Xray (x2 nodes): 4 cores<br>DB: 8 cores    | JFrog Advanced Security (x2 nodes): 24 GB | Xray (x2 nodes): 300 GB<br>DB: 500 GB (SSD, 3000 IOPS) |
| Up to 2M indexed artifacts, and 20k artifacts/builds per day | Xray (x3 nodes): 6 cores<br>DB: 16 cores   | JFrog Advanced Security (x4 nodes): 24 GB | Xray (x3 nodes): 300 GB<br>DB: 1 TB (SSD, 3000 IOPS) |
| Up to 10M indexed artifacts, and 50k artifacts/builds per day | Xray (x3 nodes): 8 cores<br>DB: 16 cores   | JFrog Advanced Security (x8 nodes): 24 GB | Xray (x3 nodes): 300 GB<br>DB: 2.5 TB (SSD, 3000 IOPS) |
| Over 10M indexed artifacts, and 50k artifacts/builds per day | Contact JFrog Support for sizing requirements. |                                  |                                       |

> The number of nodes in the table refers to high availability (HA) setups, not disaster recovery.

##### Xray Node Recommendations
Use a dedicated node for Xray with no other software running to alleviate performance bottlenecks, avoid port conflicts, and avoid setting uncommon configurations.

##### Xray Storage Recommendations
In most cases, our recommendation is to use an SSD drive for Xray to have better performance. It is not recommended to use an NFS drive, as it is a disk I/O-intensive service; a slow NFS server can suffer from I/O bottlenecks, and NFS is mostly used for storage replication.

Xray stores node-specific files, such as configuration and temporary files, to the disk. These files are exclusively used by Xray and not shared with other services. Since the local storage used for Xray services is temporary, it does not require replication between the different nodes in a multi-node/HA deployment.

##### Operating Systems and Platform Support
The following table lists the supported operating systems and the versions.

| **Product**       | **Debian** | **RHEL** | **Ubuntu** | **Amazon Linux** | **Windows Server**   |
|-------------------|------------|----------|------------|-------------------|-----------------------|
| Artifactory       | 10.x, 11.x | 8.x, 9.x | 20.04, 22.04 | Amazon Linux 2023 | 2016 or 2019          |
| Xray              | 10.x, 11.x | 8.x, 9.x | 20.04, 22.04 |    X              |     X                 |
| Distribution      | 10.x, 11.x | 8.x, 9.x | 20.04, 22.04 |    X              |     X                 |
| Insight           | 10.x, 11.x | 8.x, 9.x | 20.04, 22.04 | Amazon Linux 2023 |     X                 |
| Pipelines         |            | 8.x     | 20.04, 22.04 | Amazon Linux 2023 | Build nodes only      |

### Supported Platforms
The following table lists the supported platforms.

| **Product**       | **x86-64** | **ARM64** | **Kubernetes** | **OpenShift** |
|-------------------|------------|-----------|-----------------|----------------|
| Artifactory       | V          | V         | 1.19+           | 4.13+          |
| Xray              | V          | V         | 1.19+           | 4.13+          |
| Distribution      | V          | V         | 1.19+           | 4.13+          |
| Insight           | V          | V         | 1.19+           |     X          |
| Pipelines         | V          |   X       | 1.19+           |     X          |

Installation on Kubernetes environments is through Helm Charts. Supported Helm version is Helm 3+.

### Kubernetes Sizing Requirements
We have included YAML files with different sizing configurations for Artifactory, Xray, and Distribution in our GitHub pages. You can use these YAML files when you set up your cluster.

### ARM64 Support
Starting from version 7.41.4, Artifactory supports installation on ARM64 architecture through Helm and Docker installations. You must set up an external database as the Artifactory database since Artifactory does not support the bundled database with the ARM64 installation. Artifactory installation pulls the ARM64 image automatically when you run the Helm or Docker installation on the ARM64 platform. ARM64 support is also available for Xray, Distribution and Insight.

##### Database and Third-Party Applications in Xray
Every artifact and build indexed by Xray is broken down into multiple components. These components and the relationships between each other are represented in a checksum based components graph. Xray uses PostgreSQL to store and query this components graph.

Xray supports the following versions of PostgreSQL:
* 16.x (from version 3.107)
* 15.x (from version 3.78.9)
* 14.x
* 13.x (from version 3.18)
* 12.x

Xray supports PostgreSQL 14.x and 15.x, but currently, the Xray installer only bundles the binaries for PostgreSQL 13.x.

RabbitMQ is installed as part of the Xray installation for every node. In case of HA architecture, Xray uses queue mirroring between the different RabbitMQ nodes. External RabbitMQ instances are not officially supported; the recommended method of installation is to use the bundled RabbitMQ.

Xray has multiple flows, such as scanning, impact analysis, and database sync. These flows require processing completed by the different Xray microservices. Flows contain multiple steps that are completed by the Xray services. Xray uses RabbitMQ to manage these different flows and track synchronous and asynchronous communication between the microservices.

Xray also uses Erlang and DB-Util third-party applications. These packages are bundled with all Xray installers except Linux Archive. You need to use Erlang version 25.x, and you can use the latest available version of db-util.

##### Xray Network Ports
Xray uses the 8082 port by default for external communication. Xray uses the following internal ports by default for communication with JFrog Platform microservices.

| **Microservice** | **Port**                       |
|------------------|--------------------------------|
| Xray Server      | 8000                           |
| Analysis         | 7000                           |
| Indexer          | 7002                           |
| Persist          | 7003                           |
| Router           | HTTP: 8082, 8046, 8049<br>gRPC: 8047 |
| RabbitMQ         | 4369, 5671, 5672, 15672, 25672 |
| PostgreSQL       | 5432 (if you use the bundled PostgreSQL database) |
| Observability     | HTTP: 8036<br>gRPC: 8037       |