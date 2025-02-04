# Supported Technologies

### **Computing Platforms Support**

| Cloud Provider | On-Prem Support | Orchestration |
| -------------- | --------------- | ------------- |
| AWS            | Yes             | Kubernetes    |
| GCP            | Yes             | -             |
| Azure          | Yes             | -             |

### **Containers Technology Support**

| Container Platform | Supported Versions |
| ------------------ | ------------------ |
| Kubernetes         | 1.21+              |
| OpenShift          | 1.21+              |

### **Runtime Impact - Recommended Postgres Database**

| Monitored Nodes                                            | vCPUs                                         | Memory (GiB) | Storage Type | Network Performance |
| ---------------------------------------------------------- | --------------------------------------------- | ------------ | ------------ | ------------------- |
| Runtime Integrity (Controller only) or 100 nodes and below | 2                                             | 10           | SSD          | 4750 Mbps           |
| 500 nodes and below                                        | 10                                            | 32           | SSD          | 4750 Mbps           |
| 1000 nodes and below                                       | Contact JFrog Support for sizing requirements | -            | -            | -                   |

### **Runtime Impact - Supported Package Types**

_(Not applicable for Runtime Integrity mode)_

| Programming Languages | Executable Types |
| --------------------- | ---------------- |
| Java                  | OS Executables   |
| Go                    | -                |
