# Ignore Violations

Ignore rules allow you to whitelist and ignore security violation rules, in order to filter out unwanted violation noise. For example, you might be running Advanced Scans on a testing repository and don’t want these violations to hinder your testing, or you might have instilled strict actions if a violation is found that is a blocker for continuing your development. You want to ignore the specific violation for the time being.

There are many reasons why you might want to ignore a violation, you can read more about it here [Ignore Rules](https://www.jfrog.com/confluence/display/JFROG/Ignore+Rules).

**Ignoring an Exposures Violation**:

1. In Scans List, select the repository and artifact you want to view violations for.
2. In the **Policy Violations** tab, select the Exposures violation you want to ignore. \
   Exposures violations ID is indicated with an EXP prefix.
3. Click on the menu on the right side of the violation, and select **Ignore Violation**.\
   The create Exposure Ignore Rule window appears.
4. Choose a combination of the ignore criteria depending on your needs.

| Ignore Rule                                  | Description                                                                                                                                                                        |
| -------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Based on the Exposure**                    |                                                                                                                                                                                    |
| Exposure Scanner                             | Ignores all violations for the specific scanner. Take note, if this is checked, all exposure violations related to this scanner will be ignored.                                   |
| For any Exposure of the following categories | Ignores all violations of the specific exposures category. If all categories are selected, no violations will be created for Exposures for the specified scope in the ignore rule. |
| **Based on file path**                       |                                                                                                                                                                                    |
| Specific File path                           | The rule will be applied on the specific path within the specified artifact scope.                                                                                                 |
| For any file                                 | The rule will be applied for any file path within the specified artifact scope.                                                                                                    |
| **Based on Artifact**                        |                                                                                                                                                                                    |
| Artifact name selected current version       | The rule will be applied on the specific artifact for that specific version of the Docker image.                                                                                   |
| Artifact name selected any version           | The rule will be applied on the specific artifact for all versions of the Docker image.                                                                                            |
| For any Artifact                             | The rule will be applied on all artifacts that contain that violation in the Docker image.                                                                                         |

Managing, deleting and other Ignore Rules related actions are described in [Ignore Rules](https://jfrog.com/help/access?ft:originId=UUID-dcb8d4a3-bb33-8f0f-7c8b-bc917b82cb9d\&ft:sourceId=pal).

## **Ignoring Secrets Violations**

Ignore rules helps **reduce noise** by filtering out **false positives or non-actionable violations** in secret detection results.

1. Navigate to **Scans List** and locate the reported **Secrets Violation**.
2. Open the violation details and review the flagged issue.
3. Click **Ignore Violation** and configure an ignore rule using one of the following criteria:
   * **Based on Secret Type** – Ignore a specific type of secret (e.g., API Key, SSH Private Key).
   * **Based on File Path** – Ignore secrets found in a specific file or directory.
   * **Based on Artifact Name** – Ignore secrets detected in a particular artifact version.
4. Save the ignore rule to apply it to future scans.
