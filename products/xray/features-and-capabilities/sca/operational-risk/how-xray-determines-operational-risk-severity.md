# How Xray Determines Operational Risk Severity

Xray calculates the Operational Risk as High, Medium, Low, and None (no known risk) using the following criteria. For information on how Xray calculates operational risk effective severity, see the table **Calculating Operational Risk Effective Severity** further below.

| Risk                          | Type                          | Severity                                                                                                                                           | Notes                                                                                                                                                            |
| ----------------------------- | ----------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| End-of-Life                   | Boolean                       | <p>High = True</p><p>None = False</p>                                                                                                              |                                                                                                                                                                  |
| Version Age                   | Number                        | <p>Number of months since release / 10</p><p>High >= 4</p><p>Medium > 2 and &#x3C; 4</p><p>Low > 1 and &#x3C;= 2</p><p>None (no risk) &#x3C;=1</p> |                                                                                                                                                                  |
| Number of New Versions        | Number                        | <p>Number of versions since / 2</p><p>High >= 6</p><p>Medium >= 4 and &#x3C; 6</p><p>Low >= 2 and &#x3C; 4</p><p>None (no risk) &#x3C; 2</p>       |                                                                                                                                                                  |
| Health of Open Source Project |                               |                                                                                                                                                    |                                                                                                                                                                  |
|                               | Release cadence per year      | <p>Healthy >= 2 releases</p><p>Unhealthy &#x3C;= 1</p>                                                                                             | <p>This includes all releases. Including any dot releases and patch releases if they are GA releases.</p><p>When there is no data, it is presumed as healthy</p> |
|                               | Number of commits per year    | <p>Healthy >= 100 commits</p><p>Unhealthy &#x3C; 100 commits</p>                                                                                   |                                                                                                                                                                  |
|                               | Number of committers per year | <p>Healthy > = 5 committers</p><p>Unhealthy &#x3C; 5 c ommitters</p>                                                                               |                                                                                                                                                                  |

**Calculating Operational Risk Effective Severity**

| # | EOL  | Health    | # of new versions       | Version Age             | Combine Severity | Risk Reason                                                       |
| - | ---- | --------- | ----------------------- | ----------------------- | ---------------- | ----------------------------------------------------------------- |
| 1 | High | Any       | Any                     | Any                     | **High**         | **EOL**                                                           |
| 2 | None | High Risk | Any                     | Any                     | **High**         | **Health**                                                        |
| 3 | None | No Risk   | High                    | None, Low, Medium, High | **High**         | **Number of new versions and** **Version Age (only when High)**   |
| 4 | None | No Risk   | Medium                  | None, Low, Medium       | **Medium**       | **Number of new versions and** **Version Age (only when Medium)** |
| 5 | None | No Risk   | Low                     | None, Low               | **Low**          | **Number of new versions and** **Version Age (only when Low)**    |
| 6 | None | No Risk   | None                    | None                    | **None**         | **No given reason**                                               |
| 7 | None | No Risk   | None, Low, Medium, High | High                    | **High**         | **Version Age and number of new versions (only when High)**       |
| 8 | None | No Risk   | None, Low, Medium       | Medium                  | **Medium**       | **Version Age and number of new versions (only when Medium)**     |
| 9 | None | No Risk   | None, Low               | Low                     | **Low**          | **Version Age and number of new versions (only when Low)**        |

\
