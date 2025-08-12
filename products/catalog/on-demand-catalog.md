# On-Demand Catalog

The On-Demand Catalog extends the JFrog Catalog to include scan results for packages not available in the Public Catalog. These packages typically originate from uncataloged repositories, such as internally developed components, sensitive dependencies, or private third-party distributions.

When triggered, On-Demand Catalog stores and retrieves scan results from Xray, providing vulnerability, malicious package, and license information. It is designed to work in tandem with On-Demand Curation to apply curation policies to these packages.

On-demand Catalog is suitable for repositories that are not cataloged, within ecosystems that are already supported (e.g., Docker, Maven).

#### Business Value

* **Expanded Coverage** – Includes private, internal, or specialized packages not listed in the Public Catalog.
* **Improved Security & Compliance** – Ensures the same vulnerability and license checks apply to all software components.
* **Developer-Friendly** – Integrates into existing workflows without slowing down package retrieval.
* **Docker Support** – Displays vulnerabilities and licenses for packages within Docker images (aggregated by layer in phase 1).

### How to Enable

> **Note**\
> On-Demand Catalog does not have a separate activation toggle.\
> It is activated automatically when On-Demand Curation is enabled.

When On-Demand Curation is active, all uncataloged repositories eligible for curation will use the On-Demand Catalog to store scan results.

### How to Use

1. **Search for Packages** – Use the Catalog search; on-demand packages appear alongside cataloged packages.
2. **Identify On-Demand Results** – Look for the **On-demand** tag in search results and package details pages.
3. **View Details** – Open the package details page to see vulnerability and license data.
4. **Docker UI Specifics** – Vulnerabilities and licenses are shown for each package within an image (aggregated view).
5. **Persistence** – Results are stored for future use. When accessed again, the Catalog refreshes results via Xray to ensure up-to-date data.

### UI Reference

**Search Results**

* On-demand packages are marked with the **On-demand** tag.

**See All Page**

* Displays Public and On-Demand Catalog results in separate tabs.

**Docker View**

* Shows aggregated vulnerabilities/licenses for image layers.
