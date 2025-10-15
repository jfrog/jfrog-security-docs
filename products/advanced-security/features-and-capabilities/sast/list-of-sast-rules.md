# List of SAST Rules

JFrog SAST offers a comprehensive set of rules designed to identify security vulnerabilities across your codebase. These rules are mapped to the OWASP Top 10 vulnerabilities, as well as additional critical security issues beyond the OWASP Top 10. The mapping provides clear visibility into which specific vulnerabilities are being addressed and how they align with widely recognized security standards. In this section, you’ll find a detailed table of the SAST rules, and their corresponding OWASP categories, helping you better understand how JFrog SAST ensures your code is protected against the most critical security risks.

* [Python](list-of-sast-rules.md#python)
* [Java](list-of-sast-rules.md#java)
* [JavaScript](list-of-sast-rules.md#javascript)
* [Go](list-of-sast-rules.md#go)
* [C/C++](list-of-sast-rules.md#c-c)
* [C#](list-of-sast-rules.md#c)
* [Rust](list-of-sast-rules.md#rust)
* [PHP](list-of-sast-rules.md#php)

#### Python

| Rule id                                         | Severity | CWE      | OWASP top 10 (2021) |
| ----------------------------------------------- | -------- | -------- | ------------------- |
| python-code-injection                           | high     | CWE-94   | A03                 |
| python-command-injection                        | high     | CWE-78   | A03                 |
| python-ldap-injection                           | high     | CWE-90   | A03                 |
| python-process-control                          | high     | CWE-114  |                     |
| python-stored-code-injection                    | high     | CWE-94   | A03                 |
| python-stored-command-injection                 | high     | CWE-78   | A03                 |
| python-stored-ldap                              | high     | CWE-90   | A03                 |
| python-sql-injection                            | high     | CWE-89   | A03                 |
| python-unsafe-deserialization                   | high     | CWE-502  | A08                 |
| python-xss                                      | high     | CWE-79   | A03                 |
| python-prompt-injection-rce                     | high     |          |                     |
| python-deno-insecure-permissions                | high     | CWE-276  | A01                 |
| python-docker-cli-privileged                    | high     | CWE-250  |                     |
| python-podman-cli-privileged                    | high     | CWE-250  |                     |
| python-firejail-noprofile                       | high     | CWE-693  |                     |
| python-firejail-debuggers-allowed               | high     | CWE-693  |                     |
| python-nsjail-host-filesystem-access            | high     | CWE-22   | A01                 |
| python-nsjail-privilege-escalation              | high     | CWE-269  | A04                 |
| python-bwrap-root-binding                       | high     | CWE-22   | A01                 |
| python-flatpak-host-filesystem-access           | high     | CWE-22   | A01                 |
| python-systemd-nspawn-root-bind                 | high     | CWE-22   | A01                 |
| python-smolagents-local-rce                     | high     | CWE-94   | A03                 |
| python-docker-sdk-privileged                    | high     | CWE-250  |                     |
| python-docker-sdk-socket-mount                  | high     | CWE-250  |                     |
| python-jinja2-escape-by-modification            | high     | CWE-94   | A03                 |
| python-pyyaml-unsafe-deserialization            | high     | CWE-502  | A08                 |
| python-eval-globals-injection                   | high     | CWE-94   | A03                 |
| python-jinja2-globals-injection                 | high     | CWE-94   | A03                 |
| python-evaluator-function-injection             | high     | CWE-94   | A03                 |
| python-cookie-poisoning                         | medium   | CWE-472  | A04                 |
| python-db-connection-string-injection           | medium   | CWE-99   | A03                 |
| python-dos-by-sleep                             | medium   | CWE-400  |                     |
| python-elevate-access-privileges                | medium   | CWE-284  | A01                 |
| python-http-header-injection                    | medium   | CWE-644  | A03                 |
| python-inadequate-padding                       | medium   | CWE-780  | A02                 |
| python-insecure-random                          | medium   | CWE-338  | A02                 |
| python-insecure-websocket                       | medium   | CWE-1385 |                     |
| python-no-encryption-in-connection-string       | medium   | CWE-319  | A02                 |
| python-password-in-cookie                       | medium   | CWE-200  | A01                 |
| python-path-traversal                           | medium   | CWE-22   | A01                 |
| python-redos                                    | medium   | CWE-1333 |                     |
| python-regex-injection                          | medium   | CWE-625  |                     |
| python-response-splitting                       | medium   | CWE-113  | A03                 |
| python-2nd-order-sql-injection                  | medium   | CWE-89   | A03                 |
| python-short-crypto-key                         | medium   | CWE-326  | A02                 |
| python-stored-path-traversal                    | medium   | CWE-22   | A01                 |
| python-stored-xpath                             | medium   | CWE-643  | A03                 |
| python-stored-xss                               | medium   | CWE-79   | A03                 |
| python-ssrf                                     | medium   | CWE-918  | A10                 |
| python-ssti                                     | medium   | CWE-1336 |                     |
| python-weak-crypto-algorithm                    | medium   | CWE-327  | A02                 |
| python-weak-ssl-protocol                        | medium   | CWE-327  | A02                 |
| python-xml-injection                            | medium   | CWE-91   | A03                 |
| python-xpath-injection                          | medium   | CWE-643  | A03                 |
| python-xslt-injection                           | medium   | CWE-91   | A03                 |
| python-xxe                                      | medium   | CWE-611  | A05                 |
| python-tainted-os-command                       | medium   | CWE-78   | A03                 |
| python-stored-tainted-os-command                | medium   | CWE-78   | A03                 |
| python-environment-variable-injection           | medium   | CWE-74   | A03                 |
| python-unicode-case-mapping                     | medium   | CWE-178  |                     |
| python-missing-ssl-validation                   | medium   | CWE-295  | A07                 |
| python-unsafe-hash                              | medium   | CWE-328  | A02                 |
| python-flask-debug                              | medium   | CWE-1295 |                     |
| python-firejail-debug-mode                      | medium   | CWE-200  | A01                 |
| python-nsjail-network-sharing                   | medium   | CWE-284  | A01                 |
| python-nsjail-proc-writable                     | medium   | CWE-693  |                     |
| python-bwrap-network-sharing                    | medium   | CWE-284  | A01                 |
| python-chroot-misuse                            | medium   | CWE-693  |                     |
| python-docker-sdk-host-network                  | medium   | CWE-284  | A01                 |
| python-hardcoded-credentials                    | low      | CWE-798  | A07                 |
| python-insecure-port                            | low      | CWE-319  | A02                 |
| python-insecure-protocol                        | low      | CWE-319  | A02                 |
| python-open-redirect                            | low      | CWE-601  | A01                 |
| python-potential-redos                          | low      | CWE-1333 |                     |
| python-stored-cookie-poisoning                  | low      | CWE-472  | A04                 |
| python-stored-http-header-injection             | low      | CWE-644  | A03                 |
| python-stored-redirect                          | low      | CWE-601  | A01                 |
| python-stored-response-splitting                | low      | CWE-113  | A03                 |
| python-stack-trace-exposure                     | low      | CWE-209  | A04                 |
| python-parameter-injection                      | low      | CWE-88   | A03                 |
| python-stored-parameter-injection               | low      | CWE-88   | A03                 |
| python-stored-environment-variable-injection    | low      | CWE-74   | A03                 |
| python-externally-controllable-file-permissions | low      | CWE-732  |                     |
| python-weak-file-permissions                    | low      | CWE-732  |                     |

#### Java

| Rule id                                 | Severity | CWE      | OWASP top 10 (2021) |
| --------------------------------------- | -------- | -------- | ------------------- |
| java-code-injection                     | high     | CWE-94   | A03                 |
| java-command-injection                  | high     | CWE-78   | A03                 |
| java-ldap-injection                     | high     | CWE-90   | A03                 |
| java-process-control                    | high     | CWE-114  |                     |
| java-sql-injection                      | high     | CWE-89   | A03                 |
| java-stored-code-injection              | high     | CWE-94   | A03                 |
| java-stored-command-injection           | high     | CWE-78   | A03                 |
| java-stored-ldap                        | high     | CWE-90   | A03                 |
| java-unsafe-deserialization             | high     | CWE-502  | A08                 |
| java-xss                                | high     | CWE-79   | A03                 |
| java-jndi-injection                     | high     | CWE-642  | A04                 |
| java-cookie-poisoning                   | medium   | CWE-472  | A04                 |
| java-db-connection-string-injection     | medium   | CWE-99   | A03                 |
| java-dos-by-sleep                       | medium   | CWE-400  |                     |
| java-elevate-access-privileges          | medium   | CWE-284  | A01                 |
| java-http-header-injection              | medium   | CWE-644  | A03                 |
| java-inadequate-padding                 | medium   | CWE-780  | A02                 |
| java-insecure-random                    | medium   | CWE-338  | A02                 |
| java-insecure-websocket                 | medium   | CWE-1385 |                     |
| java-no-encryption-in-connection-string | medium   | CWE-319  | A02                 |
| java-password-in-cookie                 | medium   | CWE-200  | A01                 |
| java-path-traversal                     | medium   | CWE-22   | A01                 |
| java-redos                              | medium   | CWE-1333 |                     |
| java-regex-injection                    | medium   | CWE-625  |                     |
| java-response-splitting                 | medium   | CWE-113  | A03                 |
| java-2nd-order-sql-injection            | medium   | CWE-89   | A03                 |
| java-short-crypto-key                   | medium   | CWE-326  | A02                 |
| java-ssrf                               | medium   | CWE-918  | A10                 |
| java-ssti                               | medium   | CWE-1336 |                     |
| java-stored-path-traversal              | medium   | CWE-22   | A01                 |
| java-stored-reflection                  | medium   | CWE-470  | A03                 |
| java-stored-xpath                       | medium   | CWE-643  | A03                 |
| java-stored-xss                         | medium   | CWE-79   | A03                 |
| java-reflection                         | medium   | CWE-470  | A03                 |
| java-weak-crypto-algorithm              | medium   | CWE-327  | A02                 |
| java-weak-ssl-protocol                  | medium   | CWE-327  | A02                 |
| java-xml-injection                      | medium   | CWE-91   | A03                 |
| java-xpath-injection                    | medium   | CWE-643  | A03                 |
| java-xslt-injection                     | medium   | CWE-91   | A03                 |
| java-xxe                                | medium   | CWE-611  | A05                 |
| java-unsafe-certificate                 | medium   | CWE-295  | A07                 |
| java-misconfig                          | medium   | CWE-933  |                     |
| java-stored-misconfig                   | medium   | CWE-933  |                     |
| java-hardcoded-credentials              | low      | CWE-798  | A07                 |
| java-insecure-port                      | low      | CWE-319  | A02                 |
| java-insecure-protocol                  | low      | CWE-319  | A02                 |
| java-open-redirect                      | low      | CWE-601  | A01                 |
| java-potential-redos                    | low      | CWE-1333 |                     |
| java-stack-trace-exposure               | low      | CWE-209  | A04                 |
| java-stored-cookie-poisoning            | low      | CWE-472  | A04                 |
| java-stored-http-header-injection       | low      | CWE-644  | A03                 |
| java-stored-redirect                    | low      | CWE-601  | A01                 |
| java-stored-response-splitting          | low      | CWE-113  | A03                 |
| java-stored-trust-boundary              | low      | CWE-501  | A04                 |
| java-trust-boundary                     | low      | CWE-501  | A04                 |
| java-javascript-enabled                 | low      | CWE-749  |                     |

#### JavaScript

| Rule id                               | Severity | CWE      | OWASP top 10 (2021) |
| ------------------------------------- | -------- | -------- | ------------------- |
| js-archive-slip                       | high     | CWE-22   | A01                 |
| js-code-injection                     | high     | CWE-94   | A03                 |
| js-command-injection                  | high     | CWE-78   | A03                 |
| js-ldap-injection                     | high     | CWE-90   | A03                 |
| js-process-control                    | high     | CWE-114  |                     |
| js-sql-injection                      | high     | CWE-89   | A03                 |
| js-unsafe-deserialization             | high     | CWE-502  | A08                 |
| js-xss                                | high     | CWE-79   | A03                 |
| js-template-injection                 | high     | CWE-73   | A04                 |
| js-dom-based-xss                      | high     | CWE-79   | A03                 |
| js-dom-xss-angular                    | high     | CWE-79   | A03                 |
| js-cookie-poisoning                   | medium   | CWE-472  | A04                 |
| js-db-connection-string-injection     | medium   | CWE-99   | A03                 |
| js-dos-by-sleep                       | medium   | CWE-400  |                     |
| js-elevate-access-privileges          | medium   | CWE-284  | A01                 |
| js-http-header-injection              | medium   | CWE-644  | A03                 |
| js-inadequate-padding                 | medium   | CWE-780  | A02                 |
| js-insecure-random                    | medium   | CWE-338  | A02                 |
| js-insecure-websocket                 | medium   | CWE-1385 |                     |
| js-no-encryption-in-connection-string | medium   | CWE-319  | A02                 |
| js-password-in-cookie                 | medium   | CWE-200  | A01                 |
| js-path-traversal                     | medium   | CWE-22   | A01                 |
| js-redos                              | medium   | CWE-1333 |                     |
| js-regex-injection                    | medium   | CWE-625  |                     |
| js-response-splitting                 | medium   | CWE-113  | A03                 |
| js-short-crypto-key                   | medium   | CWE-326  | A02                 |
| js-ssrf                               | medium   | CWE-918  | A10                 |
| js-ssti                               | medium   | CWE-1336 |                     |
| js-weak-crypto-algorithm              | medium   | CWE-327  | A02                 |
| js-weak-ssl-protocol                  | medium   | CWE-327  | A02                 |
| js-xml-injection                      | medium   | CWE-91   | A03                 |
| js-xpath-injection                    | medium   | CWE-643  | A03                 |
| js-xslt-injection                     | medium   | CWE-91   | A03                 |
| js-xxe                                | medium   | CWE-611  | A05                 |
| js-helper                             | medium   |          |                     |
| js-lfi                                | medium   | CWE-98   | A03                 |
| js-remote-param-injection             | medium   | CWE-88   | A03                 |
| js-unsafe-hash                        | medium   | CWE-328  | A02                 |
| js-insecure-cookie                    | medium   | CWE-614  | A05                 |
| js-http-only                          | medium   | CWE-1004 | A05                 |
| js-improper-samesite                  | medium   | CWE-1275 | A01                 |
| js-prototype-pollution                | medium   | CWE-1321 |                     |
| js-hardcoded-credentials              | low      | CWE-798  | A07                 |
| js-insecure-port                      | low      | CWE-319  | A02                 |
| js-insecure-protocol                  | low      | CWE-319  | A02                 |
| js-open-redirect                      | low      | CWE-601  | A01                 |
| js-potential-redos                    | low      | CWE-1333 |                     |
| js-stack-trace-exposure               | low      | CWE-209  | A04                 |
| js-weak-json-token-encrypt            | low      | CWE-347  | A02                 |
| js-dom-based-open-redirect            | low      | CWE-601  | A01                 |
| js-express-without-helmet             | low      | CWE-693  |                     |
| js-cors-misconfig                     | low      | CWE-942  | A05                 |

#### Go

| Rule id                               | Severity | CWE      | OWASP top 10 (2021) |
| ------------------------------------- | -------- | -------- | ------------------- |
| go-code-injection                     | high     | CWE-94   | A03                 |
| go-command-injection                  | high     | CWE-78   | A03                 |
| go-process-control                    | high     | CWE-114  |                     |
| go-sql-injection                      | high     | CWE-89   | A03                 |
| go-stored-code-injection              | high     | CWE-94   | A03                 |
| go-stored-command-injection           | high     | CWE-78   | A03                 |
| go-unsafe-deserialization             | high     | CWE-502  | A08                 |
| go-xss                                | high     | CWE-79   | A03                 |
| go-improper-certificate-validation    | high     | CWE-295  | A07                 |
| go-insecure-tls                       | high     | CWE-295  | A07                 |
| go-cookie-poisoning                   | medium   | CWE-472  | A04                 |
| go-db-connection-string-injection     | medium   | CWE-99   | A03                 |
| go-dos-by-sleep                       | medium   | CWE-400  |                     |
| go-elevate-access-privileges          | medium   | CWE-284  | A01                 |
| go-inadequate-padding                 | medium   | CWE-780  | A02                 |
| go-insecure-random                    | medium   | CWE-338  | A02                 |
| go-insecure-websocket                 | medium   | CWE-1385 |                     |
| go-no-encryption-in-connection-string | medium   | CWE-319  | A02                 |
| go-password-in-cookie                 | medium   | CWE-200  | A01                 |
| go-path-traversal                     | medium   | CWE-22   | A01                 |
| go-redos                              | medium   | CWE-1333 |                     |
| go-regex-injection                    | medium   | CWE-625  |                     |
| go-2nd-order-sql-injection            | medium   | CWE-89   | A03                 |
| go-short-crypto-key                   | medium   | CWE-326  | A02                 |
| go-ssrf                               | medium   | CWE-918  | A10                 |
| go-ssti                               | medium   | CWE-1336 |                     |
| go-stored-path-traversal              | medium   | CWE-22   | A01                 |
| go-stored-xpath                       | medium   | CWE-643  | A03                 |
| go-stored-xss                         | medium   | CWE-79   | A03                 |
| go-weak-crypto-algorithm              | medium   | CWE-327  | A02                 |
| go-weak-ssl-protocol                  | medium   | CWE-327  | A02                 |
| go-xml-injection                      | medium   | CWE-91   | A03                 |
| go-xpath-injection                    | medium   | CWE-643  | A03                 |
| go-xxe                                | medium   | CWE-611  | A05                 |
| go-helper                             | medium   |          |                     |
| go-cleartext-logging                  | medium   | CWE-312  | A04                 |
| go-weak-password-recovery             | medium   | CWE-640  | A07                 |
| go-hardcoded-credentials              | low      | CWE-798  | A07                 |
| go-insecure-port                      | low      | CWE-319  | A02                 |
| go-insecure-protocol                  | low      | CWE-319  | A02                 |
| go-open-redirect                      | low      | CWE-601  | A01                 |
| go-potential-redos                    | low      | CWE-1333 |                     |
| go-stack-trace-exposure               | low      | CWE-209  | A04                 |
| go-stored-cookie-poisoning            | low      | CWE-472  | A04                 |
| go-stored-redirect                    | low      | CWE-601  | A01                 |
| go-parameter-injection                | low      | CWE-88   | A03                 |
| go-key-past-expiration                | low      | CWE-322  | A02                 |

#### C/C++

| Rule id                                | Severity | CWE      | OWASP top 10 (2021) |
| -------------------------------------- | -------- | -------- | ------------------- |
| cpp-classic-buffer-overflow            | high     | CWE-120  |                     |
| cpp-command-injection                  | high     | CWE-78   | A03                 |
| cpp-process-control                    | high     | CWE-114  |                     |
| cpp-sql-injection                      | high     | CWE-89   | A03                 |
| cpp-stored-command-injection           | high     | CWE-78   | A03                 |
| cpp-unsafe-deserialization             | high     | CWE-502  | A08                 |
| cpp-xss                                | high     | CWE-79   | A03                 |
| cpp-cgi-xss                            | high     | CWE-79   | A03                 |
| cpp-uncontrolled-format-string         | high     | CWE-134  |                     |
| cpp-tainted-write-size                 | high     | CWE-129  |                     |
| cpp-write-buffer-size-mismatch         | high     | CWE-787  |                     |
| cpp-cookie-poisoning                   | medium   | CWE-472  | A04                 |
| cpp-db-connection-string-injection     | medium   | CWE-99   | A03                 |
| cpp-dos-by-sleep                       | medium   | CWE-400  |                     |
| cpp-elevate-access-privileges          | medium   | CWE-284  | A01                 |
| cpp-http-header-injection              | medium   | CWE-644  | A03                 |
| cpp-inadequate-padding                 | medium   | CWE-780  | A02                 |
| cpp-insecure-random                    | medium   | CWE-338  | A02                 |
| cpp-insecure-websocket                 | medium   | CWE-1385 |                     |
| cpp-no-encryption-in-connection-string | medium   | CWE-319  | A02                 |
| cpp-password-in-cookie                 | medium   | CWE-200  | A01                 |
| cpp-path-traversal                     | medium   | CWE-22   | A01                 |
| cpp-redos                              | medium   | CWE-1333 |                     |
| cpp-regex-injection                    | medium   | CWE-625  |                     |
| cpp-response-splitting                 | medium   | CWE-113  | A03                 |
| cpp-2nd-order-sql-injection            | medium   | CWE-89   | A03                 |
| cpp-short-crypto-key                   | medium   | CWE-326  | A02                 |
| cpp-ssrf                               | medium   | CWE-918  | A10                 |
| cpp-ssti                               | medium   | CWE-1336 |                     |
| cpp-stored-path-traversal              | medium   | CWE-22   | A01                 |
| cpp-stored-xss                         | medium   | CWE-79   | A03                 |
| cpp-use-after-free                     | medium   | CWE-416  |                     |
| cpp-weak-crypto-algorithm              | medium   | CWE-327  | A02                 |
| cpp-weak-ssl-protocol                  | medium   | CWE-327  | A02                 |
| cpp-xxe                                | medium   | CWE-611  | A05                 |
| cpp-cgi-stored-xss                     | medium   | CWE-79   | A03                 |
| cpp-tainted-read-size                  | medium   | CWE-129  |                     |
| cpp-read-buffer-size-mismatch          | medium   | CWE-131  |                     |
| cpp-double-free                        | medium   | CWE-415  |                     |
| cpp-unsanitized-alloc-size             | medium   | CWE-789  |                     |
| cpp-tainted-alloc-size                 | medium   | CWE-789  |                     |
| cpp-unsanitized-memory-read-offset     | medium   | CWE-126  |                     |
| cpp-unsanitized-memory-write-offset    | medium   | CWE-125  |                     |
| cpp-tainted-memory-read-offset         | medium   | CWE-126  |                     |
| cpp-tainted-memory-write-offset        | medium   | CWE-125  |                     |
| cpp-improper-certificate-validation    | medium   | CWE-295  | A07                 |
| cpp-hardcoded-credentials              | low      | CWE-798  | A07                 |
| cpp-insecure-port                      | low      | CWE-319  | A02                 |
| cpp-insecure-protocol                  | low      | CWE-319  | A02                 |
| cpp-potential-redos                    | low      | CWE-1333 |                     |
| cpp-stack-trace-exposure               | low      | CWE-209  | A04                 |
| cpp-dangerous-functions                | low      | CWE-242  |                     |
| cpp-off-by-one-in-allocation           | low      | CWE-193  |                     |
| cpp-obsolete-functions                 | internal | CWE-477  |                     |

#### C\#

| Rule id                               | Severity | CWE      | OWASP top 10 (2021) |
| ------------------------------------- | -------- | -------- | ------------------- |
| cs-archive-slip                       | high     | CWE-22   | A01                 |
| cs-code-injection                     | high     | CWE-94   | A03                 |
| cs-command-injection                  | high     | CWE-78   | A03                 |
| cs-ldap-injection                     | high     | CWE-90   | A03                 |
| cs-process-control                    | high     | CWE-114  |                     |
| cs-sql-injection                      | high     | CWE-89   | A03                 |
| cs-stored-code-injection              | high     | CWE-94   | A03                 |
| cs-stored-command-injection           | high     | CWE-78   | A03                 |
| cs-stored-ldap                        | high     | CWE-90   | A03                 |
| cs-unsafe-deserialization             | high     | CWE-502  | A08                 |
| cs-xss                                | high     | CWE-79   | A03                 |
| cs-cookie-poisoning                   | medium   | CWE-472  | A04                 |
| cs-db-connection-string-injection     | medium   | CWE-99   | A03                 |
| cs-dos-by-sleep                       | medium   | CWE-400  |                     |
| cs-elevate-access-privileges          | medium   | CWE-284  | A01                 |
| cs-http-header-injection              | medium   | CWE-644  | A03                 |
| cs-improper-xml-validation            | medium   | CWE-112  |                     |
| cs-inadequate-padding                 | medium   | CWE-780  | A02                 |
| cs-insecure-random                    | medium   | CWE-338  | A02                 |
| cs-insecure-websocket                 | medium   | CWE-1385 |                     |
| cs-no-encryption-in-connection-string | medium   | CWE-319  | A02                 |
| cs-password-in-cookie                 | medium   | CWE-200  | A01                 |
| cs-path-traversal                     | medium   | CWE-22   | A01                 |
| cs-redos                              | medium   | CWE-1333 |                     |
| cs-regex-injection                    | medium   | CWE-625  |                     |
| cs-response-splitting                 | medium   | CWE-113  | A03                 |
| cs-2nd-order-sql-injection            | medium   | CWE-89   | A03                 |
| cs-short-crypto-key                   | medium   | CWE-326  | A02                 |
| cs-ssrf                               | medium   | CWE-918  | A10                 |
| cs-ssti                               | medium   | CWE-1336 |                     |
| cs-stored-path-traversal              | medium   | CWE-22   | A01                 |
| cs-stored-reflection                  | medium   | CWE-470  | A03                 |
| cs-stored-xpath                       | medium   | CWE-643  | A03                 |
| cs-stored-xss                         | medium   | CWE-79   | A03                 |
| cs-reflection                         | medium   | CWE-470  | A03                 |
| cs-weak-crypto-algorithm              | medium   | CWE-327  | A02                 |
| cs-weak-ssl-protocol                  | medium   | CWE-327  | A02                 |
| cs-xml-injection                      | medium   | CWE-91   | A03                 |
| cs-xpath-injection                    | medium   | CWE-643  | A03                 |
| cs-xslt-injection                     | medium   | CWE-91   | A03                 |
| cs-xxe                                | medium   | CWE-611  | A05                 |
| cs-debug-logging-tracing-enabled      | medium   | CWE-1295 |                     |
| cs-hardcoded-credentials              | low      | CWE-798  | A07                 |
| cs-insecure-port                      | low      | CWE-319  | A02                 |
| cs-insecure-protocol                  | low      | CWE-319  | A02                 |
| cs-open-redirect                      | low      | CWE-601  | A01                 |
| cs-potential-redos                    | low      | CWE-1333 |                     |
| cs-stack-trace-exposure               | low      | CWE-209  | A04                 |
| cs-stored-cookie-poisoning            | low      | CWE-472  | A04                 |
| cs-stored-http-header-injection       | low      | CWE-644  | A03                 |
| cs-stored-redirect                    | low      | CWE-601  | A01                 |
| cs-stored-response-splitting          | low      | CWE-113  | A03                 |

#### Rust

| Rule id                                | Severity | CWE      | OWASP top 10 (2021) |
| -------------------------------------- | -------- | -------- | ------------------- |
| rust-classic-buffer-overflow           | high     | CWE-120  |                     |
| rust-command-injection                 | high     | CWE-78   | A03                 |
| rust-redis-lua-script-injection        | high     | CWE-94   | A03                 |
| rust-sql-injection                     | high     | CWE-89   | A03                 |
| rust-stored-command-injection          | high     | CWE-78   | A03                 |
| rust-unsafe-deserialization            | high     | CWE-502  | A08                 |
| rust-xss                               | high     | CWE-79   | A03                 |
| rust-elevate-access-privileges         | medium   | CWE-284  | A01                 |
| rust-insecure-websocket                | medium   | CWE-1385 |                     |
| rust-nosql-injection                   | medium   | CWE-89   | A03                 |
| rust-path-traversal                    | medium   | CWE-22   | A01                 |
| rust-2nd-order-sql-injection           | medium   | CWE-89   | A03                 |
| rust-ssrf                              | medium   | CWE-918  | A10                 |
| rust-stored-path-traversal             | medium   | CWE-22   | A01                 |
| rust-stored-redis-lua-script-injection | medium   | CWE-94   | A03                 |
| rust-stored-xss                        | medium   | CWE-79   | A03                 |
| rust-use-after-free                    | medium   | CWE-416  |                     |
| rust-hardcoded-credentials             | low      | CWE-798  | A07                 |
| rust-insecure-port                     | low      | CWE-319  | A02                 |
| rust-insecure-protocol                 | low      | CWE-319  | A02                 |
| rust-stored-nosql-injection            | low      | CWE-89   | A03                 |

#### PHP

| Rule id                                | Severity | CWE     | OWASP top 10 (2021) |
| -------------------------------------- | -------- | ------- | ------------------- |
| php-code-injection                     | high     | CWE-94  | A03                 |
| php-command-injection                  | high     | CWE-78  | A03                 |
| php-sql-injection                      | high     | CWE-89  | A03                 |
| php-stored-code-injection              | high     | CWE-94  | A03                 |
| php-stored-command-injection           | high     | CWE-78  | A03                 |
| php-xss                                | high     | CWE-79  | A03                 |
| php-dos-by-sleep                       | medium   | CWE-400 |                     |
| php-insecure-random                    | medium   | CWE-338 | A02                 |
| php-no-encryption-in-connection-string | medium   | CWE-319 | A02                 |
| php-path-traversal                     | medium   | CWE-22  | A01                 |
| php-2nd-order-sql-injection            | medium   | CWE-89  | A03                 |
| php-ssrf                               | medium   | CWE-918 | A10                 |
| php-stored-path-traversal              | medium   | CWE-22  | A01                 |
| php-stored-xss                         | medium   | CWE-79  | A03                 |
| php-xxe                                | medium   | CWE-611 | A05                 |
| php-hardcoded-credentials              | low      | CWE-798 | A07                 |
| php-insecure-protocol                  | low      | CWE-319 | A02                 |
| php-insecure-port                      | low      | CWE-319 | A02                 |
| php-open-redirect                      | low      | CWE-601 | A01                 |
| php-stack-trace-exposure               | low      | CWE-209 | A04                 |
| php-stored-redirect                    | low      | CWE-601 | A01                 |
