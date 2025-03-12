# Prerequisites

### Language support

|            | Supported Frameworks                | Supported Libraries | Not Supported   |
| ---------- | ----------------------------------- | ------------------- | --------------- |
| Python     | Flask, Django                       | Sqlite3, Pymysql    | Python 1.x, 2.x |
| Javascript | Angular, Express, Node              |                     | JSX             |
| TypeScript |                                     |                     | TSX             |
| Java       | Sprint (partial), Hibernate, JSF(?) |                     | JSP             |
| C#         | ASP.Net Core, ASP.Net MVC, Nancy    |                     | ASPX            |
| C/C++      | Sqlite3, Mysql, OpenSSL, Boost      |                     |                 |
| Golang     | Echo, Chi, Gin                      | Gorm, html/template |                 |

### Analysis capabilities

Understanding the dependencies in the code (call flow, type propagation, constants etc.) in full-project context:

* Cross-functional
* Cross-file
* Cross-module&#x20;

### Querying capabilities (custom queries)



{% hint style="info" %}
This feature is in Beta and subject to changes.
{% endhint %}

Ability to construct code queries based on types, constants, external API names, data reachability, control flow dependencies, etc. of unlimited complexity.
