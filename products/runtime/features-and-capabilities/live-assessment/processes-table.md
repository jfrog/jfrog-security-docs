# Processes Table

{% hint style="info" %}
This is available only for Runtime impact (Controller + Sensors)
{% endhint %}

Under each workload, a list of process groups is presented. A process group is grouped based on its executable, execution location, command arguments, image, and workload.



The Processes table is designed to provide a comprehensive view of the processes by combining information from three key areas: process information, infrastructure information, and vulnerability information. This allows users to gain a deeper understanding of the processes running in their environment and to identify potential vulnerabilities or issues that may need to be addressed.

Additionally, the list of data in the Processes table can be filtered based on various fields, providing the ability to selectively view specific information. This makes it easier to identify and prioritize issues based on specific search criteria.

The table consists of these main key data:

* **Process name:** String
* **Risks:**
  * A process can be executed through multiple image tags. In an image tag, the running process can have different risks.
  * The risk column in the process table encompasses all of these risks. For example, a vulnerability might apply in one image tag but not another.
* **Vulnerabilities:** The number of vulnerabilities associated with the process, in case all images running are untrusted it will be shown as “unknown“.&#x20;
* **Status:**
  * Running: If currently running in at least one workload.
  * Stopped: If it has stopped in all of the workloads.
* **Argument:** Describes the execution configuration of the process.
* **Path:** Location in Artifactory.

Process name, arguments, path, and SHA256 (hidden column) create a single identifier for a process.
