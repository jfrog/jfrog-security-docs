# Strengthening Runtime Trust Through Image Verification

## How to Strengthen Runtime Trust Through Image Verification

In this article, we will guide you on how to use the "Untrusted Registry" and "Integrity Violation" quick filters in JFrog Runtime to filter out unwanted images and ensure that only trusted sources are displayed in your results.

Ensuring the integrity and trustworthiness of container images is crucial for maintaining a secure runtime environment. JFrog Runtime provides quick filters that allow you to easily identify and exclude images from untrusted sources or those that have integrity violations.

## Step 1: Apply the Quick Filters

1. In **Runtime** > **Live Assessment**&#x20;
2. **Untrusted Registry Filter** :
   * Locate the **Filters** panel on the left side of the Live Assessment page.
   * Find the **Untrusted Registry** quick filter option.
   * Check the box next to **Untrusted Registry** . This filter will display only those images that originate from registries deemed untrusted by the system.
3. **Integrity Violation Filter** :
   * In the same **Filters** panel, look for the **Integrity Violation** quick filter option.
   * Check the box next to **Integrity Violation** . This filter will show images that have been flagged for integrity violations, indicating discrepancies between the stored image and the running instance.

## Step 3: Review Filtered Results

* After applying the filters, the results table will refresh to display only the images that meet the criteria of being from untrusted registries or having integrity violations.
* Review the filtered results carefully. You can click on each image to get more details about its source, tags, and any associated vulnerabilities.

## Step 4: Take Action

* Based on the filtered results, you can decide to:
  * Remove or quarantine untrusted images from your environment.
  * Investigate integrity violations further to determine the cause and necessary remediation steps.
