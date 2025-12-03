# How to Manage “Package Pending Catalog” Events in JFrog Curation

**Use Case:**

You want to ensure that when a package is newly published (or pulled) but not yet cataloged, your build pipelines, governance, and security workflows handle this transient state appropriately — either by waiting, failing fast, or applying fallback logic.

**Workflow Steps**

There are two primary resolutions for handling packages in the Pending Catalog state:

1. **Security-Oriented Preference**:
   * For organizations that prioritize security, it is advisable to instruct developers to wait at least two hours for the new package to be scanned. This approach allows Curation to automatically curate and ensure that the latest package updates undergo thorough validation.
   * As an alternative, developers may opt to utilize the lock version of the package until the newest version is available. This strategy ensures teams can continue operations without compromising security.
2. **High-Velocity Organization Preference**:
   * Organizations with a fast-paced development environment may choose a more aggressive approach. In this case, an administrative setting can be configured to prevent blocks on packages pending catalog update.
   * To enable this, navigate to **Curation** **Settings > General** and switch the **Resolution of Pending Package Updates** to **Always Allow**. This configuration allows any packages in the pending state to automatically enter the organization’s catalog, providing more flexibility and speed for development teams.
