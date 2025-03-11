# How to Assign Supplier to your resources in SBOM reports

1. **Assign Supplier Information**
   *   Assign your supplier name (e.g "Acme Inc") to the following Artifactory property:

       ```plaintext
       / propertySet :sbom.metadata.supplier.name
       ```
   * This sets the supplier name for your software components in the SBOM.
2. **Propagation in SBOM Reports**
   * Once assigned, the supplier name is mapped to the following fields in different SBOM formats:
     * **SPDX 2.2:** `PackageCreatorOrganizations`
     * **CycloneDX 1.6:** `metadata.component.supplier`

The assigned supplier details will now be **automatically included** in your SBOM reports.

