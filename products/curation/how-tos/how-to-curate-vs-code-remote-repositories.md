# How to Curate VS Code Remote Repositories

**Use Case**

JFrog Curation now supports curating **VS Code remote repositories** created using the **Artifactory AI Editor Extensions**.\
This capability allows organizations to apply all standard curation controls, such as policies, conditions, and repository connections, to VS Code extensions fetched through supported remote repositories.

Workflow Steps

1. **Create a VS Code Remote Repository**\
   Before you can curate VS Code repositories, create a remote repository for AI Editor Extensions.\
   Follow the setup instructions in the [AI Editor Extension Repositories](https://jfrog.com/help/r/jfrog-artifactory-documentation/ai-editor-extension-repositories) documentation.
2. **Verify Environment Compatibility**\
   Ensure your environment meets the following requirements:
   * **Artifactory Version:** 7.125.6 or later&#x20;
   * **Xray Version:** 3.131.15 or later&#x20;
   * **Subscription:** **JFrog** **Ultimate or Unified Security Bundle**
3. **Connect the Remote Repository in Curation**\
   In the JFrog Platform, go to **Administration > Curation > Remote Repositories**, and connect your newly created VS Code repository.\
   Once connected, it behaves like any other supported package type in Curation.
4. **Apply Curation Policies and Conditions**
   * Create curation policies and add conditions as needed.
   * The AIEditorExtensions package type supports **all condition types** available in Curation.
   * Apply the relevant actions (e.g., Block, Allow, Notify) per policy.
5.  **Monitor Audit Events**\
    After applying policies, audit events for VS Code packages will appear under **Application > Curation > Audit Events**.

    > ⚠️ **Note:**
    >
    > * The VS Code IDE plugin acts as an anonymous requester, so the user field appears as unknown in audit events.
    > * Because the IDE plugin retries downloads multiple times, you may see several repeated block entries in the audit logs. This is expected behavior and not a system issue.
    > * As requests are anonymous, email notifications are not sent for these blocks.
