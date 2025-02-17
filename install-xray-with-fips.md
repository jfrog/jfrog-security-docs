# Install Xray with FIPS

### Overview

This installation method is fully supported for the Linux archive-based installer and is only available for RPM-based operating systems, specifically **RHEL 8, RHEL 9, and Amazon Linux 3**.

### Installation Procedure

#### Prerequisites

Before installing JFrog Xray using the Linux archive method, ensure the following prerequisites are met:

* **A running JFrog Artifactory instance** that Xray will connect to.
* **PostgreSQL Database** (Use an external PostgreSQL on a separate VM or manage it via RDS.)
*   **A FIPS-enabled VM** with the required packages installed:

    **Erlang with FIPS Support**

    JFrog provides FIPS-compiled Erlang binaries for the following OS versions:

    * **RHEL 8** - \[[Download Link](https://releases.jfrog.io/artifactory/installers/erlang-fips/26.2.5/erlang-26.2.5.6-1.el8.x86_64.rpm)]
    * **RHEL 9** - \[[Download Link](https://releases.jfrog.io/artifactory/installers/erlang-fips/26.2.5/erlang-26.2.5.6-1.el9.x86_64.rpm)]
    * **Amazon Linux 3** - \[[Download Link](https://releases.jfrog.io/artifactory/installers/erlang-fips/26.2.5/erlang-26.2.5.6-1.amzn2023.x86_64.rpm)]

    After installing Erlang, verify FIPS mode using:

    ```
    erl
    crypto:enable_FIPS_mode(true).
    crypto:info_FIPS().
    ```

    The output should confirm FIPS mode is enabled.

    **dbutils**

    The `db_dump` command-line utility is required. Verify installation by running:

    ```
    db_dump
    ```

    Installation commands by OS:

    * **RHEL 8**: Included by default
    * **RHEL 9**: `yum install libdb-utils`
    * **Amazon Linux 2023**: `yum install libdb-utils`

***

### Setting Up JFrog Xray

#### Fresh Installation

Once prerequisites are met, follow these steps:

1. **Download the Xray Linux archive-based installer** (`tar.gz`) from the JFrog Xray Downloads page.
2.  **Extract the archive**:

    ```
    tar -xvf jfrog-xray-<version>-linux.tar.gz
    ```
3.  **Set up OS User Permissions**:

    * Xray installation script creates an `xray` user by default.
    * Ensure run and execute permissions on the installation directory.
    * Recommended installation directory: `/opt`.

    ```
    mkdir -p /opt/jfrog
    cp -r jfrog-xray-<version>-linux /opt/jfrog/
    cd /opt/jfrog
    mv jfrog-xray-<version>-linux xray
    cd xray/app/bin
    ```

> **Note:** From version **3.107** onwards, Xray installers organize files into designated subfolders. Ensure correct navigation post-extraction.

4.  **Run the Installation Script**:

    ```
    ./install.sh
    ```

    The script prompts for input:

    * **Artifactory URL** (`http://artifactory_node_ip:port`)
    * **Join Key** (Retrieve from: _Administration > Security > General > Connection Details_)
    * **Machine IP Address** (System auto-detects or manually enter, ensure IPv6 is in `[]`)
    *   **Database Connection Details**:

        ```
        postgres://<IP_ADDRESS>:<PORT>/<DATABASE_NAME>?sslmode=disable
        ```

        * **Username**: `<YOUR_DATABASE_USERNAME>`
        * **Password**: `<YOUR_DATABASE_PASSWORD>`
5. **Configure FIPS for RabbitMQ**:
   *   Create `advanced.conf` in `/opt/jfrog/xray/var/etc/`:

       ```
       [
       {crypto, [
       {FIPS_mode, true}
       ]}
       ].
       ```
   *   Set environment variable:

       ```
       export RABBITMQ_ADVANCED_CONFIG_FILE="${JF_PRODUCT_HOME}/var/etc/advanced.conf"
       ```
   *   Ensure permissions:

       ```
       chown -R xray:xray /opt/jfrog/xray
       ```
6.  **Start Xray Service**:

    ```
    xray/app/bin/xray.sh start|stop
    ```

#### Installing Xray as a Service

Xray can be installed as a system service. Execute:

```
xray/app/bin/installService.sh
```

**Options:**

* `-u | --user`: (default: `xray`) Specify a custom user.
* `-g | --group`: (default: `xray`) Specify a custom group.

To manage the service:

```
systemctl <start|stop|status> xray.service
```

***

### Adding Nodes to an Xray Cluster

For additional nodes:

1. Repeat the initial Xray installation.
2. When prompted, **select** `Y` for adding to an existing cluster.
3.  **Provide the master key**:

    ```
    cat /opt/jfrog/xray/var/etc/security/master.key
    ```
4. **Enter the active RabbitMQ node hostname.**
5. **Use the same PostgreSQL details as the first node.**
6. Follow the **FIPS and permission setup** steps from the primary node.

***

### Upgrades (does it need to be separate? under upgrades?)

Follow these steps to upgrade Xray:

1.  **Stop the running service**:

    ```
    systemctl stop xray.service
    ```
2.  **Extract the new version**:

    ```
    tar -xf jfrog-xray-<version>-linux.tar.gz -C /opt/jfrog/
    ```
3.  **Replace the `app` folder**:

    ```
    export JFROG_HOME=/opt/jfrog
    export JF_NEW_VERSION=/opt/jfrog/jfrog-xray-<version>-linux
    rm -rf $JFROG_HOME/xray/app
    cp -fr $JF_NEW_VERSION/app $JFROG_HOME/xray/
    ```
4.  **Set permissions**:

    ```
    chown -R xray:xray /opt/jfrog/xray
    ```
5.  **Start the service**:

    ```
    systemctl start xray.service
    ```

***

### Uninstallation

For uninstallation, refer to the JFrog Xray Uninstallation Guide.
