# Troubleshooting

### **Common Issues and Fixes**

#### **Token Expiration Issues**

If you encounter token expiration issues during scans, consider extending the token expiration time in the **Identity Mapping Configuration**. This adjustment helps ensure that the token remains valid throughout the scanning process.

#### **Credentials Configuration**

Ensure that either `JF_USER + JF_PASSWORD` or `JF_ACCESS_TOKEN` is set, but not both at the same time. Having both configurations can lead to conflicts.

#### **Debugging Frogbot Issues**

When sending logs to support, please include the following environment variable to enable detailed logging:\
&#xNAN;**`JFROG_CLI_LOG_LEVEL=DEBUG`** .
