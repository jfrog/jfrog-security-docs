# Ignore Violations

Ignore rules allow you to whitelist and ignore security violation rules, in order to filter out unwanted violation noise. For example, you might be running Advanced Scans on a testing repository and don’t want these violations to hinder your testing, or you might have instilled strict actions if a violation is found that is a blocker for continuing your development. You want to ignore the specific violation for the time being.

Ignore rules suppress specific violations so they are not shown in future scans.\
You can ignore by category, scanner, file path, or individual finding, and define the scope by artifact, build, release bundle, or watch.

There are many reasons why you might want to ignore a violation, you can read more about it here [Ignore Rules](https://www.jfrog.com/confluence/display/JFROG/Ignore+Rules).

You can create an ignore rule for Exposures violation using the following REST API:

* [Create Ignore Rule](https://jfrog.com/help/r/xray-rest-apis/create-ignore-rule)

### Ignoring Secrets Violations

You can ignore a Secrets violation by creating a **Secrets Ignore Rule**, which defines the exact conditions under which a secret should be suppressed in future scans. Use this when a secret is a false positive, non-actionable, or intentionally present in a specific location or artifact.

1. Navigate to **Scans List** and open the **Secrets Violation** you want to ignore.
2. Click **Ignore Violation** to open the **Secrets Ignore Rule** dialog.
3. Select what to ignore under **Ignore violation of**:
   * **Specific secret** – Ignore this exact secret value
   * **Specific scanner** – Ignore all violations detected by a specific secret-detection rule
   * **All Secrets violations** – Ignore all secret findings
4. Define the **Location** scope:
   * **In this specific file** – Ignore the secret only when found in the selected file
   * **All files** – Apply the ignore rule across any file
5. Define the:

* **Artifact**:&#x20;
  * **In this specific version**
  * **All versions of**
  * **All Artifacts - Ignore across all Artifacts**
* **Build**
  * **In this specific version**
  * **All versions of**
  * **All Builds**
* **Release Bundle (V2)**:
  * **In this specific version**
  * **All versions of \<bundle>**
  * **All Release Bundle V2s**
