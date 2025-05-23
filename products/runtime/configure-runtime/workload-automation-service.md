# Workload Automation Service

**Workers** is a JFrog platform service that allows you to extend and control your execution flows. It provides a serverless execution environment. You can create workers to enhance the platform's functionality. Workers are triggered automatically by events within the JFrog Platform, giving you the flexibility to address specific use cases. \
Read more about the JFrog platform Workers [here](https://jfrog.com/help/r/jfrog-platform-administration-documentation/workers).

There are four types of built-in events that may occur in your **Workload** that may be configured to trigger actions:&#x20;

* Changes to the list of images deployed within the workload
* Changes to Xray image information
* Changes to image integrity validation information
* Changes to image trust information

## Create a Runtime Automation

### Step 1: Create a New Worker

1. Naviaget to **Administration** > **Workers**.
2. From the **Add Worker** dropdown, select **New Event Driven Worker**.\
   The **Create New Worker** window opens.&#x20;
3. On the top left corner, from the dropdown menu, select **Runtime**.\
   This will narrow down the selection to Workers relevant to Runtime.
4. Add an **After Workload State Change** Worker. \
   The **Add New Worker** window opens.

### Step 2: Configure the Worker

1. Enter a **Worker** name.
2. Enter or modify the script in the **TypeScript Editor**. \
   Use the auto-complete function to improve efficiency while coding.
3. Click the **Settings** icon from the top-right corner of the window, and then enter the details in the relevant fields:
   1. **Description**: Enter a brief description of the worker.
   2.  **Select Secrets**: Secrets are stored securely and not in plain text. The secret's clear-text value is never returned in an API or UI and will be masked from all the logs.

       **To add a secret:**

       1. Enter the **Name** and **Value** of the secret.
       2. Click **+ Add secret** to add more secrets.
       3. Click **Delete** icon to remove any secret.
4. To see results in the UI, check the **Show status of successful executions in the Troubleshooting tab** box. \
   If unchecked, the Worker will still run but won't show results in the UI.
5. To enable the Worker, toggle the **Enable Worker** on.
6. To save the Worker, Select **OK**.

### Step 3: Test Events

1. In the **Testing** pane, edit the JSON payload used to simulate the worker's events.
2. Click **Run** to test the worker.
3. Review results in:
   * **Execution Results** tab: for responses
   * **Execution Logs** tab: for logs
   * **Metrics** tab: for run time, memory, and CPU utilization details.

#### Event Sample

```
{
  "change_type": "workload",
  "workload_changed_object": {
    "name": "frontend-service",
    "namespace": "production",
    "cluster": "production-euc1",
    "nodes": [
      "node-1",
      "node-2"
    ],
    "risks": [
      "untrusted_registry_images",
      "critical_and_applicable_cves"
    ],
    "vulnerabilities_count": 5
  },
  "image_tags_object": [
    {
      "name": "frontend-image",
      "registry": "docker.io",
      "repository_path": "company/frontend",
      "architecture": "amd64",
      "tag": "v1.2.3",
      "sha256": "bce40a2025d450f7865c5ec6f1ebea13108166f81fe41462069690cb4d96c00f",
      "risks": [
        "critical_and_applicable_cves"
      ],
      "vulnerabilities": [
        {
          "package_type": "npm",
          "xray_id": "XRAY-2024-001",
          "cve_id": "CVE-2024-1234",
          "severity": "Critical",
          "cvss_v2": "6.5",
          "cvss_v3": "8.2",
          "last_fetched": "2025-02-15T12:00:00Z",
          "issue_kind": 1,
          "applicability": "applicable",
          "components": [
            {
              "component_id": "npm:lodash",
              "name": "lodash",
              "version": "4.17.21"
            }
          ]
        }
      ],
      "malicious_packages": null,
      "deployed_by": "jenkins-user",
      "build_info": {
        "build_owner": "devops-team",
        "build_name": "frontend-service",
        "build_number": "456",
        "build_repository": "jfrog-artifactory"
      }
    }
  ]
}
```

### Step 4: Save Your Configuration

1. Click **Save** to finalize the worker configuration.
2. To cancel the configuration, click **Close** and then **Discard** to discard changes.

### Step 5: Review Worker Events

1. Navigate to the **Troubleshooting** tab.
2. Select the **Worker** you wish to review.\
   The **Run History** window opens.&#x20;
3. Select an event.\
   The **History Details** window opens.
4. Under the **Summary** tab, review **Result** and **Payload**. &#x20;
5. Under the **Logs** tab, review logs.
