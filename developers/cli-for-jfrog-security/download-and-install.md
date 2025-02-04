# Download and Install

#### **JFrog CLI v2 (Latest Version)**

**Debian-based Systems**

```
sudo mkdir -p /usr/share/keyrings
wget -qO - https://releases.jfrog.io/artifactory/api/v2/repositories/jfrog-debs/keyPairs/primary/public | sudo gpg --dearmor -o /usr/share/keyrings/jfrog.gpg
echo "deb [signed-by=/usr/share/keyrings/jfrog.gpg] https://releases.jfrog.io/artifactory/jfrog-debs focal contrib" | sudo tee /etc/apt/sources.list.d/jfrog.list
sudo apt update
sudo apt install -y jfrog-cli-v2-jf
jf intro
```

**RPM-based Systems**

```
echo "[jfrog-cli]" > jfrog-cli.repo
echo "name=JFrog CLI" >> jfrog-cli.repo
echo "baseurl=https://releases.jfrog.io/artifactory/jfrog-rpms" >> jfrog-cli.repo
echo "enabled=1" >> jfrog-cli.repo
echo "gpgcheck=1" >> jfrog-cli.repo
rpm --import https://releases.jfrog.io/artifactory/api/v2/repositories/jfrog-rpms/keyPairs/primary/public
rpm --import https://releases.jfrog.io/artifactory/api/v2/repositories/jfrog-rpms/keyPairs/secondary/public
sudo mv jfrog-cli.repo /etc/yum.repos.d/
yum install -y jfrog-cli-v2-jf
jf intro
```

**Homebrew (macOS/Linux)**

```
brew install jfrog-cli
```

**cURL Installation**

```
curl -fL https://install-cli.jfrog.io | sh
```

**NPM Installation**

```
npm install -g jfrog-cli-v2-jf
```

**Docker Installation**

```
# Slim Image
docker run releases-docker.jfrog.io/jfrog/jfrog-cli-v2-jf jf -v

# Full Image
docker run releases-docker.jfrog.io/jfrog/jfrog-cli-full-v2-jf jf -v
```

**PowerShell (Windows)**

```
Start-Process -Wait -Verb RunAs powershell "-NoProfile iwr https://releases.jfrog.io/artifactory/jfrog-cli/v2-jf/[RELEASE]/jfrog-cli-windows-amd64/jf.exe -OutFile $env:SYSTEMROOT\system32\jf.exe"
```

**Chocolatey Installation (Windows)**

```
choco install jfrog-cli-v2-jf
```

#### **JFrog CLI v1 (Legacy Version)**

Legacy versions of JFrog CLI are available through the following installers:

* **Debian-based systems**
* **RPM-based systems**
* **cURL** (`curl -fL https://getcli.jfrog.io | sh`)
* **NPM** (`npm install -g jfrog-cli-go`)
* **Docker**
* **Go** (`GO111MODULE=on go get github.com/jfrog/jfrog-cli`)

## Key Enhancements in JFrog CLI v2

* **Default value for `--flat` option set to false** for `jfrog rt upload`
* **Deprecation of legacy command syntaxes** for Maven, Gradle, npm, Go, and NuGet
* **Removal of Bintray commands**
* **Migration to new configuration commands (`jfrog config add` and `jfrog config use`)**
* **Updated artifact and dependency management**
* **New environment variables for improved configurability**
