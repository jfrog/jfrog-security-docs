# Supported Technologies

### SAST, CVEs Contextual Analysis, and Secrets Detection

| Programming Language | Source Code SAST (1st party) | Source Code CVEs Contextual Analysis | Binary CVEs Contextual Analysis               | Secrets Detection |
| -------------------- | ---------------------------- | ------------------------------------ | --------------------------------------------- | ----------------- |
| Go                   | ✅                            | ✅                                    | Inside Docker                                 | ✅                 |
| Java                 | ✅                            | ✅                                    | Limited (Maven & Gradle — Uber/Fat JARs only) | ✅                 |
| Kotlin               |                              | ✅                                    | Inside Docker                                 | ✅                 |
| JavaScript           | ✅                            | ✅                                    | Inside Docker                                 | ✅                 |
| TypeScript           | ✅                            | ✅                                    | Inside Docker                                 | ✅                 |
| C# .NET              | ✅                            | ✅                                    | Inside Docker                                 | ✅                 |
| Python               | ✅                            |                                      | Inside Docker                                 | ✅                 |
| C/C++                | ✅                            |                                      | Inside Docker                                 | ✅                 |
| Rust                 | :white\_check\_mark:         |                                      | Inside Docker                                 | ✅                 |
| Docker               |                              |                                      | Conditional (depends on contained language)   |                   |
| Terraform (IaC)      | ✅                            |                                      |                                               | ✅                 |

### Misconfigurations

* Infrastructure as code (IaC)
  1. Terraform **modules** - Supported in JFrog IDE Plugins and JFrog CLI
  2. Terraform **plan** files - Supported in JFrog CLI
  3. Terraform **state** files - Supported in JFrog Artifactory (Terraform BE Repository)
* Applications and Services misconfigurations:
  1. Supported in JFrog Artifactory for **Container images**

