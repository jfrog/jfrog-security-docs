# Comparing Build Versions for Security Diff

This feature allows users to compare two versions of a scanned build and see the security differences between them, such as any new CVEs that have been introduced. With this feature you will be able to:

* Compare security posture between two build versions.
* Identify new CVEs introduced in the newer version.
* Get detailed information on each CVE including severity, description, and remediation.
* Proactively detect security regressions between build versions.
* Quickly identify and mitigate newly introduced vulnerabilities.

You can compare current build version against any previous version that was indexed by Xray.

**To compare build versions:**

1. In **Scans List**, navigate to the **Builds** tab.
2.  Select the Build, and in the Build Versions list, from the three dot menu on the right, select **Compare to Version**.

    [![comparetoversion.png](https://jfrog.com/help/api/khub/maps/6nte66fuu2ZQMB2dfriysg/resources/AsmbghnIVlWrDOsF_xqbyA-6nte66fuu2ZQMB2dfriysg/content?v=cf764666713169da)](https://jfrog.com/help/viewer/attachment/6nte66fuu2ZQMB2dfriysg/AsmbghnIVlWrDOsF_xqbyA-6nte66fuu2ZQMB2dfriysg)

    The compare dialog appears.
3.  Select the version you want to compare from the drop-down.

    [![comparedialog.png](https://jfrog.com/help/api/khub/maps/6nte66fuu2ZQMB2dfriysg/resources/LRWHB_BzHIrF~Q8iR6m6_w-6nte66fuu2ZQMB2dfriysg/content?v=11247815211d9f16)](https://jfrog.com/help/viewer/attachment/6nte66fuu2ZQMB2dfriysg/LRWHB_BzHIrF~Q8iR6m6_w-6nte66fuu2ZQMB2dfriysg)

The diff view appears. It will display the following:

*   Summary of security changes between the versions.

    CVEs that exist in one version, but not the other, are indicated as **Added.** CVEs that were fixed, are marked as **Resolved**.

    [![diffview.png](https://jfrog.com/help/api/khub/maps/6nte66fuu2ZQMB2dfriysg/resources/mNZkf6z~BIMe8JE~WY_VjQ-6nte66fuu2ZQMB2dfriysg/content?v=7a88c1a93668a1ee)](https://jfrog.com/help/viewer/attachment/6nte66fuu2ZQMB2dfriysg/mNZkf6z~BIMe8JE~WY_VjQ-6nte66fuu2ZQMB2dfriysg)
*   Details on each CVE are displayed in the right pane when you click on the CVE.

    [![CVEdetailsdiff.png](https://jfrog.com/help/api/khub/maps/6nte66fuu2ZQMB2dfriysg/resources/Fuf2l7WmIoOlUk0NiNZ2xA-6nte66fuu2ZQMB2dfriysg/content?v=c804efe54d95f36c)](https://jfrog.com/help/viewer/attachment/6nte66fuu2ZQMB2dfriysg/Fuf2l7WmIoOlUk0NiNZ2xA-6nte66fuu2ZQMB2dfriysg)
* CVEs that are not affected are hidden. Click **View Unchanged CVEs** on the bottom to view the full list.
* Filter the view by the selecting/deselecting **Added/Resolved** checkboxes.\
