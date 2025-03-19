# Preventing Supply Chain Attacks in a DevOps Pipeline - example

A software development team is using multiple open-source dependencies in their applications. They need to ensure that no vulnerabilities, malicious code, or license compliance issues enter their supply chain during development, testing, and deployment.

**JFrog Advanced Security Solution**

JFrog’s advanced security capabilities integrate seamlessly into the SDLC, providing automated security scans, policy enforcement, and real-time threat detection.

**Utilization Across the SDLC**

1. **Code & Build Phase:**
   * JFrog Xray scans source code and dependencies for known vulnerabilities (CVEs) and malware.
   * If a high-severity issue is detected, the build is blocked, preventing it from advancing to the next stage.
   * Developers receive immediate alerts and remediation guidance.
2. **Repository & Artifact Management:**
   * Scans binaries stored in JFrog Artifactory to ensure no artifacts contain critical security risks.
   * Ensures compliance by enforcing security policies before promoting artifacts to staging or production.
3. **Testing & Integration:**
   * Automatically scans container images for security risks before they are pushed to production.
   * Detects misconfigurations (e.g., exposed secrets, weak authentication settings) in infrastructure-as-code files.
4. **Deployment & Runtime Security:**
   * Integrates with CI/CD pipelines to enforce security policies before deployment.
   * Monitors deployed applications for newly discovered vulnerabilities and provides actionable insights.
