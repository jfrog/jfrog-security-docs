# Fallback Behavior for Blocked Packages

Define how JFrog Curation should handle package requests when the requested version is blocked by curation policies.

## Configure Fallback Behavior

In the **Fallback Behavior for Blocked Packages** section, configure the setting under **Resolution of Pending Package Updates**:

* **Allow if no blocking policy on remote** – Allows the package if no blocking policies exist on the remote repository.
* **Always block** – Blocks all requests for packages that violate curation policies.
* **Always allow (Not recommended)** – Allows all package requests, even if they violate policies.

## Enable Compliant Version

**Important Notes**:&#x20;

* This feature requires Xray version 3.131.x and above,  Artifactory version 7.125.x and above.
* The remote repository must have cache enabled for the feature to work properly.

\
**Currently supported**: PyPI and NPM (Maven support coming soon).

{% hint style="info" %}
**Limitations**

:exclamation:In the current version of NPM CVS, when a developer requests a locked version, the requested version may be removed by the CVS functionality if it is blocked, resulting in an Etargt error.\
\
:exclamation:Version-based waivers are not supported with CVS. To ensure waivers function correctly, configure waivers using labels rather than explicit package versions.
{% endhint %}

\
**Scope**: Applies globally to all supported ecosystems and cannot be configured per ecosystem.

**Enable compliant version selection:** Toggle this option to return the highest version that complies with your policies instead of blocking the request.

* Works for both direct and transitive dependencies.
* Primarily effective for the Missing in Catalog and Immature policies.
* Developers are not notified when a different version is delivered—this ensures a seamless workflow.
* If a developer requests a specific, locked version that is blocked by policy, the request fails (current behavior).
* A **Compliant Version Log** is being developed to let developers see why they received a different version.

**How Compliant Version Selection Works**

When a requested package version fails a Curation policy (for example, **block immature** or **missing in Catalog**), this automated process occurs:

1. **Request** – A developer requests a package version, for example, **3.141**.
2. **Version range** – Artifactory retrieves all versions that satisfy the dependency tree (e.g., 3.08–3.141).
3. **Policy check** – Curation inspects these versions and finds the first that passes all policies—**3.13** in this example.
4. **Return compliant version** – Curation returns **3.13** to Artifactory, which downloads it.
5. **Audit log** – The Curation audit log records **3.13** as **Approved**, allowing the developer to continue without interruption.
6. **Later updates** – If the originally requested version (3.141) is later updated in the catalog and passes policy, the next request for it will succeed.

**Benefits**

* **Minimized Development Disruptions** – Prevents failed requests by automatically returning compliant versions.
* **Smarter Dependency Resolution** – Ensures large projects and transitive dependencies resolve to secure and policy-compliant versions.
