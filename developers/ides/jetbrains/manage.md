# Manage

## **Access Plugin Settings**

Click on the **gear icon** in the JFrog panel to access the plugin settings.

## **Downloading External Resources Through Artifactory**

The JFrog Plugin requires external resources for scanning projects. By default, these resources are downloaded from [**https://releases.jfrog.io**](https://releases.jfrog.io). If the machine running the IDE does not have access to this URL, configure Artifactory as a proxy:

### **Configure Artifactory as a Proxy**

1. **Log in** to the JFrog Platform UI as an administrator.
2. **Create a Remote Repository** with the following settings:
   * **Basic Tab:**
     * **Package Type:** Generic
     * **Repository Key:** `jfrog-releases-repository`
     * **URL:** `https://releases.jfrog.io`
   * **Advanced Tab:**
     * **Uncheck** _Store Artifacts Locally_.
3. In the JFrog Plugin settings, navigate to **JFrog Global Configuration > Advanced**.
4. Click **Download resources through Artifactory**.
5. Enter the **Repository Key** you created in the **Repository Key** field.
6.  Alternatively, set the environment variable:

    ```plaintext
    plaintextCopyEditJFROG_IDE_RELEASES_REPO = [Repository Key]
    ```

## **Applying Xray Policies and Watches**

The JFrog Plugin can enforce **security policies** created in JFrog Xray. Policies define security rules and automated actions that are applied when linked to **Watches**.

### **Using a JFrog Project**

If your policies are associated with a **JFrog Project**, follow these steps:

1. **Create a JFrog Project** or obtain an existing **Project Key**.
2. **Create a Policy** in JFrog Xray.
3. **Create a Watch** in JFrog Xray and assign your **Policy** and **Project** to it.
4. **Configure the Project Key** in the plugin settings:
   * Go to **Settings (Preferences) > Other Settings > JFrog Global Configuration**.
   * Navigate to the **Settings** tab and enter the **Project Key**.

### **Using Xray Watches**

If your policies are managed through **Xray Watches**, follow these steps:

1. **Create one or more Watches** in JFrog Xray.
2. **Configure the Watches** in the plugin settings:
   * Go to **Settings (Preferences) > Other Settings > JFrog Global Configuration**.
   * Navigate to the **Settings** tab and enter the Watch details.
