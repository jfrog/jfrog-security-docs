# Manage

## **Access Extension Settings**

Click on the **gear icon** in the JFrog tab to access the extension settings.

## **Exclude Paths from Scan**

By default, paths containing `.git`, `test`, `venv`, and `node_modules` are excluded from Xray scans. You can modify the exclusion patterns in the **Extension Settings**.

## **Proxy Configuration**

If your JFrog environment is behind an HTTP/S proxy:

1. Navigate to **Preferences → Settings → Application → Proxy**.
2. Set the proxy URL under **Proxy**.
3. Ensure 'Proxy Support' is set to **override** or **on**. Alternatively, use the `HTTP_PROXY` and `HTTPS_PROXY` environment variables.

## **Proxy Authorization**

If your proxy server requires credentials:

1. Follow the proxy configuration steps above.
2. Encode your credentials in **Base64** format: `[Username]:[Password]`.
3.  In **settings.json**, add:

    ```json
    "http.proxyAuthorization": "Basic [Encoded credentials]"
    ```
4.  For access token authorization, use:

    ```json
    "http.proxyAuthorization": "Bearer [Access token]"
    ```

## **Downloading External Resources Through Artifactory**

If your machine lacks access to `https://releases.jfrog.io`, configure Artifactory to act as a proxy:

1. Log in to the JFrog Platform UI as an admin.
2. Create a **Remote Repository** with these settings:
   * **Basic Tab:**
     * Package Type: **Generic**
     * Repository Key: **jfrog-releases-repository**
     * URL: [**https://releases.jfrog.io**](https://releases.jfrog.io/)
   * **Advanced Tab:**
     * Uncheck **Store Artifacts Locally**.\
       This reduces storage.
3. In the **JFrog Cursor Extension Settings**, enter the repository key you created.
4. Alternatively, set the `JFROG_IDE_RELEASES_REPO` environment variable with the repository key.

## **Xray Policies and Watches**

You can configure JFrog Cursor Extension to enforce security policies set in Xray:

### **Using a JFrog Project**

1. Create a **JFrog Project** or obtain an existing project key.
2. Create a **Policy** in JFrog Xray.
3. Create a **Watch** in Xray and assign your policy and project to it.
4. Configure the project key in **Extension Settings**.

### **Using Xray Watches:**

1. Create one or more **Watches** in Xray.
2. Configure the Watches in **Extension Settings**.

## **Troubleshooting**

Adjust the log level to `debug`, `info`, `warn`, or `err` in the **Extension Settings** to diagnose issues effectively.
