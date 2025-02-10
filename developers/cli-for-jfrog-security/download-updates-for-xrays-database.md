# Download Updates for Xray's Database

The offline-update command downloads updates to Xray's vulnerabilities database. The Xray UI allows you to build the command structure.

Command: `xr offline-update`, `xr ou`

<table><thead><tr><th width="314.5"></th><th></th><th></th></tr></thead><tbody><tr><td><strong>Command Options</strong></td><td><strong>Default</strong></td><td><strong>Description</strong></td></tr><tr><td><code>--license-id</code></td><td></td><td>[Mandatory]<br>Xray license ID.</td></tr><tr><td><code>--from</code></td><td></td><td>[Optional]<br>From update date in <code>YYYY-MM-DD</code> format.</td></tr><tr><td><code>--to</code></td><td></td><td>[Optional]<br>To update date in <code>YYYY-MM-DD</code> format.</td></tr><tr><td><code>--version</code></td><td></td><td>[Optional]<br>Xray API version.</td></tr><tr><td><code>--target</code></td><td><code>./</code></td><td>Path for downloaded update files.</td></tr><tr><td><code>--stream</code></td><td><code>false</code></td><td>Set to true to use Xray DBSync V3 stream, Acceptable values : <code>public_data</code>, <code>exposures</code>, and <code>contextual_analysis</code>.</td></tr><tr><td><code>--periodic</code></td><td><code>false</code></td><td>Set to <code>true</code> to get the Xray DBSync V3. Periodic Package (Use with <code>--stream</code> flag).</td></tr></tbody></table>
