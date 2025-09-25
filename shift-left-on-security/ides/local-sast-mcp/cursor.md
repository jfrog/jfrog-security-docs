# Cursor

### Before You Begin

* Install the latest JFrog CLI
*   Configure your Artifactory instance with JAS entitlements using:

    ```sh
    jf c add
    ```

#### Installing JFrog SAST MCP

1. Open a project of interest in **Cursor**.
2. Go to `Command Palette → Open MCP Settings`.
3. Click **New MCP Server**.
4.  Edit the opened JSON file to look like this:

    ```json
    jsonCopyEdit{
      "mcpServers": {
        "jfrog-mcp": {
          "command": "jf",
          "args": ["source-mcp", "."]
        }
      }
    }
    ```
5. Go to **Cursor Settings** > **MCP Tools**, and confirm the new tools appear (may take time to load for large projects)
6. (Optional) Once MCP is set up, try prompting the AI assistant with:

* “Do I have SAST vulnerabilities in my code?”
* “Can you help me fix them?”

### Troubleshooting

* If something isn’t working as expected:

1. Open the **Command Palette** > **Show Output Channels**.
2. Select the relevant MCP output **MCP: {server name}**.
3. In the AI assistant chat, unfold the **MCP tool call** to view:
   * Tool input
   * Tool output
