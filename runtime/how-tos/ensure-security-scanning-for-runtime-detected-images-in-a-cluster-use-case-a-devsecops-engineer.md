# Ensure Security Scanning for Runtime-Detected Images in a Cluster Use Case  A DevSecOps engineer

An admin wants to ensure that all container images running in their Kubernetes clusters are automatically scanned for vulnerabilities and secrets. The engineer already uses Runtime Visibility to monitor activity in the cluster, but notices that some images appear without corresponding security scan results. To close this gap, they enable and configure Runtime scan settings for the cluster so that every image observed by the sensors is automatically scanned using SCA and Advanced Security capabilities.

This ensures consistent security coverage across the environment—no image running in the cluster remains unscanned.

### **How To Configure Runtime Security Scanning for a Cluster**

1. In the platform, under **Administration**, go to **Runtime > Sensor Management**.
2. Locate the cluster you want to secure under the **Clusters** list.
3. Hover over the cluster and open the cluster’s menu.
4. Select **Configure**.
5. When the **Scan Configuration** window opens, choose the security scanners you want to apply.
   * Enable **SCA** to scan packages and dependencies.
   * Enable **Advanced Security** features such as **Vulnerabilities Contextual Analysis**, **Secrets**, **Applications**, **Services**, or **IaC**, depending on your needs.
6. Review or adjust the **Retention** period for how long scan results should be stored.
7. Click **Apply** to save the configuration.
8. A confirmation banner appears, indicating the cluster has been successfully configured.

Once configured, the system automatically evaluates each image detected by Runtime sensors. Any image without existing security information will be indexed and scanned according to the selected scanners. This ensures security coverage remains synchronized with real runtime activity.
