# License Conclusion

License Conclusion (Starting from Xray version 3.124.x and above) allows users to determine a final, authoritative license for a specific SBOM entry, automatically or manually, without removing the originally declared licenses.

Instead of discarding conflicting or multiple declared licenses, Xray now supports automatic, priority based license conclusion to perform this task easily

Organizations often face challenges when managing multiple or conflicting licenses in a Software Bill of Materials (SBOM). For instance, a software package declared under both the MIT and Apache 2.0 licenses can create confusion regarding compliance obligations. As companies integrate diverse open source and proprietary components, clarity around licensing becomes essential to avoid legal issues. Compliance teams need effective tools to navigate these complexities and accurately communicate licensing obligations.

### Benefits

* Improves legal clarity by distinguishing between declared and concluded licenses
* Supports compliance teams with more accurate reporting and audit readiness
* Allow to better communicate the actual combined license obligations of a certain artifact

### How It Works

* License conclusion is performed based on the  assigned license “priority” value (lower is better)
* Each license is assigned a default priority based on its license category (see license priority table) - the default priority value can be overridden using the “[Set license](https://jfrog.com/help/r/xray-rest-apis/set-license-priority?tocId=qdVgd9S6QxWCQi~iwrxpkw)” API endpoint
* Custom license priority can be used to differentiate between licenses in the same category (e.g. MIT and ISC - 2 permissive licenses with the same default priority)&#x20;

Default License Priority Table

| License Category | Priority |
| ---------------- | -------- |
| CLA              | 5        |
| Copyleft Limited | 3        |
| Proprietary Free | 5        |
| Permissive       | 2        |
| Patent License   | 5        |
| Source-available | 4        |
| Free Restricted  | 4        |
| Unstated License | 5        |
| Copyleft         | 5        |
| Commercial       | 5        |
| Public Domain    | 1        |

### REST API Support

* [Get Licenses](https://jfrog.com/help/r/xray-rest-apis/get-licenses)
* [Set License Priority](https://jfrog.com/help/r/xray-rest-apis/set-license-priority?tocId=qdVgd9S6QxWCQi~iwrxpkw)

