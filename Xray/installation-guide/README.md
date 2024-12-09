## **Installing JFrog Xray**

### Overview
This document outlines the installation and setup process for JFrog Xray on a self-hosted platform. Xray is available with **Pro X**, **Enterprise X**, and **Enterprise+** licenses, and can be configured for both single node and high availability deployments. It is important to first install JFrog Artifactory 7.x before proceeding with Xray 3.x installation.

### Important Notifications
- **Dedicated Server:** It is highly recommended to use a dedicated server for Xray. Running other software on the same server can lead to performance bottlenecks, port conflicts, and undesirable configurations.
- **Port Conflicts:** If you install Xray on the same server as Artifactory, be aware of potential port conflicts. Both applications use port 8082 for network communication and share other ports (8082, 8046, 8047, and 8049) for the Router microservice.

#### Admin Permissions for Installation
It is recommended to run the installation as a root user or to provide sudo access to a non-root user. Admin permissions are needed in the following scenarios:
- **Native installer**: Always requires admin permissions.
- **Archive installer**: Requires admin permissions during installation only.
- **Docker installer**: Does not require admin permissions.

### Installation Steps
Follow these steps to install JFrog Xray:

1. **Download Xray**: Obtain the installer package suitable for your system (Docker Compose, RPM, Debian).

2. **Install Xray**: Choose between a single node installation or a high availability cluster.
   - **Install third-party dependencies**: PostgreSQL database is included in the archive.
   - **Install Xray**: Execute the installation process according to the chosen method.

3. **Configure Xray Basic Settings**:
   - Connect to an existing Artifactory instance. You will need a `joinKey` and `jfrogUrl`, which should be specified in the Xray `system.yaml` file.
   - (Optional) Configure the PostgreSQL database connection details if PostgreSQL is used as an external database.

4. **Start the Service**: Use the provided start scripts or the service management tools of your operating system.

5. **Check the Service Log**: Review the logs to confirm the successful startup of the service.

### Default Home Directory / $JFROG_HOME
The default home directory for JFrog Xray is determined by the installation type. Refer to **System Directories** for more specific details. The `$JFROG_HOME` variable represents the root directory of the JFrog product installation.

By following these guidelines, you can successfully install and configure JFrog Xray in your environment. Always ensure that your installations comply with the outlined recommendations to avoid any issues during operation.