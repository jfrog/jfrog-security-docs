# Reducing Noise in Risk Management

n today’s fast-paced development environment, managing vulnerabilities effectively is crucial for maintaining security without overwhelming your teams with noise. JFrog Runtime Security provides a multi-layered approach to risk prioritization, enabling you to focus on what truly matters. Here’s how you can leverage JFrog's capabilities to reduce noise in risk management.

### 1. Understanding the Layers of Risk Prioritization

#### Xray: Identifying Vulnerabilities

JFrog Xray is your first line of defense, identifying vulnerabilities within your artifacts and ranking them by severity. This allows you to understand the potential risks associated with your packages.

#### JFrog Advanced Security (JAS): Reducing Noise

While Xray identifies vulnerabilities, JAS takes it a step further by filtering out noise. It reduces up to 80% of the irrelevant alerts by determining which vulnerabilities are applicable to your environment. This means you can focus on the vulnerabilities that truly impact your applications.

#### Runtime Security: Focusing on Active Images

Runtime Security enhances your risk management strategy by ensuring you only address vulnerabilities in images that are actively running. By concentrating your remediation efforts on these images, you can ensure that your team is working on relevant issues that affect your production environment.

### 2. Understanding Blast Radius

Another critical aspect of risk prioritization is understanding the blast radius of a vulnerability. Knowing where a Docker image is used can significantly influence your remediation strategy. For instance, an image utilized across multiple clients or critical environments should be prioritized over one used in less strategic contexts. JFrog Runtime Security provides visibility into the deployment landscape, helping you make informed decisions about where to focus your efforts.

### 3. Validating Vulnerabilities in Runtime

The pinnacle of effective risk prioritization is fixing only those vulnerabilities that have been validated in runtime. Here’s how this process works:\
In JFrog Runtime Security, the process of validating vulnerabilities in runtime is designed to ensure that your security efforts are focused on the most relevant risks. The JFrog Runtime Sensor adds runtime signals to your vulnerability assessment, allowing you to identify vulnerabilities that are actively executed in real-time. This capability is supported for both workload and registry scans.

When a vulnerability is validated in runtime, it is counted against the specific process that is executing the code. This validation process is crucial as it ensures that only active vulnerabilities are considered for remediation. Once a vulnerability is validated at the process level, we aggregate this information to the workload level. This means that the number of vulnerabilities reported for a workload reflects only those that have been validated in runtime.

Consequently, the associated risks for both the workload and the processes are solely based on vulnerabilities that have been confirmed as active. For example, if you encounter a risk associated with a critical and applicable CVE on an image, but do not see it reflected in any workloads that are running that image, it indicates that no critical and applicable CVE was validated in runtime by the sensor.

This targeted approach helps you focus your remediation efforts on vulnerabilities that are genuinely active and relevant to your running applications, thereby enhancing your overall risk management strategy. By ensuring that your team addresses only those vulnerabilities validated in runtime, you can significantly reduce noise and improve the efficiency of your security operations.\
\
Conclusion

By utilizing JFrog Runtime Security, you can significantly reduce noise in your risk management processes. Through a combination of vulnerability identification, noise reduction, active image focus, understanding blast radius, and validating vulnerabilities in runtime, you can prioritize your remediation efforts effectively. This strategic approach not only streamlines your security operations but also enhances your overall security posture.
