# Troubleshooting

## **Common Issues and Fixes**

### **Token Expiration Issues**

If you encounter token expiration issues during scans, consider extending the token expiration time in the **Identity Mapping Configuration**. This adjustment helps ensure that the token remains valid throughout the scanning process.

### **Credentials Configuration**

Ensure that either `JF_USER + JF_PASSWORD` or `JF_ACCESS_TOKEN` is set, but not both at the same time. Having both configurations can lead to conflicts.

### **Debugging Frogbot Issues**

When sending logs to support, please include the following environment variable to enable detailed logging:\
&#xNAN;**`JFROG_CLI_LOG_LEVEL=DEBUG`** .

### **Node Requirements**

#### **Operating Systems Supported**

Frogbot scanners support the following operating systems:

* Ubuntu 18+
* RHEL 8+

#### **Required Packages**&#x20;

Ensure the following packages are available in your environment:

* **Unzip**
* **Glibc-2.33+**
* **curl**
* **Git**

Note: The above packages are included in the standard base images (e.g., Ubuntu, RHEL), but if you are using lighter images like Alpine, you will need to ensure these packages are installed.
