# Quick Start

## **Enabling Advanced Scans and Creating Security Policies**

### **Enable Advanced Scans**

Advanced Scans must be configured per repository, and the repository must be indexed by Xray. For more details on indexing resources, see the _Indexing Resources_ guide. Note that Advanced Scans are applied only to newly scanned artifacts, not existing indexed artifacts. However, you can run contextual analysis and exposure scans on existing artifacts.

1. In **Classic Navigation**, go to the Administration module > Xray Settings > General > Indexed Resources.
2. In **New Navigation**, go to the Administration module > Xray Settings > Indexed Resources.
3. Select the repository or build and click **Configure**.
4. Choose the categories you want to enable.

## **Create a Security Policy with Advanced Scan Rules**

Security policies enable you to define rules based on security criteria, with automatic actions triggered according to your needs. These policies are enforced when applied to Xray Watches. For guidance on creating policies, see _Creating Xray Policies and Rules_.

It is recommended to create policies for a focused list of violations based on your security criteria. You can create policies specific to exposures and contextual analysis rules. A violation is issued when the criteria set in the policy are met. Violations can be viewed on either the _Scans List_ or _Watch Violations_ pages.

###
