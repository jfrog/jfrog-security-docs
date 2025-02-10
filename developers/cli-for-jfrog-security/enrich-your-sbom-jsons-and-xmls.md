# Enrich your SBOM JSONs & XMLs

The sbom enrichment command takes an exported SBOM file in XML/JSON format and enriches your file with package vulnerabilities found by XRAY.CommentThis _**jf sbom enrich \<file\_path>**_ command enriches a file that is found on file\_path.Comment

***

Comment**Note**Comment

> This command requires:Comment

* Version 3.101.3 or above of XrayComment
* Version 2.60.0 or above of JFrog CLIComment

Comment

***

Comment

**Commands Params**

Comment

| **Command name**      | sbom-enrich                                                                                                             |
| --------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| **Abbreviation**      | se                                                                                                                      |
| **Command options**   | ​                                                                                                                       |
| `--server-id`         | \[Optional] Server ID configured using the _jf c add_ command. If not specified, the default configured server is used. |
| **Command arguments** | ​                                                                                                                       |
| `file_path`           | the sbom file path.                                                                                                     |

Comment

**Example 1**

CommentEnriches an XML fileCommentjf se "path/to/file.xml"Comment

**Example 2**

CommentEnriches a JSON fileCommentjf se "path/to/files/file.json"Comment[\
](https://app.gitbook.com/o/qA7lOLzSLvqlPYMcxj0G/s/HtpcI8sApaH537Ph5QxY/jfrog-applications/jfrog-cli/cli-for-jfrog-security/how-tos/scan-your-binaries)
