# System Monitoring

Xray displays your general system status.

The overall status is an accumulation of the status for a variety of parameters. The table below describes the parameters monitored and the condition that generates a notification. Note that some notifications may be categorized as "warnings" or "errors" depending on the severity of the condition:

| **Parameter**                            | **Condition for notification**                                             |
|------------------------------------------|---------------------------------------------------------------------------|
| Connection to the PostgreSQL database    | No connection                                                             |
| Connection to RabbitMQ messaging service  | No connection                                                             |
| Connection to Global Database Server      | No connection                                                             |
| Connection to Artifactory instances       | No connection                                                             |
| Service restarts                          | **Warning**: 3 in the last 5 hours<br>**Error**: 50 in the last 5 hours |
| Average CPU usage                         | **Warning:** 90%<br>**Error:** 95%                                       |
| Average RAM usage                         | **Warning:** 90%<br>**Error:** 95%                                       |
| System open files usage                   | **Warning:** 80% of maximum<br>**Error:** 95% of maximum                 |
| Working directory disk usage              | **Warning:** 80% of total<br>**Error:** 95% of total                     |
| Xray data folder disk usage               | **Warning:** 80% of maximum specified in the Xray configuration files<br>**Error:** 95% of maximum specified in the Xray configuration files |
| Failed Messages Count                     | **Warning:** More than 0 failure messages<br>**Error:** More than 100 failure messages |