# System Monitoring

Xray displays your general system status.

The overall status is an accumulation of the status for a variety of parameters. The table below describes the parameters monitored and the condition that generates a notification. Note that some notifications may be categorized as "warnings" or "errors" depending on the severity of the condition:

| **Parameter**                            | **Condition for notification**                                                                                                                                                |
| ---------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Connection to the PostgreSQL database    | No connection                                                                                                                                                                 |
| Connection to RabbitMQ messaging service | No connection                                                                                                                                                                 |
| Connection to Global Database Server     | No connection                                                                                                                                                                 |
| Connection to Artifactory instances      | No connection                                                                                                                                                                 |
| Service restarts                         | <p><strong>Warning</strong>: 3 in the last 5 hours<br><strong>Error</strong>: 50 in the last 5 hours</p>                                                                      |
| Average CPU usage                        | <p><strong>Warning:</strong> 90%<br><strong>Error:</strong> 95%</p>                                                                                                           |
| Average RAM usage                        | <p><strong>Warning:</strong> 90%<br><strong>Error:</strong> 95%</p>                                                                                                           |
| System open files usage                  | <p><strong>Warning:</strong> 80% of maximum<br><strong>Error:</strong> 95% of maximum</p>                                                                                     |
| Working directory disk usage             | <p><strong>Warning:</strong> 80% of total<br><strong>Error:</strong> 95% of total</p>                                                                                         |
| Xray data folder disk usage              | <p><strong>Warning:</strong> 80% of maximum specified in the Xray configuration files<br><strong>Error:</strong> 95% of maximum specified in the Xray configuration files</p> |
| Failed Messages Count                    | <p><strong>Warning:</strong> More than 0 failure messages<br><strong>Error:</strong> More than 100 failure messages</p>                                                       |
