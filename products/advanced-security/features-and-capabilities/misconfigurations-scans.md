# Misconfigurations Scans

JFrog Advanced Security goes beyond detecting CVEs, 1st party SAST issues, and exposed secrets—it also identifies security misconfigurations that can leave your applications vulnerable. By scanning for misconfigurations across your infrastructure, services, and applications, JFrog Advanced Security helps you strengthen your security posture early in the development pipeline and ensures compliance at every stage.

### **IaC Scans – Infrastructure as Code (IaC) Security Analysis**

JFrog Advanced Security scans your **Terraform files** for cloud misconfigurations at different stages of the development pipeline. During development, it scans **Terraform Modules** and **Plan files** to catch issues early before deployment. Once the infrastructure is deployed, **Terraform State files** in Artifactory are scanned to ensure that cloud services remain securely configured. It supports cloud services from AWS, Azure, and GCP, enabling comprehensive coverage for all major cloud platforms.

A key differentiator of JFrog Advanced Security is its focus on real security risks in Infrastructure as Code (IaC) scanning. Unlike common IaC tools that report many low-severity issues with little impact, JFrog Advanced Security provides detailed severity ratings, allowing teams to identify and address actual security risks. By focusing on the most critical misconfigurations and providing severity ratings that other tools lack, it ensures that security efforts are directed toward genuine threats.

#### **Examples of Detected Misconfigurations**:

* Insufficient access restrictions to services (public access to repositories, publicly accessible clusters, globally readable/deletable/writeable buckets, use of admin roles in ECS services, IAM users with privileged access to all resources, enforce authorization for all API Gateway methods)
* Insecure use of credentials (use of hardcoded credentials)
* Allowing weak crypto algorithms (use of weak cipher suites)
* Running batches in privileged mode
* Enforcement of secure communication (listening to HTTP, unencrypted communications)
* Wildcard actions in Glue policies
* Missing logging (e.g., found CloudTrail trails with logging disabled)
* Disabled upgrades (e.g., RDS database instance with disabled minor engine upgrades)
* Data at rest encryption enablement for Kinesis streams

### Services Scans - Services Configuration Security <a href="#uuid-58e1bcf7-4260-c0bf-5b4b-32c67d2757a7_bridgehead-idm455673167603843399558218115" id="uuid-58e1bcf7-4260-c0bf-5b4b-32c67d2757a7_bridgehead-idm455673167603843399558218115"></a>

JFrog Advanced Security scans common OSS libraries and services in your containers for misconfigurations, ensuring that services such as web servers, databases, and proxies are securely configured by default. This helps prevent vulnerabilities in essential services.

#### **Supported Services:**

* Envoy
* Etcd
* Prometheus
* NGINX
* Apache

#### **Examples of Detected Misconfigurations**:

* Insecure use of credentials (NGINX credential in config file, credential stored insecurely)
* Enforcement of secure communication (redirecting HTTP to HTTPS, enforcing TLS, TLS version)
* Allowing weak crypto algorithms
* Externally exposing Admin interface
* Un-authenticated access to resources

#### Applications Scans - Application Libraries Misuse <a href="#uuid-58e1bcf7-4260-c0bf-5b4b-32c67d2757a7_bridgehead-idm4599339870576033995583152195" id="uuid-58e1bcf7-4260-c0bf-5b4b-32c67d2757a7_bridgehead-idm4599339870576033995583152195"></a>

JFrog Advanced Security detects misconfigurations and insecure usage of libraries and services within your containers. Supporting **Python** and **Node.js**, JFrog Advanced Security scans for issues like excessive privileges, insecure communication, and unsafe cryptographic operations.

**Examples of Detected Issues**:

* Insecure use of credentials (insecure key storage)
* Enforcement of secure communication (redirecting HTTP to HTTPS, enforcing TLS, verifying the TLS certificates of all servers in Python scripts, enforcing TLS version, using secure HTTP headers)
* Use of weak crypto keys
* Throttle logins to prevent brute-force attacks (Throttle Node.js logins to prevent brute-force attacks)
* Invoking Node.js exec functionality with user-provided input
