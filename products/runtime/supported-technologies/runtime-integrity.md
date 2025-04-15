# Runtime Integrity

### System Architecture & Platform Compatibility

| Technology                     | Supported                           | Not Supported  |
| ------------------------------ | ----------------------------------- | -------------- |
| Node architecture              | X86-64, ARM64                       |                |
| Container technology           | Kubernetes 1.21+, OpenShift 1.21+   |                |
| Computing platforms            | AWS, GCP, Azure, on-prem Kubernetes |                |
| Kernel OS                      | Linux Kernel 4.18+                  | Windows Kernel |
| <p></p><p>Protocol Support</p> | HTTP/2                              |                |

### CPU and Memory Sizing Guidelines

Nodes are considered to run an average of 100 pods.

| Number of Running Nodes | CPU                                            | Memory |
| ----------------------- | ---------------------------------------------- | ------ |
| 100 nodes and below     | 6 Cores                                        | 16 GiB |
| 500 nodes and below     | 30 Cores                                       | 16 GiB |
| 1000 nodes and below    | Contact JFrog Support for sizing requirements. |        |
