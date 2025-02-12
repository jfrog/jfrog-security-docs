# Offline Setup for Frogbot Executables

By default, Frogbot downloads its executables and other required tools directly from[ JFrog’s public releases repository](https://releases.jfrog.io). If your Frogbot deployment runs in an environment without internet access, you can configure it to download these resources from a private Artifactory instance instead.

Follow the steps below to set up an Artifactory repository as the source for Frogbot downloads:

### Steps for Setting Up Artifactory as the Frogbot Executable Source

1. Login to Artifactory:
2.
   * Log in to your Artifactory UI with a user account that has admin credentials.
3. Create a Remote Repository:
4.
   * Go to the Artifactory Admin panel and create a new Remote Repository with the following settings:
5. Repository Configuration
6.
   * Under the Basic tab:
   *
     * Package Type: Select Generic.
     * URL: Set this to https://releases.jfrog.io, which is the source of Frogbot’s releases.
   * Under the Advanced tab:
   *
     * Store Artifacts Locally: Uncheck this option. This will prevent Artifactory from storing a local copy, reducing storage needs.
7. Configure Frogbot to Use the New Repository:
8.
   * In your Frogbot setup configuration, set the JF\_RELEASES\_REPO variable to the Repository Key of the remote repository you created in step 2.

yaml\
Copy code\
JF\_RELEASES\_REPO: "\<Your\_Repository\_Key>"

5. Replace \<Your\_Repository\_Key> with the actual repository key from your Artifactory configuration.

\
\


* Viewing Results
*
  * Viewing results in Xray

TBD Lina

* Viewing results in Github Advanced Security

TBD AsafC

**9. Best Practices - This section will  be complete once XSC is in Xray**

* Security Best Practices for CI/CD Integration
* Reducing False Positives with Contextual Analysis
* Keeping Dependencies Up-to-date
* Monitoring and Managing Vulnerabilities
