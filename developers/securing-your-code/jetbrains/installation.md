# Installation

**Step 1: Install the JFrog Plugin**

* Install the JFrog Plugin via the **Plugins** tab in the IDE settings or from **JetBrains Marketplace**.

**Step 2: Connect IntelliJ IDEA to Your JFrog Environment**

You can connect the plugin to your JFrog environment using one of the following methods:

**Using the IDE Settings**

1. Once the plugin is installed, open **Settings (Preferences) > Other Settings > JFrog Global Configuration**.
2. Enter your JFrog Platform URL and login credentials.
3. Click **Test Connection** to verify connectivity to Xray.
4. If your JFrog Platform instance is behind an HTTP proxy, configure the proxy settings as described here.
   * **Manual proxy configuration** is supported from version **1.3.0**.
   * **Auto-detect proxy settings** is supported from version **1.7.0**.

**Using Environment Variables**

1. Open **Settings (Preferences) > Other Settings > JFrog Global Configuration**.
2. Enable **Load connection details from environment variables**.
3. Set the required environment variables:
   * `JFROG_IDE_PLATFORM_URL` – JFrog Platform URL
   * You can provide basic authentication credentials or an access token.

**Note:** For security reasons, it is recommended to unset environment variables after launching the IDE.

**Step 3: Start Using the Plugin**

Once connected, you can start using the JFrog plugin within IntelliJ IDEA.

***

#### **Notes**

* If your JFrog Platform instance uses a domain with a self-signed certificate, add the certificate to IntelliJ IDEA as described here.
* **Xray Permissions:**
  * **Xray 1.9 to 2.x:** Users must be granted the **"View Components"** action.
  * **Xray 3.x and later:** Users require **"Read"** permission to connect. More details here.

