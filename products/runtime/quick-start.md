# Quick Start

## Prerequisites

It is essential that you have:

* [Xray installed](https://jfrog.com/help/r/jfrog-installation-setup-documentation/installing-xray)
* The JFrog platform domain name
* The Artifactory Kubernetes service name (used for your Xray installation)&#x20;
* JFrog platform `<join-key>`

## **Enabling/Disabling Runtime Sensors**

*   Disable on specific nodes:

    ```sh
    shCopyEditkubectl label nodes <node-name> disable_jfrog_runtime=true
    ```
*   Enable sensors:

    ```sh
    shCopyEditkubectl label nodes <node-name> disable_jfrog_runtime-
    ```

## **Monitoring & Verification**

* Navigate to **Sensor Management** in the JFrog UI to verify sensor deployment.
* Use **Live Assessment** to check runtime security insights, risks, and workloads.
