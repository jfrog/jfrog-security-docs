# Installation

## **Download the JFrog Eclipse Plugin**

| Version | Download link                                                                                                                  | Compatibility       |
| ------- | ------------------------------------------------------------------------------------------------------------------------------ | ------------------- |
| 1.2.0   | [Download](https://github.com/jfrog/jfrog-eclipse-plugin/releases/download/1.2.0/com.jfrog.ide.eclipse.releng.update-site.zip) | Eclipse 4.13 - 4.33 |
| 1.1.1   | [Download](https://github.com/jfrog/jfrog-eclipse-plugin/releases/download/1.1.1/com.jfrog.ide.eclipse.releng.update-site.zip) | Eclipse 4.10 - 4.19 |

## **Install the JFrog Eclipse Plugin**

1. **Download** the JFrog Eclipse IDE Plugin zip file.
2. Open **Eclipse** and go to **Help** > **Install New Software**.
3. Click **Add**, then select **Archive**.
4. Choose the **plugin zip file** you downloaded and click **Add**.
5. Click **Next** to complete the installation.

**Note**: If JFrog Xray is behind an **HTTP proxy**, configure the proxy settings described [here](https://help.eclipse.org/latest/index.jsp?topic=%2Forg.eclipse.platform.doc.user%2Freference%2Fref-net-preferences.htm). (Supported in versions 1.1.1 and 1.2.0 of the JFrog Eclipse Plugin.)

## **Configure the Plugin**

After installing the plugin, you need to connect it to **JFrog Xray**.

1. Open **Eclipse Preferences** and go to **JFrog Xray**.
2. Enter your **JFrog Platform URL** and **login credentials**.
3. Click **Test Connection** to verify your setup.

## **Scan and View Xray Results**

Once connected, you can start scanning Gradle projects with JFrog Xray.

* **Run a scan** and view results directly in Eclipse.
* **Filter scanned results** to focus on specific components.

For detailed steps on scanning Gradle projects, see Scanning with the JFrog Eclipse Plugin.
