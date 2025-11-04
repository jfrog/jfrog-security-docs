# View SBOM in GitHub Dependency Graph

Frogbot generates an SBOM for each scanned repository and publishes it to the repository’s Dependency graph in GitHub. This lets developers review direct and transitive dependencies within their native GitHub workflow.

It is essential that you&#x20;

**Before You Begin**

* Requires JFrog Advanced Security license
* Enable GitHub [Dependency Graph](https://docs.github.com/en/code-security/supply-chain-security/understanding-your-software-supply-chain/about-the-dependency-graph) for the repositories you wish to publish SBOMs to
* To disable automatic SBOM results from being uploaded to GitHub, [set](../configure-frogbot/frogbot-optional-configuration-parameters.md) the `JF_UPLOAD_SBOM_TO_VCS` parameter to `false`

**Procedure**

1. In GitHub, open the repository scanned by Frogbot and click **Insights**.
2. In the left pane, select **Dependency graph**.
3. Open the **SBOM** view (if available) to see the latest SBOM uploaded by Frogbot, or review the dependency list populated from the SBOM.
4. Click a dependency to view details such as version, relationships, and metadata.
