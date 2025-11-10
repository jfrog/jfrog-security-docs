# Prerequisites

### Language support

| Language       | Supported Frameworks                                                                  | Supported Libraries                                                                                                                                                                                                                                                                                                                              | Not Supported                             |
| -------------- | ------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ----------------------------------------- |
| **PHP**        | Laravel, Symfony, CodeIgniter, Yii2, WordPress                                        | Guzzle, PDO                                                                                                                                                                                                                                                                                                                                      | —                                         |
| **Python**     | Flask, Django, FastAPI                                                                | SQLAlchemy, psycopg2, MySQLdb, mysql.connector, pymongo, requests, bleach, tkinter, pandas, numpy                                                                                                                                                                                                                                                | Python 1.x, 2.x                           |
| **JavaScript** | Express.js, Koa, Fastify, NestJS                                                      | mysql / mysql2, pg, mongodb, sequelize, knex, sqlite3, redis, axios, node-fetch, request, needle, ws, DOMPurify, escape-html, xss, sanitize-html, validator, lodash, Handlebars, EJS, Pug, Mustache, multiparty, formidable, unified, path-sanitizer, sanitize-filename, sqlstring                                                               | JSX                                       |
| **TypeScript** | (Same as JavaScript frameworks) Express.js, Koa, Fastify, NestJS                      | (Same as JavaScript libraries) See JavaScript list above                                                                                                                                                                                                                                                                                         | TSX                                       |
| **Java**       | Spring Framework, JAX-RS, Micronaut, Struts, Vaadin, Wicket, Grails, Seam, Atmosphere | Hibernate, JPA, MyBatis, OWASP ESAPI, Apache Commons, Thymeleaf, FreeMarker, Velocity, JSP templating                                                                                                                                                                                                                                            | — (legacy JSP standalone only)            |
| **C# / .NET**  | ASP.NET Core, ASP.NET MVC, ASP.NET Web Forms, Nancy, ServiceStack, Blazor             | Entity Framework, Dapper, NHibernate, PetaPoco, Microsoft AntiXss, Razor, Telerik UI, Infragistics, ComponentArt, log4net, NLog, Serilog, Microsoft.Extensions.Logging                                                                                                                                                                           | ASPX (legacy templates only)              |
| **C / C++**    | Pistache, Wt, Qt, MFC                                                                 | SQLite3, MySQL C API, libpq, ODBC, mysqlpp, libpqxx, Boost, OpenSSL, Crypto++, Libgcrypt, pugixml, RapidJSON, nlohmann/json, TinyXML2, yaml-cpp, protobuf, FlatBuffers, Cap'n Proto, cereal                                                                                                                                                      | —                                         |
| **Golang**     | Gin, Echo, Chi, Gorilla Mux, Beego, fasthttp, grpc                                    | GORM, sqlx, pgx, go-sql-driver, go-redis, gocql, mongo-go-driver, viper                                                                                                                                                                                                                                                                          | html/template (no taint-tracking support) |
| **Rust**       | Actix-web, Rocket, Axum, Warp, Tide, Poem, Salvo, Hyper, Iron                         | Diesel, SQLx, tokio-postgres, rusqlite, mysql, mongodb, redis, tiberius, reqwest, hyper, surf, ureq, isahc, attohttpc, tokio, async-std, futures, serde\_json, serde\_yaml, bincode, postcard, rmp-serde, askama, tera, handlebars, maud, sailfish, liquid, minijinja, yarte, ammonia, base64, hex, clap, structopt, rdkafka, lapin, nats, tonic | —                                         |

### Analysis capabilities

Understanding the dependencies in the code (call flow, type propagation, constants etc.) in full-project context:

* Cross-functional
* Cross-file
* Cross-module

### Querying capabilities (custom queries)

{% hint style="info" %}
This feature is in Beta and subject to changes.
{% endhint %}

Ability to construct code queries based on types, constants, external API names, data reachability, control flow dependencies, etc. of unlimited complexity.
