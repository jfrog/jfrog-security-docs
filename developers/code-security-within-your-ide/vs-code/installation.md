# Installation

The extension can be installed from the VS Code Extensions Marketplace. Once installed, a JFrog tab will appear in the activity bar.

## **Connect VS Code to the JFrog Platform**

After installing the JFrog extension:

1. Click on the **JFrog tab** in the activity bar.
2. This will open the **Sign-in page**.
3. Fill in your connection details and click **Sign In** to start using the extension.
   * To use custom URLs for **Artifactory** or **Xray**, click on **Advanced**.
   * You can also choose alternative authentication methods:
     * **Single Sign-On (SSO)**
     * **JFrog CLI's Connection Details**
     * **Environment Variables**

### **Connect Using SSO**

1. On the sign-in page, click **Continue with SSO**.
2. Enter your JFrog platform URL and click **Sign in With SSO**.
3. You will be redirected to your SSO login page.
4. Once authenticated, you will be signed in to VS Code.

### **Connect Using JFrog CLI Connection Details**

If **JFrog CLI** is installed and configured with your JFrog Platform details, a notification will appear on the **Sign-in page**, indicating automatic detection of credentials.
