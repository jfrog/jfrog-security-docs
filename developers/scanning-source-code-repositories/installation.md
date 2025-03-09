# Package Manager Prerequisites

## Before You Begin

Frogbot relies on specific lock files, the presence of package manager executables, and proper configuration to accurately scan and secure your repositories.

## SCA Requirements

| **Requirement**                 | **Description**                                                                                   |
| ------------------------------- | ------------------------------------------------------------------------------------------------- |
| **Lock Files**                  | Ensure that relevant lock files are present in your repository for dependency management.         |
| **Package Manager Executables** | Ensure the appropriate package manager is installed and operational in your environment.          |
| **Network Access**              | Frogbot may need internet access to download dependencies based on your package manager settings. |
| **Environment Configuration**   | Ensure that necessary environment variables, proxies, or custom configurations are properly set.  |

### **Lock Files**

The following common lock files are required per package manager:

| **Package Manager** | **Lock File**                       | **Description**                                                                                                            |
| ------------------- | ----------------------------------- | -------------------------------------------------------------------------------------------------------------------------- |
| npm                 | `package-lock.json`                 | Automatically generated when running npm commands, ensuring consistent dependency installation.                            |
| Yarn                | `yarn.lock`                         | Maintained by Yarn, this file locks dependencies to specific versions, ensuring consistency across different environments. |
| Maven               | `pom.xml`                           | This Project Object Model file is essential for understanding and resolving dependencies.                                  |
| Python (pip)        | `requirements.txt`                  | Lists required Python packages, typically including specific versions, to ascertain vulnerabilities.                       |
| Golang (Go)         | `go.sum`                            | Automatically created with`go.mod`, detailing all dependencies and their exact versions.                                   |
| .NET (NuGet)        | `.sln`,`packages.config`,`*.csproj` | Solution files organize projects in Visual Studio, while dependency files track project dependencies within .NET projects. |

## Technology-Specific Prerequisites

Each package manager and build tool may have unique prerequisites.

### **npm (Node.js)**

| **Requirement**       | **Details**                                                      |
| --------------------- | ---------------------------------------------------------------- |
| **Requirements**      | Ensure Node.js and npm are installed and available in your PATH. |
| **Lock File**         | `package-lock.json`is required for accurate dependency scanning. |
| **Environment Setup** | Run`npm install`to verify dependencies resolve correctly.        |

### **Yarn**

| **Requirement**       | **Details**                                                      |
| --------------------- | ---------------------------------------------------------------- |
| **Requirements**      | Install Yarn and verify it’s available in your PATH.             |
| **Lock File**         | The`yarn.lock`file must be present.                              |
| **Environment Setup** | Run`yarn install`to confirm that the setup works without errors. |

### **Maven (Java)**

| **Requirement**       | **Details**                                            |
| --------------------- | ------------------------------------------------------ |
| **Requirements**      | Ensure Maven (or the`mvnw`wrapper) is accessible.      |
| **Lock File**         | The`pom.xml`file should be correctly configured.       |
| **Environment Setup** | Execute`mvn install`to validate dependency resolution. |

### **Python (pip)**

| **Requirement**       | **Details**                                                                          |
| --------------------- | ------------------------------------------------------------------------------------ |
| **Requirements**      | Python and pip must be installed and available in the environment.                   |
| **Lock File**         | The`requirements.txt`file should be present for dependency definitions.              |
| **Environment Setup** | Run`pip install -r requirements.txt`to ensure dependencies are configured correctly. |

### **Go**

| **Requirement**       | **Details**                                                                              |
| --------------------- | ---------------------------------------------------------------------------------------- |
| **Requirements**      | Ensure Go is installed and available in your PATH.                                       |
| **Lock File**         | The`go.sum`file must be present for accurate dependency scanning.                        |
| **Environment Setup** | Run`go mod tidy`to ensure all dependencies are correctly listed and resolved in`go.sum`. |

### **.NET (NuGet)**

| **Requirement**            | **Details**                                                                           |
| -------------------------- | ------------------------------------------------------------------------------------- |
| **Requirements**           | Install the .NET SDK and ensure NuGet is available in your PATH.                      |
| **Visual Studio Projects** | Ensure`.sln`files are present in your repository.                                     |
| **Other Dependency Files** | Files such as`packages.config`or`*.csproj`should be present and correctly configured. |
| **Lock File**              | Various files assist in tracking dependencies; specific files ensure completeness.    |
| **Environment Setup**      | Run`dotnet restore`to confirm that all NuGet dependencies are resolved correctly.     |

\
