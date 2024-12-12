# CI/CD Integration



### Set Up Xray CI Integration <a href="#set-up-xray-ci-integration" id="set-up-xray-ci-integration"></a>

&#x20;Setting up Xray CI configuration involves the following two steps:

#### 1. Configure Xray for CI Integration <a href="#id-1.-configure-xray-for-ci-integration" id="id-1.-configure-xray-for-ci-integration"></a>

1. Install Xray.
2. Set up indexing on the resources.
3. For Xray to scan builds upon request by a CI server, you need to configure a Watch with the right filters that specify which artifacts and vulnerabilities should trigger an alert, and set a Fail Build Job Action for that Watch.

#### 2. Configure your CI Server for Xray Integration <a href="#id-2.-configure-your-ci-server-for-xray-integration" id="id-2.-configure-your-ci-server-for-xray-integration"></a>

CommentXray CI/CD integration is supported for:

* //TODO GithHub&#x20;
* **Jenkins**: To **configure a build job** to request a scan, with the [Jenkins Artifactory Plug-in](https://jfrog.com/help/access?ft:clusterId=UUID-76a95645-d616-a394-b620-cf5756ce4900) (v2.9.0 and above), you need to create a `scanConfig` instance and and pass it to the `xrayScan` method in the Jenkins Pipeline.
* **Azure DevOps**: To scan build artifacts for vulnerabilities in [Azure DevOps](https://github.com/jfrog/jfrog-azure-devops-extension#readme), you need to add the Artifactory Xray Scan task after the Artifactory Publish BuildInfo task.
* **Bamboo**: To scan build artifacts for vulnerabilities, with the [Bamboo Artifactory Plug-in](https://jfrog.com/help/access?ft:clusterId=UUID-76a95645-d616-a394-b620-cf5756ce4900), you need to add the Artifactory Xray Scan task to your plan. The task should follow a previous task which publishes the build-info to Artifactory.
* **TeamCity**: To scan build artifacts and dependencies for vulnerabilities with the [TeamCity Artifactory Plug-in](https://jfrog.com/help/access?ft:clusterId=UUID-8975dd73-a0be-e1c6-559d-bccf059ed832) ,you need to enable the **Xray scan on build** and **Fail build options**, configured per build.
* **JFrog CLI**: To scan build artifacts for vulnerabilities using JFrog CLI, you need to use the[ jfrog rt scan-build ](https://jfrog.com/help/access?ft:originId=UUID-004d6e3e-0fac-6728-b946-9474736e4504\&ft:sourceId=pal).
