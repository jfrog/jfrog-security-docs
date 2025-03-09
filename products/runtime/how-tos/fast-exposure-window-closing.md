# Fast Exposure Window Closing

In this guide, we will demonstrate how to leverage the traceability capabilities of JFrog Runtime, specifically utilizing the **Build Owner** and **Deployed By** attributes in the detailed view of an image tag. We will also explain how to set up alarms based on worker events to ensure real-time notifications for relevant users and send runtime events to all pertinent tools.

### Step 1: Accessing Image Tag Details

#### View Image Details

1. In **Runtime** > **Live Assessment** > **Images**, locate the image you want to investigate.
2. Click on the image name to open the **Detailed View**.\
   The Detailed View window opens.&#x20;
3. In the Detailed View, find the **Build Owner** and **Deployed By** attributes. \
   These attributes provide critical information about who created the image and who deployed it, allowing you to trace back any issues to the responsible parties.
4. **Identify Responsible Parties** : Use the **Build Owner** to contact the developer responsible for the image. If an integrity violation or untrusted registry issue is detected, you can quickly reach out to the relevant team for remediation.
5. **Document Issues** : Record any discrepancies or security concerns associated with the image in your tracking system, referencing the Build Owner and Deployed By information for accountability.

### Step 2: Setting Up Alarms with Runtime Workers

#### Configure Worker Events

1. Navigate to the **Workers** section in your JFrog Platform.
2. Set up a new worker that listens for specific runtime events, such as **Workload Changed Events** .
3. Define the criteria for triggering alerts, including:
   * Changes in deployment status.
   * Integrity violations detected.
   * Images from untrusted registries.

#### Create Alert Notifications

1. In the worker configuration, specify the alerting mechanism (e.g., email, Slack, webhook).
2. Ensure that notifications include essential information:
   * Workload details (name, namespace, cluster).
   * Image details (name, tag, integrity status).
   * Any associated risks or vulnerabilities.

#### Test Alerting Functionality

1. Simulate a workload change or integrity violation to verify that alerts are triggered correctly.
2. Ensure that notifications are sent to the relevant users and that runtime events are communicated to all necessary tools for further action.

