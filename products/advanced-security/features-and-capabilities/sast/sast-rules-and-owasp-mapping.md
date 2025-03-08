# SAST Rules and OWASP Mapping

JFrog SAST offers a comprehensive set of rules designed to identify security vulnerabilities across your codebase. These rules are mapped to the OWASP Top 10 vulnerabilities, as well as additional critical security issues beyond the OWASP Top 10. The mapping provides clear visibility into which specific vulnerabilities are being addressed and how they align with widely recognized security standards. In this section, you’ll find a detailed table of the SAST rules, and their corresponding OWASP categories, helping you better understand how JFrog SAST ensures your code is protected against the most critical security risks.

| Jfrog rule                                      | CWE string | OWASP Top 10 mapping |
| ----------------------------------------------- | ---------- | -------------------- |
| cpp-xxe                                         | CWE-611    | A01                  |
| cs-stored-response-splitting                    | CWE-113    | A01                  |
| js-db-connection-string-injection               | CWE-99     | A01                  |
| js-xss                                          | CWE-79     | A01                  |
| js-insecure-random                              | CWE-338    | A01                  |
| js-dos-by-sleep                                 | CWE-400    | A01                  |
| go-password-in-cookie                           | CWE-200    | A01                  |
| js-weak-crypto-algorithm                        | CWE-327    | A01                  |
| go-insecure-random                              | CWE-338    | A01                  |
| cs-ssti                                         | CWE-1336   | A01                  |
| python-weak-ssl-protocol                        | CWE-327    | A01                  |
| java-xpath-injection                            | CWE-643    | A01                  |
| python-unicode-case-mapping                     | CWE-178    | A01                  |
| python-regex-injection                          | CWE-625    | A01                  |
| java-dos-by-sleep                               | CWE-400    | A01                  |
| java-redos                                      | CWE-1333   | A01                  |
| java-trust-boundary                             | CWE-501    | A01                  |
| java-hardcoded-credentials                      | CWE-798    | A01                  |
| java-sql-injection                              | CWE-89     | A01                  |
| js-ssti                                         | CWE-1336   | A01                  |
| java-xss                                        | CWE-79     | A01                  |
| python-password-in-cookie                       | CWE-200    | A01                  |
| js-xslt-injection                               | CWE-91     | A01                  |
| cpp-write-buffer-size-mismatch                  | CWE-787    | A01                  |
| js-template-injection                           | CWE-73     | A01                  |
| go-insecure-protocol                            | CWE-319    | A01                  |
| cs-hardcoded-credentials                        | CWE-798    | A01                  |
| cs-dos-by-sleep                                 | CWE-400    | A01                  |
| cpp-tainted-alloc-size                          | CWE-789    | A02                  |
| cpp-improper-certificate-validation             | CWE-295    | A02                  |
| go-weak-crypto-algorithm                        | CWE-327    | A02                  |
| python-db-connection-string-injection           | CWE-99     | A02                  |
| go-2nd-order-sql-injection                      | CWE-89     | A02                  |
| cpp-ssti                                        | CWE-1336   | A02                  |
| java-xxe                                        | CWE-611    | A02                  |
| cs-stored-command-injection                     | CWE-78     | A02                  |
| js-dom-xss-angular                              | CWE-79     | A02                  |
| java-short-crypto-key                           | CWE-326    | A02                  |
| cs-stored-http-header-injection                 | CWE-644    | A02                  |
| java-misconfig                                  | CWE-933    | A02                  |
| cs-stack-trace-exposure                         | CWE-209    | A02                  |
| java-stored-code-injection                      | CWE-94     | A02                  |
| cs-cookie-poisoning                             | CWE-472    | A02                  |
| java-weak-ssl-protocol                          | CWE-327    | A02                  |
| go-improper-certificate-validation              | CWE-295    | A02                  |
| cs-open-redirect                                | CWE-601    | A02                  |
| js-weak-ssl-protocol                            | CWE-327    | A02                  |
| java-stored-redirect                            | CWE-601    | A02                  |
| js-weak-json-token-encrypt                      | CWE-347    | A02                  |
| python-code-injection                           | CWE-94     | A02                  |
| cs-stored-code-injection                        | CWE-94     | A02                  |
| go-redos                                        | CWE-1333   | A02                  |
| cs-xss                                          | CWE-79     | A02                  |
| java-stored-reflection                          | CWE-470    | A02                  |
| java-stored-response-splitting                  | CWE-113    | A02                  |
| cpp-redos                                       | CWE-1333   | A02                  |
| java-ssrf                                       | CWE-918    | A02                  |
| cs-unsafe-deserialization                       | CWE-502    | A02                  |
| go-regex-injection                              | CWE-625    | A02                  |
| go-stored-xss                                   | CWE-79     | A02                  |
| cs-stored-reflection                            | CWE-470    | A02                  |
| go-short-crypto-key                             | CWE-326    | A02                  |
| js-short-crypto-key                             | CWE-326    | A02                  |
| java-2nd-order-sql-injection                    | CWE-89     | A02                  |
| go-cleartext-logging                            | CWE-312    | A02                  |
| java-stored-misconfig                           | CWE-933    | A02                  |
| java-unsafe-certificate                         | CWE-295    | A02                  |
| js-response-splitting                           | CWE-113    | A02                  |
| cs-weak-ssl-protocol                            | CWE-327    | A02                  |
| cs-inadequate-padding                           | CWE-780    | A03                  |
| cpp-insecure-port                               | CWE-319    | A03                  |
| java-open-redirect                              | CWE-601    | A03                  |
| cpp-2nd-order-sql-injection                     | CWE-89     | A03                  |
| python-unsafe-deserialization                   | CWE-502    | A03                  |
| go-hardcoded-credentials                        | CWE-798    | A03                  |
| cs-stored-path-traversal                        | CWE-22     | A03                  |
| cs-short-crypto-key                             | CWE-326    | A03                  |
| java-db-connection-string-injection             | CWE-99     | A03                  |
| go-insecure-tls                                 | CWE-295    | A03                  |
| java-insecure-port                              | CWE-319    | A03                  |
| cpp-process-control                             | CWE-114    | A03                  |
| cpp-short-crypto-key                            | CWE-326    | A03                  |
| js-unsafe-hash                                  | CWE-328    | A03                  |
| java-weak-crypto-algorithm                      | CWE-327    | A03                  |
| cs-http-header-injection                        | CWE-644    | A03                  |
| go-parameter-injection                          | CWE-74     | A03                  |
| cpp-command-injection                           | CWE-78     | A03                  |
| js-command-injection                            | CWE-78     | A03                  |
| cpp-sql-injection                               | CWE-89     | A03                  |
| java-http-header-injection                      | CWE-644    | A03                  |
| go-ssti                                         | CWE-1336   | A03                  |
| js-insecure-port                                | CWE-319    | A03                  |
| cs-ldap-injection                               | CWE-90     | A03                  |
| cs-2nd-order-sql-injection                      | CWE-89     | A03                  |
| cpp-cookie-poisoning                            | CWE-472    | A03                  |
| js-express-without-helmet                       | CWE-693    | A03                  |
| go-xxe                                          | CWE-611    | A03                  |
| cpp-weak-ssl-protocol                           | CWE-327    | A03                  |
| go-weak-password-recovery                       | CWE-640    | A03                  |
| cpp-dos-by-sleep                                | CWE-400    | A03                  |
| js-xxe                                          | CWE-611    | A03                  |
| cs-response-splitting                           | CWE-113    | A03                  |
| python-insecure-port                            | CWE-319    | A03                  |
| cpp-ssrf                                        | CWE-918    | A03                  |
| cs-insecure-port                                | CWE-319    | A03                  |
| python-prompt-injection-rce                     | CWE--1     | A03                  |
| python-path-traversal                           | CWE-22     | A03                  |
| cs-stored-cookie-poisoning                      | CWE-472    | A03                  |
| cpp-password-in-cookie                          | CWE-200    | A03                  |
| java-response-splitting                         | CWE-113    | A03                  |
| cpp-cgi-xss                                     | CWE-79     | A03                  |
| cpp-potential-redos                             | CWE-1333   | A03                  |
| js-ssrf                                         | CWE-918    | A03                  |
| cpp-read-buffer-size-mismatch                   | CWE-131    | A03                  |
| python-potential-redos                          | CWE-1333   | A03                  |
| python-short-crypto-key                         | CWE-326    | A03                  |
| java-stored-http-header-injection               | CWE-644    | A03                  |
| python-sql-injection                            | CWE-89     | A03                  |
| go-sql-injection                                | CWE-89     | A03                  |
| cs-reflection                                   | CWE-470    | A03                  |
| cpp-tainted-write-size                          | CWE-129    | A03                  |
| python-xss                                      | CWE-79     | A03                  |
| python-redos                                    | CWE-1333   | A03                  |
| python-ldap-injection                           | CWE-90     | A03                  |
| js-cookie-poisoning                             | CWE-472    | A03                  |
| cpp-tainted-read-size                           | CWE-129    | A03                  |
| go-stored-xpath                                 | CWE-643    | A03                  |
| cpp-insecure-random                             | CWE-338    | A03                  |
| python-hardcoded-credentials                    | CWE-798    | A03                  |
| cs-insecure-protocol                            | CWE-319    | A03                  |
| cpp-db-connection-string-injection              | CWE-99     | A03                  |
| java-xslt-injection                             | CWE-91     | A03                  |
| js-hardcoded-credentials                        | CWE-798    | A03                  |
| python-flask-debug                              | CWE-1295   | A03                  |
| cpp-double-free                                 | CWE-415    | A03                  |
| cs-regex-injection                              | CWE-625    | A03                  |
| java-stored-ldap                                | CWE-90     | A03                  |
| cs-process-control                              | CWE-114    | A03                  |
| python-unsafe-hash                              | CWE-328    | A03                  |
| cpp-obsolete-functions                          | CWE-477    | A03                  |
| go-ssrf                                         | CWE-918    | A03                  |
| python-open-redirect                            | CWE-601    | A03                  |
| cs-stored-xss                                   | CWE-79     | A03                  |
| cpp-regex-injection                             | CWE-625    | A03                  |
| js-ldap-injection                               | CWE-90     | A03                  |
| python-insecure-protocol                        | CWE-319    | A03                  |
| cpp-unsanitized-memory-read-offset              | CWE-126    | A03                  |
| java-insecure-protocol                          | CWE-319    | A03                  |
| cpp-unsanitized-alloc-size                      | CWE-789    | A03                  |
| js-helper                                       | CWE--1     | A03                  |
| java-stored-path-traversal                      | CWE-22     | A03                  |
| cs-stored-redirect                              | CWE-601    | A03                  |
| cpp-response-splitting                          | CWE-113    | A03                  |
| go-db-connection-string-injection               | CWE-99     | A03                  |
| go-potential-redos                              | CWE-1333   | A03                  |
| python-xxe                                      | CWE-611    | A04                  |
| js-insecure-protocol                            | CWE-319    | A04                  |
| cpp-stored-path-traversal                       | CWE-22     | A04                  |
| cs-potential-redos                              | CWE-1333   | A04                  |
| go-unsafe-deserialization                       | CWE-502    | A04                  |
| go-insecure-port                                | CWE-319    | A04                  |
| python-insecure-random                          | CWE-338    | A04                  |
| java-reflection                                 | CWE-470    | A04                  |
| cs-redos                                        | CWE-1333   | A04                  |
| python-xslt-injection                           | CWE-91     | A04                  |
| js-password-in-cookie                           | CWE-200    | A04                  |
| cs-db-connection-string-injection               | CWE-99     | A04                  |
| js-insecure-websocket                           | CWE-1385   | A04                  |
| cpp-uaf                                         | CWE-416    | A04                  |
| go-code-injection                               | CWE-94     | A04                  |
| java-jndi-injection                             | CWE-642    | A04                  |
| python-externally-controllable-file-permissions | CWE-732    | A04                  |
| cpp-tainted-memory-write-offset                 | CWE-125    | A05                  |
| go-stored-redirect                              | CWE-601    | A05                  |
| go-stored-cookie-poisoning                      | CWE-472    | A05                  |
| cpp-hardcoded-credentials                       | CWE-798    | A05                  |
| python-dos-by-sleep                             | CWE-400    | A05                  |
| go-cookie-poisoning                             | CWE-472    | A05                  |
| cs-command-injection                            | CWE-78     | A05                  |
| js-dom-based-open-redirect                      | CWE-601    | A05                  |
| java-password-in-cookie                         | CWE-200    | A07                  |
| python-cookie-poisoning                         | CWE-472    | A07                  |
| cpp-http-header-injection                       | CWE-644    | A07                  |
| js-insecure-cookie                              | CWE-614    | A07                  |
| js-code-injection                               | CWE-94     | A07                  |
| java-potential-redos                            | CWE-1333   | A07                  |
| java-regex-injection                            | CWE-625    | A07                  |
| cs-password-in-cookie                           | CWE-200    | A07                  |
| java-stored-xpath                               | CWE-643    | A07                  |
| java-cookie-poisoning                           | CWE-472    | A07                  |
| python-process-control                          | CWE-114    | A07                  |
| js-archive-slip                                 | CWE-22     | A07                  |
| python-xpath-injection                          | CWE-643    | A08                  |
| go-dos-by-sleep                                 | CWE-400    | A08                  |
| go-xpath-injection                              | CWE-643    | A08                  |
| go-open-redirect                                | CWE-601    | A08                  |
| js-process-control                              | CWE-114    | A08                  |
| go-xss                                          | CWE-79     | A08                  |
| java-path-traversal                             | CWE-22     | A10                  |
| python-missing-ssl-validation                   | CWE-295    | A10                  |
| python-command-injection                        | CWE-78     | A10                  |
| python-http-header-injection                    | CWE-644    | A10                  |
| cpp-weak-crypto-algorithm                       | CWE-327    | A10                  |
| python-stack-trace-exposure                     | CWE-209    | A10                  |
| cpp-unsanitized-memory-write-offset             | CWE-125    |                      |
| cpp-insecure-protocol                           | CWE-319    |                      |
| java-stack-trace-exposure                       | CWE-209    |                      |
| js-dom-based-xss                                | CWE-79     |                      |
| python-weak-crypto-algorithm                    | CWE-327    |                      |
| go-key-past-expiration                          | CWE-322    |                      |
| cs-stored-xpath                                 | CWE-643    |                      |
| go-path-traversal                               | CWE-22     |                      |
| go-stored-code-injection                        | CWE-94     |                      |
| js-cors-misconfig                               | CWE-942    |                      |
| java-command-injection                          | CWE-78     |                      |
| cpp-path-traversal                              | CWE-22     |                      |
| java-ldap-injection                             | CWE-90     |                      |
| js-http-only                                    | CWE-1004   |                      |
| cs-xpath-injection                              | CWE-643    |                      |
| go-process-control                              | CWE-114    |                      |
| cs-insecure-random                              | CWE-338    |                      |
| js-redos                                        | CWE-1333   |                      |
| java-ssti                                       | CWE-1336   |                      |
| java-stored-cookie-poisoning                    | CWE-472    |                      |
| go-weak-ssl-protocol                            | CWE-327    |                      |
| cs-weak-crypto-algorithm                        | CWE-327    |                      |
| python-weak-file-permissions                    | CWE-732    |                      |
| python-parameter-injection                      | CWE-74     |                      |
| cpp-stored-command-injection                    | CWE-78     |                      |
| js-lfi                                          | CWE-98     |                      |
| js-xpath-injection                              | CWE-643    |                      |
| java-javascript-enabled                         | CWE-749    |                      |
| java-stored-trust-boundary                      | CWE-501    |                      |
| cs-stored-ldap                                  | CWE-90     |                      |
| cpp-unsafe-deserialization                      | CWE-502    |                      |
| python-response-splitting                       | CWE-113    |                      |
| go-command-injection                            | CWE-78     |                      |
| go-stored-command-injection                     | CWE-78     |                      |
| java-unsafe-deserialization                     | CWE-502    |                      |
| cs-xxe                                          | CWE-611    |                      |
| js-sql-injection                                | CWE-89     |                      |
| cs-xslt-injection                               | CWE-91     |                      |
| js-http-header-injection                        | CWE-644    |                      |
| js-open-redirect                                | CWE-601    |                      |
| python-tainted-os-command                       | CWE-78     |                      |
| cpp-dangerous-functions                         | CWE-242    |                      |
| cpp-classic-buffer-overflow                     | CWE-120    |                      |
| js-potential-redos                              | CWE-1333   |                      |
| cpp-cgi-stored-xss                              | CWE-79     |                      |
| cs-path-traversal                               | CWE-22     |                      |
| java-stored-xss                                 | CWE-79     |                      |
| python-ssti                                     | CWE-1336   |                      |
| java-process-control                            | CWE-114    |                      |
| cs-sql-injection                                | CWE-89     |                      |
| java-insecure-random                            | CWE-338    |                      |
| java-code-injection                             | CWE-94     |                      |
| cpp-off-by-one-in-allocation                    | CWE-193    |                      |
| cpp-tainted-memory-read-offset                  | CWE-126    |                      |
| js-regex-injection                              | CWE-625    |                      |
| go-stored-path-traversal                        | CWE-22     |                      |
| js-remote-param-injection                       | CWE-141    |                      |
| python-ssrf                                     | CWE-918    |                      |
| java-stored-command-injection                   | CWE-78     |                      |
| js-path-traversal                               | CWE-22     |                      |
| cs-archive-slip                                 | CWE-22     |                      |
| js-unsafe-deserialization                       | CWE-502    |                      |
| cs-code-injection                               | CWE-94     |                      |
| js-improper-samesite                            | CWE-1275   |                      |
| go-helper                                       | CWE-1      |                      |
| cpp-uncontrolled-format-string                  | CWE-134    |                      |
| cs-ssrf                                         | CWE-918    |                      |
