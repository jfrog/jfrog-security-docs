# Frogbot Offline

By default, Frogbot downloads its executables and other required tools directly from[ JFrog’s public releases repository](https://releases.jfrog.io). If your Frogbot deployment runs in an environment without internet access, or if you want Frogbot to download resources via an Artifactory instance, you can configure it to download these resources from a private Artifactory instance.

Follow the steps below to set up an Artifactory repository as the source for Frogbot downloads:

## Set Artifactory to be the Frogbot Executable Source

### Step 1: Create a Designated Repository in Artifactory

1. Under Administration, navigate to Repositories and select Create a Repository.&#x20;
2. From the drop-down menu, select Remote. \
   The Select Package Type window opens.
3. Select Generic.\
   The New Remote Repository window opens.
4. Under the Basic tab, set the following URL address: \
   `https://releases.jfrog.io`
5. Under the Advanced tab, uncheck the Store Artifacts Locally box. \
   This reduces storage.

### Step 2: Configure Frogbot to Use the New Repository

1. Go to Frogbot and navigate to Configuration
2. Set the `JF_RELEASES_REPO` variable to be the Repository Key of the remote repository you created in step 1.
