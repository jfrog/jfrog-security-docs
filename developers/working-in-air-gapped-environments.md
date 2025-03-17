# Working in Air-Gapped Environments

By default, JFrog Shiftleft utilities (IDE, CLI, and Frogbot) download JFrog engines directly from[ JFrog’s public releases repository](https://releases.jfrog.io). If your environment is without internet access, you can configure it to download these resources from a private Artifactory instance.

The instance should be configured with either:

* Generic Remote Repository: a proxy to `https://releases.jfrog.io`
* Generic Local Repository

## Configure a Generic Remote Repository in Artifactory

1. Under Administration, navigate to Repositories and select Create a Repository.&#x20;
2. From the drop-down menu, select **Remote**.&#x20;

&#x20;   The Select Package Type window opens.

1. Select **Generic**.\
   The New Remote Repository window opens.
2. Configure the desired **Repository Key - This should be used in the shift left utilities**
3. Under the Basic tab, set the following URL address: \
   `https://releases.jfrog.io`
4. Under the Advanced tab, uncheck the Store Artifacts Locally box. \
   This reduces storage.

## Configure a Generic Local Repository in Artifactory

* Under Administration, navigate to Repositories and select Create a Repository.&#x20;
* From the drop-down menu, select **Local**. \
  The Select Package Type window opens.
* Select **Generic**.\
  The New Remote Repository window opens.
* Configure the desired **Repository Key - This should be used in the shift left utilities**
