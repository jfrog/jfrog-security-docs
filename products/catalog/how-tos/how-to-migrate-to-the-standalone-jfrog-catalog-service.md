# How to Migrate to the Standalone JFrog Catalog Service

### Use Case

JFrog Catalog is available as a **standalone service**, decoupled from Xray, and is recommended for customers who want improved stability, availability, and access to advanced Catalog capabilities.\
This guide explains how to migrate to the standalone JFrog Catalog service and transition existing Catalog data.

The standalone JFrog Catalog service introduces enhanced capabilities and broader ecosystem support while operating independently of Xray. Migrating to this service allows you to take advantage of new Catalog features and improved system reliability.

#### Key Improvements

**Decoupled from Xray**

The standalone Catalog service runs independently of Xray, reducing operational dependencies and improving overall performance and stability.

**New Capabilities**

The standalone Catalog service introduces features that were not available in the legacy Catalog implementation, including:

* **Custom Catalog support**, enabling:
  * Package **labels**
  * More granular and tailored **curation policies**
* **Expanded ecosystem coverage**, including:
  * Ruby Gems
  * Gradle
  * Rust
  * Conda
  * PHP
  * Pub
  * Alpine
  * Debian

### Steps

#### 1. [Install the Standalone Catalog Service](https://jfrog.com/help/r/jfrog-installation-setup-documentation/installing-catalog)

The Catalog service is included with the latest Xray versions for Self-Hosted installations. Ensure compatibility.&#x20;

Once installed, the Catalog service runs independently of Xray.

#### 2. Plan the Catalog Migration

Migrating to the standalone Catalog service requires migrating existing Catalog data.

* The migration is performed with assistance from the JFrog team.
* Customers must schedule a dedicated migration session to ensure a smooth and controlled transition.

#### 3. Schedule a Migration Session

To initiate the migration to the standalone Catalog service:

* Contact **JFrog Support** at **support@jfrog.com**, or
* Open a request through the JFrog Support Portal.

During the migration session, the JFrog team will:

* Coordinate the Catalog data migration
* Validate Catalog functionality after migration
* Confirm successful enablement of the standalone Catalog service
