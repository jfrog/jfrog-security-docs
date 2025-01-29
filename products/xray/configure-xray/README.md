# Configure Xray

Key configuration tasks required for JFrog Xray:

1. **Database Synchronization**:
   * Xray syncs with JFrog’s global vulnerability database.
   * Available in **Online** (automatic) and **Offline** (manual sync) modes.
2.  **Indexing Xray Resources**

    * Xray does **not** automatically index all resources; users must select:
      * **Repositories**
      * **Builds**
      * **Release Bundles**
    * Allows fine-tuning indexing rules, such as **artifact age-based indexing**.

    **Data Retention and Storage**

    * **Indexed resources retention period**:
      * Default: **90 days** (configurable via system YAML).
      * Artifacts downloaded reset retention period.
3. **Configure Scans**
4. **Create Watches and Policies ( Optional but recommended)**
   * Policies define **security and compliance rules**.
   * Watches monitor **repositories, builds, and release bundles**.
   * Violations trigger **alerts, enforcement actions, or CI/CD failures**.

