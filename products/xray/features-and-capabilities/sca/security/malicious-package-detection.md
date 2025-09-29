# Malicious Package Detection

JFrog’s Xray detects malicious software packages based on artifact scanning. This feature is based on a robust package scanning mechanism automatically scans packages uploaded to public open-source software repositories. It is designed to detect potential security risks and malicious code in various open-source software packages.

### Scan Architecture <a href="#gn5dc2c0a135" id="gn5dc2c0a135"></a>

![](<../../../../../.gitbook/assets/0 (6).png>)

JFrog developed a set of automated scanners that run on each new package created or updated in all of the supported software repositories. These scanners produce a "maliciousness score" on each package.

If the score is extremely high, the package is automatically added as malicious to Xray's database and is disclosed to the public repository maintainer. In this case, the package appears as malicious in Xray's cloud environment in \~2-4 hours (from the time it was created/updated).

If the score is somewhat high, the package is deferred for manual inspection by one of JFrog's dedicated researchers, and after careful evaluation, it is either marked as malicious or clean. In case the package is malicious, Xray's cloud environment will be updated in \~1-3 days since the package was initially scanned.

If the maliciousness score is low - the package is deemed to be safe.

An updated list of all packages that were discovered and disclosed by JFrog's scanners & research team is available here -[ https://research.jfrog.com/malicious-packages](https://research.jfrog.com/malicious-packages).

In addition to JFrog's automated scanners, the Xray database is updated with malicious packages from two additional sources:

* Open-source malicious package DBs, such as the[ one curated by OpenSSF](https://github.com/ossf/malicious-packages).
* JFrog's dedicated malware research team performs a daily audit of all new malware attacks and third-party disclosures, to update the Xray DB with newly-discovered threats.

### Which malicious code patterns can be identified by JFrog's scanners? <a href="#w9t9tlyjem4a" id="w9t9tlyjem4a"></a>

JFrog employs many automated scanners that attempt to find the following payload patterns:

(Note that each mentioned payload may have a few specific scanners, one for each implementation)

* Code obfuscation
* Domain name generation
* Dynamic code evaluation (Ex. eval() in Python)
* Download and Execute payloads
* Shell-popping payloads (either listening or connectback)
* Access to sensitive files (ex. /etc/shadow or the browser's saved passwords cache)
* Environment variable stealing
* PII stealing
* Cryptomining
* Usage of popular exfiltration services (ex. Pipedream)

In addition, scanners exist that identify malicious packages via the following metadata patterns:

* Dependency confusion (ex. very high version numbers)
* Typosquatting (package name is very similar to an existing package name)
* Running code immediately on package installation

The above scanners are used in conjunction to build a "maliciousness score" automatically for each new public package.

### Supported Software Repositories <a href="#id-22u1iua6uj12" id="id-22u1iua6uj12"></a>

JFrog currently supports alerting on malicious package usage from the following public repositories -

* [npm](https://www.npmjs.com/) - Packages are continuously polled, scanned and reported to Xray DB.
* [PyPI](https://pypi.org/) - Packages are continuously polled, scanned and reported to Xray DB.
* [Hugging Face](https://huggingface.co/) - ML Models are continuously scanned (via Webhook push notification) and reported to Xray DB. See more information in "[Scanning Malicious AI Models](https://jfrog.com/help/r/jfrog-security-documentation/scanning-malicious-ai-models)"\

* [NuGet](https://nuget.org/) - Well-known coverage - Only well-known malicious packages are reported to Xray DB.
* [Docker Hub](https://hub.docker.com/) - Well-known coverage - Only well-known malicious packages are reported to Xray DB.
* [Maven](https://mvnrepository.com/) - Well-known coverage - Only well-known malicious packages are reported to Xray DB.
* [RubyGems](https://rubygems.org/) - Well-known coverage - Only well-known malicious packages are reported to Xray DB.
* [Crates.io](https://crates.io/) - Well-known coverage - Only well-known malicious packages are reported to Xray DB.

### Non-covered repositories and well-known coverage only <a href="#xxbdaxadluul" id="xxbdaxadluul"></a>

**Non-covered repositories:** Xray currently does not support alerting on malicious packages from several repositories, for example CocoaPods.

**Repositories with well-known coverage only:** For other repositories (most notably Maven) known malicious packages will be highlighted by Xray, but the repository itself is not continuously scanned for new malicious packages.

The decision to not cover (or partially cover) the above repositories was made since our research showed there is zero or a negligible amount of malicious packages uploaded to these repositories.
