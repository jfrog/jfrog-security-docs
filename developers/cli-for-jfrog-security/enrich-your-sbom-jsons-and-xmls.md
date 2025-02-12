# Enrich your SBOM JSONs & XMLs

The `sbom-enrich` command takes an exported SBOM file in XML or JSON format and enriches it with package vulnerabilities identified by Xray.

## Before You Begin

It is essential you have:

* Xray 3.101.3 or above
* JFrog CLI 2.60.0 or above

**Command**: `jf sbom-enrich`, `jf se`

## Command Parameters

| `--server-id` | \[Optional] Server ID configured using the `jf c add` command. If not specified, the default configured server is used. | Optional |
| ------------- | ----------------------------------------------------------------------------------------------------------------------- | -------- |
| `file_path`   | The path to the SBOM file you want to enrich.                                                                           | Required |

### Examples

Enrich an XML file

```
jf se "path/to/file.xml"
```

Enrich a JSON file

```
jf se "path/to/files/file.json"
```
