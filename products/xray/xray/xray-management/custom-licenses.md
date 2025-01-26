# Custom Software Licenses

JFrog Xray's License Management provides a comprehensive list of open-source licenses existing on the market and indicates which scanned artifacts use each license. Using Xray's License Management, you can also create custom licenses which you can assign to components at any time.

### To view compliance licenses:

See the list of available licenses in the **Administration** module under **Xray | Advanced | Manage Compliance Licenses**.

![Custom License](../../../../.gitbook/assets/custom-license-image.png)

## Create and Edit Custom Licenses

Using Manage Licenses, you can create custom licenses which can then be assigned to components. To create a custom license, click **Add a License.**

| **Field**         | **Description**                                                                                                                  |
| ----------------- | -------------------------------------------------------------------------------------------------------------------------------- |
| License Name      | The abbreviated license name.                                                                                                    |
| License Full Name | The full license name.                                                                                                           |
| Description       | A description of the license.                                                                                                    |
| References        | A list of fully qualified references to components that use this license.                                                        |
| Aliases           | A list of aliases associated with the license. An alias needs to be unique and cannot be used more than once or across licenses. |

> Aliases are Supported from Xray 2.10.0 The aliases will be scanned from version 2.10.0. If you want to add aliases to previous license versions, you need to reindex the relevant artifacts or repository.
