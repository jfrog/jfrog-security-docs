# How-Tos

## **Scanning Gradle Projects with the JFrog Eclipse IDE Plugin**

The JFrog plugin automatically generates a dependency tree for your project by executing a Gradle script. It reads the Gradle configuration defined in Eclipse, which is managed by the [Buildship plugin](https://marketplace.eclipse.org/content/buildship-gradle-integration).

### **Accessing Gradle Configuration**

To view or modify the Gradle configuration:

1. Go to **Preferences** > **Gradle** > **Gradle Distribution** in Eclipse.

### **Gradle Configuration Handling**

* If a Gradle configuration is not set, the plugin will use **Gradle Wrapper** by default.
* If the project does not include Gradle Wrapper, Gradle will be automatically downloaded.
