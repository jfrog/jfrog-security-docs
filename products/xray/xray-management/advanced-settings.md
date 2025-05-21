# Advanced Settings

{% hint style="info" %}
Advanced Settings apply only to Self-Hosted environments.
{% endhint %}

Xray is built on a set of microservices that perform its actions in the realm of indexing artifacts, communicating with Artifactory, managing events and notifications and so on.

To configure these settings, in the Administration module, go to Xray Security and Compliance | Advanced and click Settings.

The following advanced configurations are available:

## Basic Settings

| Field                                                  | Description                                                                                                                        |
| ------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------- |
| Xray Enabled                                           | Indicates that Xray is enabled on the JFrog Platform and is set by default when Xray is installed.                                 |
| Allow download and distribute when Xray is unavailable | Allows downloading artifacts from Artifactory and distributing Release Bundles to Edge Nodes when the Xray service is unavailable. |
| Allow downloads of blocked artifacts                   | Allows downloading all artifacts, including artifacts that have been blocked for download by Xray.                                 |
| Block Unscanned Artifacts Download Timeout (Sec)       | <p>The max time a download request will be pending Xray to complete scanning the artifact. <br>Default value: 60 sec</p>           |

## System Parameters

| Field                     | Description                                                                                                           |
| ------------------------- | --------------------------------------------------------------------------------------------------------------------- |
| SSL Insecure              | Toggles enablement of skipping Xray's self-signed certificate validation.                                             |
| Mail Without SSL          | Toggles usage of Transport Layer Security when connecting to the mail server.                                         |
| Send Anonymous Statistics | Improves the Xray optimization by sending anonymous usage statistics.                                                 |
| Max Disk Usage            | Percentage of disk usage tolerated by Xray. When this value is reached, Xray will NOT download packages for indexing. |
| Monitor Sampling Interval | Interval for executing monitoring jobs on CPU, Disk Usage, restarts, etc.                                             |
| Job Interval              | Interval for running node specific jobs.                                                                              |

## Queue Parameters

|                       |                                                                                                                                |
| --------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| Index                 | Number of workers managing indexing of artifacts.                                                                              |
| Persist               | Number of workers managing persistent storage needed to build the artifact relationship graph.                                 |
| Alert                 | Number of workers managing alerts.                                                                                             |
| Analysis              | Number of workers involved in scanning analysis.                                                                               |
| Impact Analysis       | Number of workers involved in Impact Analysis to determine how a component with a reported issue impacts others in the system. |
| Notification          | Number of workers managing notifications.                                                                                      |
| Queue Message Max TTL | Number of retries to be accepted in the Message Queue system.                                                                  |

{% hint style="info" %}
Adjusting these parameters may affect your system's performance, please contact JFrog Support for additional information.
{% endhint %}
