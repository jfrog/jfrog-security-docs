# How to Prevent the Use of Deprecated or Outdated Packages in Development

**Use Case:**

A DevOps team wants to ensure that only actively maintained and secure package versions are used, preventing developers from relying on outdated or unsupported dependencies.

**Workflow Steps:**

1. **Enable Curation for Software Package Repositories**
   * Navigate to **Curation > Curated Repositories**.
   * Enable curation for repositories with long-term dependencies (e.g., npm, Maven, NuGet, PyPI).
2. **Create a Package Age Policy**
   * Go to **Curation > Policies Management** and create a new policy: **Enforce Up-to-Date Dependencies**.
   * Under **Policy Scope**, apply the policy to all curated repositories.
3. **Define an Operational Condition**
   * Select a condition that prevents outdated package usage:
     * **Package Version is Aged (No Newer Version Identified)**: Blocks versions older than two years if no newer version exists.
     * **Package Version is Aged (New Version Available)**: Blocks versions older than six months when a newer version exists.
     * **Package Version is Immature**: Prevents using versions released less than a specified time ago.
4. **Select an Action & Notifications**
   * Choose **Block** to enforce the restriction.
   * Enable **Email notifications** to alert the requester and DevOps team when a package is blocked.
5. **Validate Package Version Control**
   * Attempt to install an outdated package.
   * Confirm the request is blocked with an alert explaining why the version is restricted.
   * Review package metadata in **Audit Events**.
