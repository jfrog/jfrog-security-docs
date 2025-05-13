# Configure Indexing in JFrog Xray

Navigate to **Administration → Xray → Indexed Resources** and do the following:&#x20;

### **Indexing Repositories**

Repositories must be indexed to allow continuous vulnerability and compliance scanning.

#### **How to Enable Repository Indexing:**

1. Under **Repositories**, click **Add Repositories**.
2. Select the repositories you want Xray to index.
3. Click **Save** to start indexing.

{% hint style="info" %}
Starting from Xray version 3.120.x and above, enable Xray indexing when creating a new repository by default. This is enabled by setting the Xray ​`system.yaml​​` `​server.enableXrayOnNewRepos​` parameter.
{% endhint %}

### **Indexing Builds**

Indexing builds ensure that all direct and transitive dependencies used during CI/CD processes are scanned.

#### **How to Enable Build Indexing:**

1. Go to **Xray → Administration → Indexing → Builds**.
2. Click **Add Builds** and select the relevant builds.
3. Click **Save**.

### **Indexing Release Bundles**

Before distributing software, it's important to scan release bundles to ensure they are secure and compliant.

#### **How to Enable Release Bundle Indexing:**

1. Navigate to **Xray → Administration → Indexing → Release Bundles**.
2. Click **Add Release Bundles** and select the bundles you want to scan.
3. Click **Save** to start indexing.

### **Verify Indexing Status**

Once indexing is enabled:

* Check if repositories, builds, and Release Bundles appear in the **indexed items list**.&#x20;
