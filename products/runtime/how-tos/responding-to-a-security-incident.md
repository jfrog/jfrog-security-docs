---
description: >-
  This workflow outlines steps for responding to a detected security breach or
  anomaly.
---

# Responding to a Security Incident

## **Identify the Breach**

1. Receive an alert (e.g., via email or dashboard notification) for a security incident, such as a malicious package or integrity violation.
2. Navigate to the affected cluster in the **Cluster Inventory**.

## **Investigate the Impact**

1. Use the Live Assessment to pinpoint the affected workloads, processes, or images.
2. Check the Cluster Detailed View to assess the extent of the issue across nodes.

## **Isolate the Issue**

1.  Disable affected sensors or nodes temporarily to contain the breach:

    ```bash
    bashCopyEditkubectl label nodes <node-name> disable_jfrog_runtime=true
    ```

## **Remediate and Restore**

1. Replace compromised workloads or processes with clean versions.
2.  Re-enable sensors and nodes after the remediation:

    ```bash
    bashCopyEditkubectl label nodes <node-name> disable_jfrog_runtime-
    ```

## **Post-Incident Analysis**

1. Generate a report using the Live Assessment and Risk Summary tabs to document the incident.
2. Adjust security policies or configurations to prevent similar breaches in the future.
