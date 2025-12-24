# Configure AWS ECS Fargate

Runtime supports scanning containerized applications deployed as **ECS tasks** in AWS. This includes tasks running on both **Fargate** and **EC2** launch types. Fargate is a serverless compute engine for containers that removes the need to manage EC2 infrastructure.

With this support, Runtime can securely connect to your AWS environment, discover ECS tasks (including those running on Fargate), and analyze them for security risks using stored AWS credentials.

### Before You Begin

Before integrating Fargate with JFrog Runtime, perform the following setup in your AWS account:

* Create a dedicated AWS IAM user\
  Go to AWS Console → **IAM → Users** and create a new user for integration with JFrog Runtime.
  * **Username**: Any name (e.g., `jfrog-runtime-user`)
  * **Programmatic Access**: Enabled
  * **Permissions**: Attach a policy that allows the following actions:
    * `ecs:List*`
    * `ecs:Describe*`
    * `iam:List*`
    * `cloudwatch:Get*`
    * `logs:Describe*`
    * `logs:Get*`

These permissions enable ECS and Fargate discovery and scanning.

* Generate access keys
  * After creating the user, generate an **Access Key ID** and **Secret Access Key**.
  * These values will be used to authenticate JFrog Runtime with AWS.

#### Step 1: Choose ECS Fargate as the Provider

1. Navigate to **Runtime > Sensor Management**.
2. Click **Install Runtime**.
3. In the **Choose Your Provider** screen, select **ECS: Fargate**.
4. Click **Next**.

#### Step 2: Configure Environment Details

This screen defines how scanning will be authorized and executed.

**Task Name**

Enter a recognizable task name to help identify and monitor this scanning job in AWS.\
Example: `fargate-prod-scan` or `teamA-eu-central-clusters`.

**Select Credential Secret**

Select the AWS credential secret that JFrog will use to access and list your Fargate workloads.

You may:

* Select an existing secret, or
* Create a new one directly from this screen

**To create a new secret:**

1. Open **Select Credential Secrets**.
2. Click **Add New Secret**.
3. Provide the following:
   * **Secret Alias** – A name for the stored credential (e.g., `runtime-scan-prod`)
   * **Secret Key (Access ID)** – Your AWS Access Key ID
   * **Secret Access Key** – Your AWS Secret Key
4. Click **Create** to save.
5. The new secret is now selectable in the environment configuration dropdown.

**Deployment Region**

Select the AWS region that contains the ECS Fargate workloads you want to scan.\
Example: `US EAST (N. Virginia)`.

#### Step 3: Start Scanning

1. After all required fields are provided, click **Next**.
2. The wizard transitions to the **Scanning Status** screen.

Runtime Security will now:

* Detect ECS clusters and tasks in the selected region
* Begin scanning them for runtime exposures and vulnerabilities

Scanning may take several minutes depending on workload size.

#### Viewing Scan Results

After the scan begins, return to:

**Runtime > Sensor Management**

Each discovered cluster displays:

* **Scanning Status** (Running, Partial, Failed, Completed)
* **Cloud Provider** (AWS Fargate)
* **Sensor Status**
* **Cluster details and findings**

If a cluster shows **Partial**, it may still be scanning.\
If a cluster shows **Failed**, click into the row for troubleshooting details.
