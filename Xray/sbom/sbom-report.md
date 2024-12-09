# SBOM Report 
Starting from Xray version 3.40.x and above, Xray has introduced the capability to generate a **Software Bills of Materials (SBOM)*- report, that will enable DevSecOps engineers to understand and analyze the dependencies of their components.  
SBOM is a readable inventory of software components and dependencies. The report will include SBOM data of your components, including unidentified components and open-source software. This enables you to:  
-   Understand components and code dependencies.  
-   Gain visibility into open-source licenses for the components in use.  
-   Be aware of the end-of-life of components, and which components need to be updated.  
-   Identify vulnerable components or recently identified vulnerabilities.  
-   Enforce organizational compliance and policies.  

### How it Works
After performing an Xray scan, you can export the scan data as an SBOM report using one of the two supported SBOM formats:  
- **SPDX**: Software Package Data Exchange (SPDX) is a standard format for communicating the components of software packages, including information about license copyrights. It includes several mechanisms that are especially useful for open-source software.  
    - Supported formats: 
        - tag:value 
        - JSON 
        - xlsx  

- **CycloneDX**: CycloneDX is a lightweight SBOM specification designed specifically for software security requirements and related risk analysis. Starting with Xray version 3.67.x and above, the SBOM also includes VEX information, such as vulnerability details, exploitability, and detailed analysis. CycloneDX designed to be flexible, easily adaptable, with implementations for popular build systems.  
    -  Supported formats: 
        - JSON
        - XML