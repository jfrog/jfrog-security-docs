# How to Manage Virtual Repository Behavior and Curation in JFrog Xray

This guide explains the expected behavior of virtual repositories in JFrog Artifactory when handling **curated package types**. It also outlines best practices for managing virtual repositories with **curation policies** to ensure compliance and security.

Virtual repositories can contain curated remote repositories or smart repositories that point to curated repositories. This guide helps administrators configure virtual repositories correctly to avoid unexpected behavior.

### **Understanding Virtual Repository Behavior**

When a package that violates the **curation policy** is requested but does not exist in local repositories or cache, Artifactory behaves as follows:

#### **Resolution Order in Artifactory**

1. **Local repositories** – First attempt to resolve artifacts.
2. **Cache** – If not found locally, Artifactory searches in the cache.
3. **Remote repositories** – If still unresolved, Artifactory queries the remote repositories based on the configuration order.

#### **Behavior for Different Virtual Repository Configurations**

| **Scenario**                                                     | **Expected Behavior**                                                                                                                                                                                                                                                                                                                                                                                    | **Response Code**                                      |
| ---------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------ |
| **One curated remote repository**                                | Artifactory tries to resolve the artifact from this repository, but it gets **blocked** due to the curation policy.                                                                                                                                                                                                                                                                                      | **403 (Blocked)**                                      |
| **One smart repository linked to a curated remote**              | Artifactory tries to resolve from this smart repository, but it gets **blocked** due to curation policy.                                                                                                                                                                                                                                                                                                 | **403 (Blocked)**                                      |
| **Multiple remote repositories, including at least one curated** | <p>Artifactory follows the order of remotes:<br>- If an artifact is found in a remote repository and it is not blocked, Artifactory resolves and returns it (<strong>200 OK</strong>).<br>- If the artifact does not exist (<strong>404</strong>), Artifactory moves to the next remote.<br>- If the artifact is blocked by the curation policy, Artifactory returns <strong>403 (Blocked)</strong>.</p> | **403 (Blocked)** / **200 (OK)** / **404 (Not Found)** |

For a full matrix of supported package types, refer to:\
➡ [**JFrog Curation Support Matrix**](https://jfrog.com/help/r/jfrog-curation/curation-support-matrix)

***

### **Best Practices for Virtual Repository Curation**

To optimize your virtual repository behavior and prevent security risks:

✅ **Limit Remote Repositories**

* Have **only one remote repository** per external source in the virtual repository.
* Example: If using **Maven Central**, ensure only one Maven remote repository exists in the virtual repository.

✅ **Order of Repositories**

* The **curated repository should be the last** in the resolution order.
* If placed earlier, it may block the package, while a later repository might still resolve it—leading to inconsistent behavior.

✅ **Handling Blocked Packages**

* If a package is blocked (403) due to curation policy, Artifactory will **continue searching** in other remotes.
* If no remotes resolve the artifact, a **404 Not Found** response is returned.

✅ **Security Considerations**

* **Avoid backdoor access to the internet** by ensuring that only one remote repository is configured.
* Ensure **all remote repositories are curated** to prevent unauthorized package downloads.

***

### **Troubleshooting**

| **Issue**                     | **Possible Cause**                                                  | **Solution**                                                               |
| ----------------------------- | ------------------------------------------------------------------- | -------------------------------------------------------------------------- |
| Package is blocked (403)      | It violates the curation policy.                                    | Ensure the package meets curation requirements or adjust repository rules. |
| Package resolves unexpectedly | Curated repository is not the last in the virtual repository order. | Adjust the order to place curated repositories last.                       |
| 404 Not Found error           | No repository contains the requested package.                       | Check repository configuration and cache settings.                         |
