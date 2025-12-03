# OpenShift SCC

## Grant OpenShift Security Context Constraints Privileges

In **OpenShift**, **Security Context Constraints (SCCs)** are enforced to restrict the permissions of running containers. By default, OpenShift applies strict security policies that limit container privileges, which can prevent the JFrog Runtime Sensor from collecting essential runtime security data.

Granting the necessary privileged SCC ensures that the Runtime Sensor can:

* **Monitor running workloads effectively** by accessing necessary kernel-level data.
* **Collect real-time security insights** using **eBPF technology** to detect threats, integrity violations, and process activity.
* **Transmit security data** from OpenShift nodes to the JFrog Platform for further analysis.

Without this privilege, the sensor may be unable to access required system resources, leading to incomplete security monitoring and reduced visibility into runtime threats.

1. To grant SCC privileges, run:

```
shCopyEditoc adm policy add-scc-to-user privileged system:serviceaccount:jfrog-runtime:jf-sensors-sensors-service-account
```
