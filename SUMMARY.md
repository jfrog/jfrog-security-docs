# Table of contents

* [What is JFrog Security?](README.md)
* [Products](products/README.md)
  * [Curation](products/curation/README.md)
    * [Supported Technologies](products/curation/supported-technologies.md)
    * [Features and Capabilities](products/curation/features-and-capabilities.md)
    * [Configure Curation](products/curation/configure-curation/README.md)
      * [Configure Curation for Self Hosted](products/curation/configure-curation/configure-curation-for-self-hosted.md)
      * [Set User Roles and Permissions](products/curation/configure-curation/set-user-roles-and-permissions.md)
      * [General ](products/curation/configure-curation/general.md)
      * [Configure Repositories](products/curation/configure-curation/configure-repositories/README.md)
        * [Connect Remote Repositories to Curation](products/curation/configure-curation/configure-repositories/connect-remote-repositories-to-curation.md)
        * [Enable Pass-Through for Specific Repositories](products/curation/configure-curation/configure-repositories/enable-pass-through-for-specific-repositories.md)
      * [Create Policies](products/curation/configure-curation/create-policies/README.md)
        * [List of Available Conditions](products/curation/configure-curation/create-policies/list-of-available-conditions.md)
      * [Create Custom Conditions](products/curation/configure-curation/create-custom-conditions.md)
    * [Manage Curation](products/curation/manage-curation/README.md)
      * [Manage Repositories](products/curation/manage-curation/manage-repositories.md)
      * [View the Active Policies for a Repository](products/curation/manage-curation/view-the-active-policies-for-a-repository.md)
      * [Manage Policies](products/curation/manage-curation/manage-policies.md)
      * [Manage Waivers](products/curation/manage-curation/manage-waivers.md)
      * [Audit Events](products/curation/manage-curation/audit-events.md)
    * [Curation How-Tos](products/curation/curation-how-tos/README.md)
      * [How to Block Malicious or Vulnerable Packages from Entering the Repository](products/curation/curation-how-tos/how-to-block-malicious-or-vulnerable-packages-from-entering-the-repository.md)
      * [How to Ensure Only Open-Source Packages with Approved Licenses Are Used](products/curation/curation-how-tos/how-to-ensure-only-open-source-packages-with-approved-licenses-are-used.md)
      * [How to Prevent the Use of Deprecated or Outdated Packages in Development](products/curation/curation-how-tos/how-to-prevent-the-use-of-deprecated-or-outdated-packages-in-development.md)
      * [How to Use JFrog Curation as a Developer with the JFrog CLI](products/curation/curation-how-tos/how-to-use-jfrog-curation-as-a-developer-with-the-jfrog-cli.md)
      * [How to Utilize JFrog Catalog for Curation](products/curation/curation-how-tos/how-to-utilize-jfrog-catalog-for-curation.md)
      * [How to Manage Virtual Repository Behavior and Curation in JFrog Xray](products/curation/curation-how-tos/how-to-manage-virtual-repository-behavior-and-curation-in-jfrog-xray.md)
  * [Xray](products/xray/README.md)
    * [Xray Supported Technologies](products/xray/xray-supported-technologies.md)
    * [Xray Features and Capabilities](products/xray/xray-features-and-capabilities/README.md)
      * [SCA](products/xray/xray-features-and-capabilities/sca/README.md)
        * [Security](products/xray/xray-features-and-capabilities/sca/security/README.md)
          * [JFrog Security Research](products/xray/xray-features-and-capabilities/sca/security/jfrog-security-research.md)
          * [Malicious Package Detection](products/xray/xray-features-and-capabilities/sca/security/malicious-package-detection.md)
        * [Legal](products/xray/xray-features-and-capabilities/sca/legal.md)
        * [Operational Risk](products/xray/xray-features-and-capabilities/sca/operational-risk.md)
        * [SBOM](products/xray/xray-features-and-capabilities/sca/sbom/README.md)
          * [SBOM Import](products/xray/xray-features-and-capabilities/sca/sbom/sbom-import.md)
          * [SBOM Export](products/xray/xray-features-and-capabilities/sca/sbom/sbom-export.md)
      * [Policies in JFrog Xray](products/xray/xray-features-and-capabilities/sdlc-policy-mangement/README.md)
        * [Watches in JFrog Xray](products/xray/xray-features-and-capabilities/sdlc-policy-mangement/watches.md)
        * [Ignoring Violations in JFrog Xray: Understanding Ignore Rules](products/xray/xray-features-and-capabilities/sdlc-policy-mangement/ignore-rules.md)
      * [Export Scan Results](products/xray/xray-features-and-capabilities/export-scan-results.md)
      * [Understanding and Analyzing Xray Scan Results](products/xray/xray-features-and-capabilities/understanding-and-analyzing-xray-scan-results/README.md)
        * [Builds](products/xray/xray-features-and-capabilities/understanding-and-analyzing-xray-scan-results/builds/README.md)
          * [Builds Security Overview](products/xray/xray-features-and-capabilities/understanding-and-analyzing-xray-scan-results/builds/builds-security-overview.md)
          * [Comparing Build Versions](products/xray/xray-features-and-capabilities/understanding-and-analyzing-xray-scan-results/builds/comparing-build-versions.md)
        * [Violations Handling and Notifications](products/xray/xray-features-and-capabilities/understanding-and-analyzing-xray-scan-results/violations-handling-and-notifications/README.md)
          * [Jira Integration](products/xray/xray-features-and-capabilities/understanding-and-analyzing-xray-scan-results/violations-handling-and-notifications/jira-integration/README.md)
            * [Setup Xray Jira Integration](products/xray/xray-features-and-capabilities/understanding-and-analyzing-xray-scan-results/violations-handling-and-notifications/jira-integration/setup-xray-jira-integration.md)
            * [View Jira Tickets Created with Xray Integration](products/xray/xray-features-and-capabilities/understanding-and-analyzing-xray-scan-results/violations-handling-and-notifications/jira-integration/view-jira-tickets-created-with-xray-integration.md)
            * [Manually Create a Jira Ticket](products/xray/xray-features-and-capabilities/understanding-and-analyzing-xray-scan-results/violations-handling-and-notifications/jira-integration/manually-create-a-jira-ticket.md)
            * [Ticket Status](products/xray/xray-features-and-capabilities/understanding-and-analyzing-xray-scan-results/violations-handling-and-notifications/jira-integration/ticket-status.md)
            * [Best Practices](products/xray/xray-features-and-capabilities/understanding-and-analyzing-xray-scan-results/violations-handling-and-notifications/jira-integration/best-practices.md)
            * [Xray Jira Integration REST API Support](products/xray/xray-features-and-capabilities/understanding-and-analyzing-xray-scan-results/violations-handling-and-notifications/jira-integration/xray-jira-integration-rest-api-support.md)
          * [Webhooks](products/xray/xray-features-and-capabilities/understanding-and-analyzing-xray-scan-results/violations-handling-and-notifications/webhooks.md)
      * [Xray Reports](products/xray/xray-features-and-capabilities/reports.md)
    * [Quick Start](products/xray/quick-start.md)
    * [Configure Xray](products/xray/configure-xray/README.md)
      * [Index Xray Resources](products/xray/configure-xray/index-xray-resources/README.md)
        * [Configure Indexing in JFrog Xray](products/xray/configure-xray/index-xray-resources/configure-indexing-in-jfrog-xray.md)
        * [Set a Retention Period for Xray Indexed Resources](products/xray/configure-xray/index-xray-resources/retention-period.md)
      * [Create Watches](products/xray/configure-xray/create-watches.md)
      * [Create Policies](products/xray/configure-xray/create-policies.md)
    * [Manage Xray](products/xray/xray-management/README.md)
      * [Xray <--> JFrog External DB Sync](products/xray/xray-management/xray-less-than-greater-than-jfrog-external-db-sync.md)
      * [Migration Guide for Self-Hosted Customers: Upgrading from DBSync V1 to V3](products/xray/xray-management/migration-guide-for-self-hosted-customers-upgrading-from-dbsync-v1-to-v3.md)
      * [Advanced Settings](products/xray/xray-management/advanced-settings.md)
      * [Custom Software Licenses](products/xray/xray-management/custom-licenses.md)
      * [System Monitoring](products/xray/xray-management/system-monitoring.md)
      * [TLS Certificates](products/xray/xray-management/tls-certificates.md)
    * [Xray How-Tos](products/xray/xray-how-tos/README.md)
      * [How to Filter Out Your 1st Party Components in CycloneDX SBOM report](products/xray/xray-how-tos/how-to-filter-1st-party-components.md)
      * [How to Detect Malicious AI Models using Xray](products/xray/xray-how-tos/how-to-detect-malicious-ai-models-using-xray.md)
      * [How to Assign Supplier to your resources in SBOM reports](products/xray/xray-how-tos/how-to-assign-supplier-to-your-resources-in-sbom-reports.md)
      * [How to Block Malicious Packages in your SDLC](products/xray/xray-how-tos/how-to-block-malicious-packages-in-your-sdlc.md)
      * [How to Block Critical and High Vulnerabilities Before Promotion](products/xray/xray-how-tos/how-to-block-critical-and-high-vulnerabilities-before-promotion.md)
      * [How to Create a Violation for a Specific Package Version](products/xray/xray-how-tos/how-to-create-a-violation-for-a-specific-package-version.md)
      * [How to Send Email Notifications for Each Critical Vulnerability Found in Resource](products/xray/xray-how-tos/how-to-send-email-notifications-for-each-critical-vulnerability-found-in-resource.md)
      * [How to Generate a Report with All Vulnerabilities in a Distributed Bundle](products/xray/xray-how-tos/how-to-generate-a-report-with-all-vulnerabilities-in-a-distributed-bundle.md)
      * [How to Generate a Report with All Used Licenses in Your Environment Using JFrog Xray](products/xray/xray-how-tos/how-to-generate-a-report-with-all-used-licenses-in-your-environment-using-jfrog-xray.md)
  * [Advanced Security](products/advanced-security/README.md)
    * [Supported Technologies](products/advanced-security/supported-technologies.md)
    * [Features and Capabilities](products/advanced-security/features-and-capabilities/README.md)
      * [CVEs Contextual Analysis](products/advanced-security/features-and-capabilities/vulnerability-contextual-analysis.md)
      * [Secrets Scans](products/advanced-security/features-and-capabilities/secrets-scans.md)
      * [Misconfigurations Scans](products/advanced-security/features-and-capabilities/misconfigurations-scans.md)
      * [SAST](products/advanced-security/features-and-capabilities/sast/README.md)
        * [Prerequisites](products/advanced-security/features-and-capabilities/sast/prerequisites.md)
        * [List of SAST Rules](products/advanced-security/features-and-capabilities/sast/list-of-sast-rules.md)
    * [Set Up Advanced Security](products/advanced-security/set-up-advanced-security/README.md)
      * [Initiate Advanced Scans](products/advanced-security/set-up-advanced-security/initiate-advanced-scans/README.md)
        * [Repositories](products/advanced-security/set-up-advanced-security/initiate-advanced-scans/repositories.md)
        * [Artifacts](products/advanced-security/set-up-advanced-security/initiate-advanced-scans/artifacts.md)
      * [Create Advanced Security Policies](products/advanced-security/set-up-advanced-security/create-advanced-security-policies/README.md)
        * [Contextual Analysis Policy](products/advanced-security/set-up-advanced-security/create-advanced-security-policies/contextual-analysis-policy.md)
        * [Exposures Policy](products/advanced-security/set-up-advanced-security/create-advanced-security-policies/exposures-policy.md)
      * [Ignore Violations](products/advanced-security/set-up-advanced-security/ignore-violations.md)
    * [How-Tos](products/advanced-security/how-tos/README.md)
      * [Vulnerability Contextual Analysis](products/advanced-security/how-tos/vulnerability-contextual-analysis.md)
      * [Scan Results and Post-Scan Actions](products/advanced-security/how-tos/scan-results-and-post-scan-actions.md)
      * [Create an Uber JAR for Contextual Analysis](products/advanced-security/how-tos/create-an-uber-jar-for-contextual-analysis.md)
      * [Secrets Scans](products/advanced-security/how-tos/secrets-scans.md)
      * [Preventing Supply Chain Attacks in a DevOps Pipeline - example](products/advanced-security/how-tos/preventing-supply-chain-attacks-in-a-devops-pipeline-example.md)
      * [Preventing a Log4j Exploit in a CI/CD Pipeline - example](products/advanced-security/how-tos/preventing-a-log4j-exploit-in-a-ci-cd-pipeline-example.md)
      * [Utilizing JFrog Advanced Security Findings for Risk Mitigation](products/advanced-security/how-tos/utilizing-jfrog-advanced-security-findings-for-risk-mitigation.md)
  * [Runtime](products/runtime/README.md)
    * [Supported Technologies](products/runtime/supported-technologies.md)
    * [Features and Capabilities](products/runtime/features-and-capabilities.md)
    * [Configure Runtime](products/runtime/configure-runtime/README.md)
      * [Sensor](products/runtime/configure-runtime/sensor.md)
      * [OpenShift SCC](products/runtime/configure-runtime/openshift-scc.md)
      * [Certificate Verification](products/runtime/configure-runtime/certificate-verification.md)
      * [Workload Automation Service](products/runtime/configure-runtime/workload-automation-service.md)
    * [Manage Runtime](products/runtime/manage-runtime.md)
    * [How-Tos](products/runtime/how-tos/README.md)
      * [Inspecting Live Software Components](products/runtime/how-tos/inspecting-live-software-components.md)
      * [Reducing Noise in Risk Management](products/runtime/how-tos/reducing-noise-in-risk-management.md)
      * [Fast Exposure Window Closing](products/runtime/how-tos/fast-exposure-window-closing.md)
      * [Strengthening Runtime Trust Through Image Verification](products/runtime/how-tos/strengthening-runtime-trust-through-image-verification.md)
      * [Detecting Your Live Artifacts in Artifactory](products/runtime/how-tos/detecting-your-live-artifacts-in-artifactory.md)
  * [Catalog](products/catalog/README.md)
    * [Catalog Supported Technologies](products/catalog/catalog-supported-technologies.md)
    * [Catalog Features and Capabilities](products/catalog/catalog-features-and-capabilities.md)
    * [Configure Catalog](products/catalog/configure-catalog/README.md)
      * [Configure and Manage Labels](products/catalog/configure-catalog/configure-and-manage-labels.md)
      * [GraphQL APIs](products/catalog/configure-catalog/graphql-apis.md)
    * [Catalog How-Tos](products/catalog/catalog-how-tos/README.md)
      * [How to Identify and Mitigate Vulnerable OSS Packages in Your Repository](products/catalog/catalog-how-tos/how-to-identify-and-mitigate-vulnerable-oss-packages-in-your-repository.md)
      * [How to Enforce Compliance Policies Using Catalog Labels](products/catalog/catalog-how-tos/how-to-enforce-compliance-policies-using-catalog-labels.md)
      * [How to Compare and Select the Best OSS Package for Your Project](products/catalog/catalog-how-tos/how-to-compare-and-select-the-best-oss-package-for-your-project.md)
* [Developers](developers/README.md)
  * [Working in Air-Gapped Environments](developers/working-in-air-gapped-environments.md)
  * [JFrog Security CLI](developers/jfrog-security-cli/README.md)
    * [Platform Maintenance](developers/jfrog-security-cli/platform-maintenance/README.md)
      * [Download Updates for Xray's Vulnerability Database](developers/jfrog-security-cli/platform-maintenance/download-updates-for-xrays-vulnerability-database.md)
      * [Count Contributing Developers](developers/jfrog-security-cli/platform-maintenance/count-contributing-developers.md)
    * [Scan Your Source Code](developers/jfrog-security-cli/scan-your-source-code.md)
    * [Scan Your Binaries](developers/jfrog-security-cli/scan-your-binaries.md)
    * [Scan Published Builds](developers/jfrog-security-cli/scan-published-builds.md)
    * [Enrich your SBOM JSONs & XMLs](developers/jfrog-security-cli/enrich-your-sbom-jsons-and-xmls.md)
    * [Curation Compliance Check](developers/jfrog-security-cli/curation-compliance-check.md)
  * [Code Security Within Your IDE](developers/code-security-within-your-ide/README.md)
    * [Visual Studio Code](developers/code-security-within-your-ide/vs-code/README.md)
      * [Package Manager Prerequisites](developers/code-security-within-your-ide/vs-code/package-manager-prerequisites.md)
      * [Supported Technologies](developers/code-security-within-your-ide/vs-code/supported-technologies.md)
      * [Installation](developers/code-security-within-your-ide/vs-code/installation.md)
      * [Manage](developers/code-security-within-your-ide/vs-code/manage.md)
      * [Quick Start](developers/code-security-within-your-ide/vs-code/quick-start.md)
      * [How-Tos](developers/code-security-within-your-ide/vs-code/how-tos.md)
    * [JetBrains](developers/code-security-within-your-ide/jetbrains/README.md)
      * [Prerequisites](developers/code-security-within-your-ide/jetbrains/prerequisites.md)
      * [Supported Technologies](developers/code-security-within-your-ide/jetbrains/supported-technologies.md)
      * [Installation](developers/code-security-within-your-ide/jetbrains/installation.md)
      * [Manage](developers/code-security-within-your-ide/jetbrains/manage.md)
      * [Quick Start](developers/code-security-within-your-ide/jetbrains/quick-start.md)
      * [How-Tos](developers/code-security-within-your-ide/jetbrains/how-tos.md)
      * [Troubleshooting](developers/code-security-within-your-ide/jetbrains/troubleshooting.md)
    * [Eclipse](developers/code-security-within-your-ide/eclipse/README.md)
      * [Prerequisites](developers/code-security-within-your-ide/eclipse/prerequisites.md)
      * [Supported Technologies](developers/code-security-within-your-ide/eclipse/supported-technologies.md)
      * [Installation](developers/code-security-within-your-ide/eclipse/installation.md)
      * [Manage](developers/code-security-within-your-ide/eclipse/manage.md)
      * [Quick Start](developers/code-security-within-your-ide/eclipse/quick-start.md)
      * [How-Tos](developers/code-security-within-your-ide/eclipse/how-tos.md)
    * [Visual Studio](developers/code-security-within-your-ide/visual-studio/README.md)
      * [Prerequisites](developers/code-security-within-your-ide/visual-studio/prerequisites.md)
      * [Supported Technologies](developers/code-security-within-your-ide/visual-studio/supported-technologies.md)
      * [Installation](developers/code-security-within-your-ide/visual-studio/installation.md)
      * [Manage](developers/code-security-within-your-ide/visual-studio/manage.md)
      * [Quick Start](developers/code-security-within-your-ide/visual-studio/quick-start.md)
      * [How-Tos](developers/code-security-within-your-ide/visual-studio/how-tos.md)
  * [APIs](developers/apis.md)
  * [Scanning Source Code Repositories](developers/scanning-source-code-repositories/README.md)
    * [Package Manager Prerequisites](developers/scanning-source-code-repositories/installation.md)
    * [Features and Capabilities](developers/scanning-source-code-repositories/features-and-capabilities.md)
    * [Supported Technologies](developers/scanning-source-code-repositories/supported-technologies.md)
    * [Installing Frogbot](developers/scanning-source-code-repositories/configure-frogbot/README.md)
      * [GitHub](developers/scanning-source-code-repositories/configure-frogbot/github.md)
      * [GitLab](developers/scanning-source-code-repositories/configure-frogbot/gitlab.md)
      * [Bitbucket Server](developers/scanning-source-code-repositories/configure-frogbot/bitbucket-server.md)
      * [Azure Repos](developers/scanning-source-code-repositories/configure-frogbot/azure-repos.md)
      * [Jenkins](developers/scanning-source-code-repositories/configure-frogbot/jenkins.md)
    * [Troubleshooting](developers/scanning-source-code-repositories/troubleshooting.md)
    * [Frogbot Optional Configuration Parameters](developers/scanning-source-code-repositories/frogbot-optional-configuration-parameters.md)
    * [Frogbot Offline](developers/scanning-source-code-repositories/frogbot-offline.md)
  * [CI/CD](developers/ci-cd.md)
