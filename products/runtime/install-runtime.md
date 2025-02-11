# Install Runtime

## System Requirements for Self-Hosted Installation

### Before You Begin

* It is essential you have:
  * Artifactory version 7.77.20
  * Xray version 3.104.08
* Ensure your `kubectl` and `helm` clients can access the Kubernetes cluster where you intend to install the Runtime Service.
* JFrog officially supports the Nginx controller configured with TLS. Other ingress controllers may work if they support GRPC communication.
* JFrog Runtime Security must be installed on a pre-existing JFrog platform.

|                      |                                   |                   |
| -------------------- | --------------------------------- | ----------------- |
| **Component**        | **Supported**                     | **Not Supported** |
| Container technology | Kubernetes 1.21+, OpenShift 1.21+ |                   |
| Kernel OS            | Linux Kernel 4.18+                | Windows Kernel    |
| Database             | Postgres 16                       |                   |

#### CPU and Memory <a href="#cpu-and-memory" id="cpu-and-memory"></a>

Nodes are considered to run an average of 100 pods.

<table><thead><tr><th width="261"></th><th width="369.3333333333333"></th><th></th></tr></thead><tbody><tr><td><strong>Number of Running Nodes</strong></td><td><strong>CPU</strong></td><td><strong>Memory</strong></td></tr><tr><td>100 or below</td><td>6 Cores</td><td>16 GiB</td></tr><tr><td>500 or below</td><td>30 Cores</td><td>16 GiB</td></tr><tr><td>1000 or below</td><td>Contact JFrog Support for sizing requirements.</td><td></td></tr></tbody></table>

<table><thead><tr><th width="205">Monitored Nodes</th><th width="200">vCPUs</th><th>Memory (GiB)</th><th>Storage Type</th><th>Network Performance</th></tr></thead><tbody><tr><td>Runtime Integrity (controller only setup) or 100 nodes and below</td><td>2</td><td>10</td><td><p>SSD</p><p>20 GiB<br>IOps: 600<br>Throughput:500MBps</p></td><td>4750 Mbps</td></tr><tr><td>500 nodes and below</td><td>10</td><td>32</td><td><p>SSD</p><p>100 GiB</p><p>IOps: 3000</p><p>Throughput:500MBps</p></td><td>4750 Mbps</td></tr><tr><td>1000 nodes and below</td><td>Contact JFrog Support for sizing requirements.</td><td></td><td></td><td></td></tr></tbody></table>

## System Requirements for SaaS <a href="#kernel-operating-systems-support" id="kernel-operating-systems-support"></a>

### Before You Begin

It is essential you have:

* Artifactory version 7.77.20
* Xray version 3.104.08

|                      |                                   |                   |
| -------------------- | --------------------------------- | ----------------- |
| **Technology**       | **Supported**                     | **Not Supported** |
| Container technology | Kubernetes 1.21+, OpenShift 1.21+ |                   |
| Kernel OS            | Linux Kernel 4.18+                | Windows Kernel    |
