# Frogbot

JFrog **Frogbot** is an advanced Git-based bot designed to elevate software development security by automatically scanning source code in Git repositories for various vulnerabilities. Acting as a project gatekeeper, Frogbot continuously monitors your code to detect potential security threats.

Frogbot conducts thorough scans that uncover a range of concerns, including Static Application Security Testing (SAST) vulnerabilities, Software Composition Analysis (SCA) findings, secrets exposure, and CVE Contextual Analysis. When new security issues are identified in pull requests, Frogbot proactively comments to alert developers, ensuring that only secure code is merged. Furthermore, it can automatically generate pull requests with proposed fixes for SCA vulnerabilities, streamlining the remediation process and helping teams maintain secure and compliant dependencies.

Integrating Frogbot into your development lifecycle allows you to proactively enforce security policies, thereby protecting your project from the outset. While Frogbot plays a critical role in maintaining security at the repository level, it is advisable for developers to also scan their code within their IDEs before committing changes. This complementary approach enables teams to identify and address vulnerabilities early, leading to a more robust security posture.

### Before You Begin

It is essential that you:

* Meet the [system requirements](../)
