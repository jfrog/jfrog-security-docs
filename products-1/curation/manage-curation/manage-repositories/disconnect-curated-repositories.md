# Disconnect Curated Repositories

To disconnect a remote repository from the JFrog Curation service, follow these steps:

1. **Access the Curated Repositories Table**:
   * Navigate to the **Curated Repositories** section within your JFrog Platform.
2. **Disable Curation for the Desired Repository**:
   * Locate the specific remote repository you wish to disconnect.
   * Click the toggle switch next to the repository's name to turn it off.
3. **Confirm the Disconnection**:
   * A confirmation window will appear, listing the policies that will no longer apply to the repository once it's disconnected.
   * Review the information carefully.
   * Click **Yes, Disable** to confirm and finalize the disconnection.

**Important Note**: After disconnecting, the repository will no longer be governed by the curation policies previously assigned to it. If a policy was exclusively applied to this repository, that policy will become inactive.

By following these steps, you can effectively manage which repositories are under the purview of JFrog Curation, ensuring that only the desired repositories are subject to curation policies.

{% hint style="info" %}
If there is a policy that applies to the disabled repository only, that policy becomes inactive.
{% endhint %}

