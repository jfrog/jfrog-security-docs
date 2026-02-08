# Supported Technologies

#### **Supported Package Type in Catalog**

| Package Type  | Name / Ecosystem             | Catalog Version / Requirements   | Source URLs                                                                                                                                   |
| ------------- | ---------------------------- | -------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------- |
| Maven         | MVN Repository, Google Maven | 1.0.0                            | [https://repo1.maven.org/maven2/](https://repo1.maven.org/maven2/) [https://dl.google.com/android/maven](https://dl.google.com/android/maven) |
| npm           | NPM registry                 | 1.0.0                            | [https://registry.npmjs.org](https://registry.npmjs.org/)                                                                                     |
| PyPI          | PyPI org                     | 1.0.0                            | [https://files.pythonhosted.org](https://files.pythonhosted.org/)                                                                             |
| Docker\*      | Docker Hub                   | 1.0.0                            | [https://hub.docker.com/](https://hub.docker.com/)                                                                                            |
| NuGet         | NuGet Gallery                | 1.0.0                            | [https://www.nuget.org/](https://www.nuget.org/)                                                                                              |
| Conan         | Conan central repository     | 1.0.0                            | [http://center.conan.io/](http://center.conan.io/)                                                                                            |
| Crates (Rust) | Rust Package Registry        | 1.17.2                           | [https://crates.io/](https://crates.io/)                                                                                                      |
| Hugging Face  | Hugging Face                 | 1.0.0                            | [https://huggingface.co/](https://huggingface.co/)                                                                                            |
| Conda         | Anaconda Packages            | 1.22.4                           | [https://repo.anaconda.com/pkgs/](https://repo.anaconda.com/pkgs/)                                                                            |
| Golang        | Go Packages                  | 1.19.1                           | [https://proxy.golang.org/](https://proxy.golang.org/)                                                                                        |
| RubyGems      | RubyGems                     | 1.0.0                            | [https://rubygems.org/](https://rubygems.org/)                                                                                                |
| PHP Composer  | Composer (Git-based)         | Xray ≥ 3.137 Artifactory ≥ 7.131 | [https://github.com](https://github.com/) [https://bitbucket.org](https://bitbucket.org/)                                                     |
| R             | CRAN                         | Xray ≥ 3.137 Catalog UI ≥ 1.26   | [https://cran.r-project.org](https://cran.r-project.org/)                                                                                     |
| Pub           | Dart Pub                     | Xray ≥ 3.137 Catalog UI ≥ 1.26   | [https://pub.dev](https://pub.dev/)                                                                                                           |

#### Operating System Package Ecosystems

| Package Type | Name / Ecosystem      | Catalog Version / Requirements | Source URLs                                                                                                                                               |
| ------------ | --------------------- | ------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Alpine       | Alpine Linux packages | Xray ≥ 3.136 Catalog UI ≥ 1.28 | [http://dl-cdn.alpinelinux.org](http://dl-cdn.alpinelinux.org/)                                                                                           |
| Debian       | Debian packages       | Xray ≥ 3.137 Catalog UI ≥ 1.28 | [https://deb.debian.org/debian](https://deb.debian.org/debian) [https://security.debian.org/debian-security](https://security.debian.org/debian-security) |
| Ubuntu (deb) | Ubuntu packages       | Xray ≥ 3.137 Catalog UI ≥ 1.28 | [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu)               |

{% hint style="info" %}
Support for Docker is currently through REST API only.
{% endhint %}
