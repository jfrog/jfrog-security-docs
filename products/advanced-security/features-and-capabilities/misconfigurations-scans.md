# Misconfigurations Scans

#### Services Scans - Services Configuration Security <a href="#uuid-58e1bcf7-4260-c0bf-5b4b-32c67d2757a7_bridgehead-idm455673167603843399558218115" id="uuid-58e1bcf7-4260-c0bf-5b4b-32c67d2757a7_bridgehead-idm455673167603843399558218115"></a>

Detects whether common OSS libraries and services are configured securely, so an application can be easily hardened by default.

Xray scans for configuration issues and security malpractices for specific services and daemons included in your artifacts, such as web servers, database services, proxies, logging daemons, and so on.

#### Note

Supported Services:

* Envoy
* Etcd
* Prometheus
* NGINX
* Apache
* Insecure use of credentials (NGINX credential in config file, credential stored insecurely)
* Enforcement of secure communication (redirecting HTTP to HTTPS, enforcing TLS, TLS version)
* Allowing weak crypto algorithms
* Externally exposing Admin interface
* Un-authenticated access to resources

#### Applications Scans - Application Libraries Misuse <a href="#uuid-58e1bcf7-4260-c0bf-5b4b-32c67d2757a7_bridgehead-idm4599339870576033995583152195" id="uuid-58e1bcf7-4260-c0bf-5b4b-32c67d2757a7_bridgehead-idm4599339870576033995583152195"></a>

Detects whether common OSS libraries and services are used securely by the application.

Xray scans for configuration issues, security malpractices, and insecure usage of common OSS libraries in your application framework, including the use of excessive privileges, insecure communication methods, insufficient authorization mechanisms, or unsafe cryptographic operations.

#### Note

In this version, only Python and Node-JS applications are supported.

**Examples**:

* Insecure use of credentials (insecure key storage)
* Enforcement of secure communication (redirecting HTTP to HTTPS, enforcing TLS, verifying the TLS certificates of all servers in Python scripts, enforcing TLS version, using secure HTTP headers)
* Use of weak crypto keys
* Throttle logins to prevent brute-force attacks (Throttle Node.js logins to prevent brute-force attacks)
* Invoking Node.js exec functionality with user-provided input

#### IaC Scans - IaC Security Analysis <a href="#uuid-58e1bcf7-4260-c0bf-5b4b-32c67d2757a7_bridgehead-idm4516530813920033995584528292" id="uuid-58e1bcf7-4260-c0bf-5b4b-32c67d2757a7_bridgehead-idm4516530813920033995584528292"></a>

Scans IaC files stored in Artifactory for early detection of cloud and infrastructure misconfigurations to prevent attacks and data leak.

Xray scans your Terraform state in Artifactory for Cloud services configuration issues such as the following examples. Xray scans Terraform states for AWS, Azure and GCP cloud services.

**Examples**:

* Insufficient access restrictions to services (public access to repositories, publicly accessible clusters, globally readable/deletable/writeable buckets, use of admin roles in ECS services, IAM users with privileged access to all resources, enforce authorization for all API Gateway methods)
* Insecure use of credentials (use of hardcoded credentials)
* Allowing weak crypto algorithms (use of weak cipher suites)
* Running batches in privileged mode
* Enforcement of secure communication (listening to HTTP, unencrypted communications)
* Wildcard actions in Glue policies
* Missing logging (e.g., found CloudTrail trails with logging disabled)
* Disabled upgrades (e.g., RDS database instance with disabled minor engine upgrades)
* Data at rest encryption enablement for Kinesis streams
