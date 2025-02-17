# Troubleshooting

## **Viewing Plugin Logs**

The JFrog Plugin logs events in the IDE log files. By default, the **log level** is set to `INFO`.

To increase the log level to `DEBUG`:

1. Navigate to **Help** > **Diagnostic Tools** > **Debug Log Settings...**
2.  In the **Custom Debug Log Configuration** window, add the following line:

    ```plaintext
    plaintextCopyEdit#com.jfrog.ide.idea.log.Logger
    ```
3. To view the IDE log file, go to **Help** > **Show Log in Explorer/Finder/Konqueror/Nautilus** (depending on your OS and IDE version). Learn more here.

## **Reporting Issues**

To report an issue, please open a [GitHub issue](https://github.com/jfrog/jfrog-idea-plugin/issues).

## **Android Studio Support for JCEF**

The JFrog Plugin uses **JCEF (Java Chromium Embedded Framework)** for webview components in the plugin's tool window.

* Most **IntelliJ-based IDEs** include JCEF by default.
* **Android Studio** and some older versions of IntelliJ-based IDEs **do not** include JCEF in their boot runtime, preventing the plugin from loading.

### Enable JCEF support in Android Studio

1. Open the **Choose Boot Runtime for the IDE** dialog.
2. Select a boot runtime that includes **JCEF**.
