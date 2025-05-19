# Installation

This section provides instructions for installing, configuring, and using the JFrog Visual Studio Extension.

## **Supported Visual Studio Versions**

Two extensions are available in the Visual Studio Marketplace, each supporting different versions:

* **Visual Studio 2022** – [JFrogV2](https://marketplace.visualstudio.com/items?itemName=JFrog.JFrogV2)
* **Visual Studio 2017 and 2019** – [JFrog](https://marketplace.visualstudio.com/items?itemName=JFrog.JFrog)

## **Installing the JFrog Visual Studio Extension**

1. Open the **terminal window**.
2. Run the **nuget** command. If the command is not recognized, add `nuget.exe` to the **PATH** environment variable.
3. If your projects use **NPM**, run the **npm** command. If the command is not recognized, add `npm.exe` to the **PATH** environment variable.
4. Open **Visual Studio**.
5. Navigate to **Tools → Extensions and Updates**.
6. Search for **JFrog**.
7. Click **Download** and complete the installation.
8. Restart **Visual Studio** after installation.

## **Configuring the JFrog Visual Studio Extension**

Once installed, configure the extension to connect to **JFrog Xray**:

1. Open **Visual Studio**.
2. Go to **Tools → Options → JFrog → JFrog Xray**.
3. Enter your **JFrog Platform URL** and **login credentials**.
4. Click **Test Connection** to verify the setup.
