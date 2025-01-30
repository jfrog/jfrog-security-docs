---
description: >-
  This workflow uses JFrog Runtime Security to monitor clusters and handle
  risks.
---

# Continuous Monitoring and Risk Management

## **Monitor Clusters**

1. Access **Cluster Inventory** under Sensor Management to see a list of monitored clusters.
2. Check cluster health, node statuses, and controller/sensor deployments.
3. Drill down into individual clusters to view detailed node information.

## **Identify Risks**

1. Go to the **Live Assessment** tab to view runtime objects (workloads, processes, images).
2. Use filters to focus on high-risk elements (e.g., critical vulnerabilities, untrusted images).
3. Examine risks such as malicious packages, untrusted images, and integrity violations.

## **Remediate Issues**

1. For detected vulnerabilities, trace the affected artifacts back to their source in Artifactory.
2. Replace untrusted or outdated images and deploy updates to workloads.
3. Reassess the environment to ensure issues are resolved.

## **Track Progress**

1. Continuously monitor the Live Assessment dashboard for new issues.
2. Use historical data (retained for 10 days) to compare improvements and detect recurring problems.
