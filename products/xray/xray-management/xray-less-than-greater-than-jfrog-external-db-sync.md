# Xray <--> JFrog External DB Sync

To provide accurate and up-to-date **vulnerability intelligence**, JFrog Xray continuously synchronizes with its **JFrog global security database**. This database contains:

✔ **Known CVEs (Common Vulnerabilities and Exposures)**\
✔ **Security research insights from JFrog**\
✔ **Open-source software vulnerabilities**\
✔ **License compliance data**

Keeping Xray’s database **synchronized** ensures that scans detect the **latest threats**, allowing security teams to **proactively address vulnerabilities** in software artifacts.

***

### **Database Synchronization Modes**

Xray offers two modes of database synchronization, depending on your organization's connectivity and security requirements:

| **Mode**         | **Description**                                                               | **Best Use Case**                                                        |
| ---------------- | ----------------------------------------------------------------------------- | ------------------------------------------------------------------------ |
| **Online Mode**  | Xray automatically syncs with JFrog’s security database at regular intervals. | Organizations with **internet access**, requiring **real-time updates**. |
| **Offline Mode** | Xray syncs manually using downloaded data packages.                           | **Air-gapped environments** or **restricted network access**.            |

***

### **Online Mode: Automatic Synchronization**

By default, Xray operates in **Online Mode**, where it **automatically fetches security updates** from the JFrog global database.

#### **How It Works**

* Xray **checks for updates** periodically.
* The database is **incrementally updated**, ensuring minimal performance impact.
* No user intervention is required—Xray stays **continuously up to date**.

&#x20;**Best For:** Cloud-based and connected environments that need **real-time security intelligence**.

***

### **Offline Mode: Manual Synchronization**

For **air-gapped networks** or organizations with **restricted internet access**, Xray supports **Offline Mode**.

#### **How It Works**

1. Download the **latest database update package** from JFrog’s external source.
2. Transfer the update package **to the offline Xray instance**.
3. Apply the update using the **JFrog CLI or Admin Panel**.

#### **Steps to Manually Sync in Offline Mode**

**Step 1: Download the Security Database Update**

* Obtain the latest vulnerability database file from **JFrog’s security data source**.
* Ensure that your **JFrog environment is authorized** to access the update package.

**Step 2: Transfer the Update to the Offline System**

* Move the package to the **isolated network** using secure file transfer.

**Step 3: Apply the Update to Xray**

* Use **JFrog CLI** or the **JFrog Platform UI** to import the security database update.
* Verify that the synchronization was successful.

&#x20;**Best For:** Enterprises with **restricted internet access** that require **controlled updates**.

***

### **Verifying Database Synchronization**

To check the current synchronization status:

1. Navigate to **Xray → Administration → Security & Compliance → Database Sync**.
2. Verify the **last update timestamp** and sync frequency.
3. Check for **any sync errors** or connectivity issues.

For **offline mode**, ensure that the **latest update package** has been applied correctly.

