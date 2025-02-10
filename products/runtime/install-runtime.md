# Install Runtime

## Self-Hosted Requirements

## Before You Begin (SH)

Before proceeding with the installation, ensure the following system requirements are met:

Type of supported database: Postgres16

<table><thead><tr><th>Monitored Nodes</th><th width="200">vCPUs</th><th>Memory (GiB)</th><th>Storage Type</th><th>Network Performance</th></tr></thead><tbody><tr><td>Runtime Integrity (controller only setup) or 100 nodes and below</td><td>2</td><td>10</td><td><p>SSD</p><p>20 GiB<br>IOps: 600<br>Throughput:500MBps</p></td><td>4750 Mbps</td></tr><tr><td>500 nodes and below</td><td>10</td><td>32</td><td><p>SSD</p><p>100 GiB</p><p>IOps: 3000</p><p>Throughput:500MBps</p></td><td>4750 Mbps</td></tr><tr><td>1000 nodes and below</td><td>Contact JFrog Support for sizing requirements.</td><td></td><td></td><td></td></tr></tbody></table>

#### CPU and Memory (SH) <a href="#cpu-and-memory" id="cpu-and-memory"></a>

Nodes are considered to run an average of 100 pods.

| Number of running nodes | CPU                                            | Memory |
| ----------------------- | ---------------------------------------------- | ------ |
| 100 nodes and below     | 6 Cores                                        | 16 GiB |
| 500 nodes and below     | 30 Cores                                       | 16 GiB |
| 1000 nodes and below    | Contact JFrog Support for sizing requirements. |        |

## Self-Hosted and SaaS Requirements <a href="#kernel-operating-systems-support" id="kernel-operating-systems-support"></a>

#### Kernel Operating Systems Support  <a href="#kernel-operating-systems-support" id="kernel-operating-systems-support"></a>

| Linux Kernel         | Windows Kernel                                                                                                                     |
| -------------------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| <p>4.18+</p><p> </p> | ![:cross\_mark:](https://jfrog-int.atlassian.net/gateway/api/emoji/62d6e2d0-84c6-4564-9b2c-7379252a974d/atlassian-cross_mark/path) |

#### Containers Technology Support  <a href="#containers-technology-support" id="containers-technology-support"></a>

| Kubernetes | OpenShift |
| ---------- | --------- |
| 1.21+      | 1.21+     |

Before proceeding with the installation, ensure the following requirements are met:

* **Kubernetes Cluster Access:** Ensure your `kubectl` and `helm` clients can access the Kubernetes cluster where you intend to install the Runtime Service.
* **Ingress Controller:** JFrog officially supports the Nginx controller configured with TLS. Other ingress controllers may work if they support GRPC communication.
* **JFrog Platform:** JFrog Runtime Security must be installed on a pre-existing JFrog platform.

###
