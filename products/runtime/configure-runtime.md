---
description: >-
  This workflow sets up the JFrog Runtime Security system and ensures it’s
  configured correctly.
---

# Configure Runtime



## **Enabling/Disabling Runtime Sensors**

*   Disable on specific nodes:

    ```sh
    shCopyEditkubectl label nodes <node-name> disable_jfrog_runtime=true
    ```
*   Enable sensors:

    ```sh
    shCopyEditkubectl label nodes <node-name> disable_jfrog_runtime-
    ```

***

## **Monitoring & Verification**

* Navigate to **Sensor Management** in the JFrog UI to verify sensor deployment.
* Use **Live Assessment** to check runtime security insights, risks, and workloads.
