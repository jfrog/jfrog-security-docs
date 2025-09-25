# Visual Studio Code

### Before You Begin

* Install the latest JFrog CLI
*   Configure your Artifactory instance with JAS entitlements enabled using:

    ```sh
    jf c add
    ```

### Installation

1. Open the project you want to use MCP with.
2. Go to `View → Command Palette`, and select **MCP: Add Server**.
3. Choose `Command (stdio)`.
4.  For **Command to run**, enter:

    ```sh
    jf source-mcp ${workspaceFolder}
    ```
5. Set the **Server ID** (e.g., `JFrog Source MCP`).
6. Choose **Workspace Settings**.
7. Open the **Copilot Chat** tab, and enable **Agent Mode**.
8. Click **Select Tools** and confirm that JFrog tools appear (initial indexing may take time in large projects).
9. (Optional) Once MCP is set up, try prompting Copilot with:
   * “Do I have SAST vulnerabilities in my code?”
   * “Can you help me fix them?”

### Troubleshooting

* If something isn’t working as expected:

1. Open the **Command Palette** > **Show Output Channels**.
2. Select the relevant MCP output **MCP: {server name}**.
3. In Copilot Chat, unfold the **MCP tool call** to view:
   * Tool input
   * Tool output
