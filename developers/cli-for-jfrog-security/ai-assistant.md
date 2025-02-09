# AI Assistant

The **JFrog CLI AI Command Assistant** simplifies your workflow by converting natural language requests into precise JFrog CLI commands.

Just describe the action you want to perform—uploading artifacts, managing repositories, scanning code, or other CLI tasks—and the assistant will generate the appropriate command with all necessary parameters.

Before You Begin:

* The AI assistant supports Artifactory and Xray commands

Key features:

* **Natural Language Processing:** No need to remember complex CLI syntax.
* **Efficiency & Accuracy:** Quickly generate precise commands.
* **Session-Based Queries:** Each request is handled individually, with no chat history maintained.

## **How to Use the JFrog CLI AI Command Assistant**

1. **Open Your Terminal**\
   Ensure JFrog CLI is installed and properly configured in your terminal session.
2.  **Check Supported Version**\
    The AI Assistant is available from JFrog CLI version 2.69 and above. To verify your version, run:

    ```
    jf --version
    ```
3.  **Launch the AI Assistant**\
    Initiate the assistant with the following command:

    ```
    jf how
    ```
4.  **Enter Your Request**\
    After running the command, you’ll see a prompt:

    ```
    Your request:
    ```

    Describe your desired action in plain language. For example:

    ```
    Your request: How do I upload all files in the 'build' directory to the 'my-repo' repository?
    ```
5.  **Receive the Generated Command**\
    The assistant will process your request and return the corresponding CLI command, complete with all necessary parameters:

    ```
    jf rt u build/ my-repo/
    ```
6. **Execute or Refine**\
   Copy the generated command and run it in your terminal. If adjustments are needed, refine your request and try again.
