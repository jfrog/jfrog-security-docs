# Enable Pass-Through for Specific Repositories



JFrog Curation's Pass-Through feature allows certain package managers, like Maven, to download and audit packages that would typically be blocked due to policy violations without storing them in Artifactory. This ensures that while developers can perform necessary audits, the violating packages do not reside in the repository, maintaining security and compliance.

**When to Enable Curation Pass-Through**

Enable this feature if your development workflow involves package managers or build systems that require access to all dependencies, including those that violate curation policies, for audit purposes. Currently, Maven is a primary example of such a package manager.

**Supported Deployment Models**

Curation Pass-Through is compatible with the following deployment configurations:

* **Direct Curated Remote Repository Communication**: The remote repository communicates directly with the Curation service.
* **Curated Remote Repository Communication via Smart Remote**: The remote repository connects to the Curation service through a Smart Remote setup.

**Steps to Enable Curation Pass-Through**

Pass-through is enabled by default when you connect the repository type; you can disable this in the Remote repository configuration.&#x20;

1. **Access Artifactory**:
   * Log in to your Artifactory instance.
2. **Navigate to the Desired Remote Repository**:
   * Go to the **Repositories** section.
   * Select the remote repository you wish to configure for pass-through.
3. **Configure Pass-Through**:
   * Scroll to the bottom of the repository's settings page.
   * Locate the **Enable Curation Pass-Through** option.
   * Toggle the switch to **On of OFF** acording to your needs.

**Additional Configuration for Smart Remote Repositories**

If your setup includes a Smart Remote repository that connects to a curated remote:

1. **Access the Smart Remote Repository Settings**:
   * Log in to your Artifactory instance.
   * Navigate to the **Repositories** section.
   * Select the Smart Remote repository in question.
2. **Enable User Context for Curation**:
   * Within the repository settings, find the **Add User Context for Curation** option.
   * Ensure this option is enabled to support pass-through functionality.

**Important Considerations**

* **Security**: While Curation Pass-Through allows the download of packages that violate policies for auditing purposes, these packages **are not stored in Artifactory,** ensuring they don't inadvertently become part of your development or production environments.
* **Compatibility**: Currently, Maven is identified as a build system that requires this pass-through capability for effective auditing.

