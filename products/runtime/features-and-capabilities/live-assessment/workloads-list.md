# Workloads List

The main Live Assessment screen displays a list of workloads that have been detected in the runtime environment.&#x20;

Workloads consist of one or more containers or applications running in your runtime environment. They represent the operational tasks and services that are actively executing on your infrastructure. The Workloads List in the Live Assessment screen offers a comprehensive overview of these detected workloads, along with detailed information about their status and associated risks.

The Workload table displays a row for every workload operating in production. Each workload is linked to a specific image (accessible in the image tab) and the corresponding running processes are listed beneath each row.&#x20;



The table consists of these main key data:

* **Risk column**: There are four [risks ](broken-reference)for each Workload however, the sources of the risks are different.&#x20;
  * Integrity Violation and Untrusted Registry risks come from the associated image with the workloads. and do not appear in the running processes.
  * Critical/applicable CVEs and Malicious Packages riska are associated, with the running processes and can be a sub-set of the risk.
* **Vulnerability column**: A sum of all vulnerabilities of the associated processes
* **Status column**: Indicates if the workload is running or not
* **Cluster, Node, and Namespace** columns are information directly associated with the workload. They are intended to assist you in locating the specific area where problems can be addressed within your cloud environments.
