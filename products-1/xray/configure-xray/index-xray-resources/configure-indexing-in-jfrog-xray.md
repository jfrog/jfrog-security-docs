# Configure Indexing in JFrog Xray

### **Step 1: Access the Indexing Configuration**

1. Log in to the **JFrog Platform**.
2. Navigate to **Administration → Xray → Indexed Resources**.

***

### **Step 2: Indexing Repositories**

Repositories must be indexed to allow **continuous vulnerability and compliance scanning**.

#### **How to Enable Repository Indexing:**

1. Under **Repositories**, click **Add Repositories**.
2. Select the repositories you want Xray to index.
3. Click **Save** to start indexing.

**Tip:**\
✔ Enable **automatic indexing** for critical repositories (e.g., production repositories).\
✔ For **performance optimization**, avoid indexing **temporary or test repositories**.

***

### **Step 3: Indexing Builds**

Indexing **builds** ensures that all **direct and transitive dependencies** used during CI/CD processes are scanned.

#### **How to Enable Build Indexing:**

1. Go to **Xray → Administration → Indexing → Builds**.
2. Click **Add Builds** and select the relevant builds.
3. Click **Save**.

&#x20;**Tip:**\
✔ Enable build indexing for **critical production pipelines**.\
✔ Use Xray's integration with **Jenkins, GitHub Actions, GitLab CI/CD, and Azure DevOps** for **automated security checks**.

***

### **Step 4: Indexing Release Bundles**

Before distributing software, it's important to **scan release bundles** to ensure they are **secure and compliant**.

#### **How to Enable Release Bundle Indexing:**

1. Navigate to **Xray → Administration → Indexing → Release Bundles**.
2. Click **Add Release Bundles** and select the bundles you want to scan.
3. Click **Save** to start indexing.

&#x20;**Tip:**\
✔ Always **index release bundles before deploying software** to production.\
✔ Generate **SBOM (Software Bill of Materials) reports** for compliance tracking.

***

### **Step 5: Verify Indexing Status**

Once indexing is enabled:

* Check if repositories, builds, and release bundles appear in the **indexed items list**.&#x20;
