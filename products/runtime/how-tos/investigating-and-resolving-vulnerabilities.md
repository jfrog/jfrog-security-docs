---
description: >-
  This workflow provides steps to investigate and mitigate vulnerabilities in
  real time.
---

# Investigating and Resolving Vulnerabilities

## **Detect Vulnerabilities**

1. Access the **Risk Summary** tab to identify high-severity risks (e.g., critical CVEs, untrusted registries).
2. Use the Live Assessment to locate affected workloads and processes.

## **Analyze Details**

1. Drill into the **Workload's Process Group Detailed View** to see affected processes.
2. Review associated vulnerabilities and their severity (e.g., CVSS scores, exploitability).

## **Remediate Vulnerabilities**

1. Update or patch affected images in Artifactory.
2. Deploy the updated images to the runtime environment using Kubernetes.
3. Reassess to confirm the vulnerabilities are resolved.

## **Verify Environment Security**

1. Use the Image Tags Detailed View to validate that all running images are patched and from trusted registries.
2. Ensure no lingering risks remain in the monitored environment.
