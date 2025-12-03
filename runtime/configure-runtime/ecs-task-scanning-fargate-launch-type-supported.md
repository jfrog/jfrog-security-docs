# ECS Task Scanning (Fargate Launch Type Supported)

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

### Integration Process

Once your AWS user is ready, follow this step-by-step process to enable Fargate scanning.

1. Store AWS credentials in JFrog.\
   Use the **AWS Credentials Management** API:

```bash
bashCopyEditPOST /v1/aws/credentials
```

Request body:

```json
jsonCopyEdit{
  "credentialName": "fargate-production",
  "accessKey": "<your-aws-access-key>",
  "accessSecret": "<your-aws-secret-access-key>"
}
```

**Response:**

```json
jsonCopyEdit{
  "secretName": "fargate-production",
  "credentialId": "<generated-uuid>",
  "status": "ok"
}
```

You'll receive a status of `"ok"` and a **credentialId** (**which is the UUID of the stored credentials**).\
Save this `credentialId` — it will be used to register ECS/Fargate scanning tasks.

{% hint style="info" %}
Save these values — they will be used to register ECS/Fargate scanning tasks.
{% endhint %}

2. Register an ECS Task (Fargate launch type supported).\
   Use the **ECS Task Registration** API (Fargate is supported natively):

```bash
bashCopyEditPOST /v1/aws/ecs/tasks
```

Request body:

```json
jsonCopyEdit{
  "taskName": "fargate-scan-prod",
  "secretUUID": "<uuid-from-step-1>",
  "region": "us-east-1"
}
```

This registers the task to scan containers running in ECS (Fargate or EC2) in the specified region.

### Reviewing Scan Results

To view scan outcomes and live status:

1. In the **JFrog Platform**, navigate to **Runtime** > **Live Assessments**.
2. Filter or search for your registered Fargate task (by name or region).
3. View vulnerability, compliance, and risk assessments.
