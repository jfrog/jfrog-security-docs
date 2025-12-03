# GraphQL APIs

This section includes examples of GraphQL APIs for JFrog Catalog.

#### Note

* This API is in beta phase and subject to changes.
*   The request that needs to be done for this API is a POST HTTP request to path

    &#x20;`/catalog/api/v1/custom/graphql` with standard GraphQL over POST format for the body of the request.

#### Labels

#### Get a label with its assigned packages and package versions

```
{
  customCatalogLabel {
    getLabel(name: "my_label") {
      name
      description


      publicPackagesConnection(first:5) {
        edges {
          node {
            name
            type
          }
        }
      }
    
      publicPackageVersionsConnection(first:5) {
        edges {
          node {
            publicPackage {
              name
              type
            }
            version
          }
        }
      }
    }
  }
}
```

#### Get multiple labels with their assigned packages and package versions

```
{
  customCatalogLabel {
    searchLabels(first:10 where:{nameContainsFold:"my"} orderBy:{field:NAME, direction:ASC}) {
      edges {
        node{
          name
          description


          publicPackagesConnection(first:4) {
            edges {
              node {
                name
                type
              }
            }
          }


          publicPackageVersionsConnection(first:4) {
            edges {
              node {
                publicPackage {
                  name
                  type
                }
                version
              }
            }
          }
        }
      }
    }
  }
}
```

#### Get a package with its labels

```
{
  publicPackage {
    getPackage(name: "my_package" type: "npm") {
      name
      type


      customCatalogLabelsConnection(first:4) {
        edges {
          node {
            name
          }
        }
      }
    }
  }
}
```

#### Get a package version with its labels and its package with its labels

```
{
  publicPackageVersion {
    getVersion(name: "my_package" type: "npm" version: "1.0.0") {
      publicPackage {
        name
        type
        
        customCatalogLabelsConnection(first:4) {
          edges {
            node {
              name
            }
          }
        }
      }
      version


      customCatalogLabelsConnection(first:4) {
        edges {
          node {
            name
          }
        }
      }
    }
  }
}
```

#### Create a label

```
mutation {
   customCatalogLabel {
       createCustomCatalogLabel(label: {name: "my_label", description: "some description"}) {
           name
           description
       }
   }
}
```

#### Create multiple labels

```
mutation {
   customCatalogLabel{
       createCustomCatalogLabels(labels: [{name: "my_label1", description: "description1"}, {name: "my_label2", description: "description2"}]) {
           name
           description
       }
   }
}
```

#### Assign a label to a package

```
mutation {
    customCatalogLabel {
      assignCustomCatalogLabelsToPublicPackage(
        publicPackageLabels: {
          publicPackage: {name:"my_package", type:"npm"}
          labelNames:["my_label"]
        }
      )
   }
}
```

#### Assign a label to a package version

```
mutation {
  customCatalogLabel {
    assignCustomCatalogLabelsToPublicPackageVersion(
      publicPackageVersionLabels: {
        publicPackageVersion: {publicPackage: {name: "my_package", type: "npm"}, version: "1.0.0"}
        labelNames: ["my_label1"]
      }
    )
  }
}
```

#### Assign a label to multiple package versions

```
mutation {
  customCatalogLabel {
    assignCustomCatalogLabelToPublicPackageVersions(
      publicPackageVersionsLabel: {
        publicPackageVersions: [
          {publicPackage: {name: "my_package", type: "npm"}, version: "1.0.0"},
          {publicPackage: {name: "my_package", type: "npm"}, version: "1.0.0"}
        ],
        labelName: "my_label1"
      }
    )
  }
}
```

#### Remove labels from a package

```
mutation {
  customCatalogLabel {
    removeCustomCatalogLabelsFromPublicPackage(
      publicPackageLabels:{
        labelNames:["my_label", "my_label2"]
        publicPackage:{name:"my_package", type:"npm"}})
   }
}
```

#### Remove labels from a package version

```
mutation {
  customCatalogLabel {
    removeCustomCatalogLabelsFromPublicPackageVersion(
      publicPackageVersionLabels: {
        labelNames:["my_label1", "my_label2"]
        publicPackageVersion: {
          publicPackage: {name:"my_package", type:"npm"}
          version:"package_version"
        }
      }
    )
  }
}
```

#### Remove a label from multiple package versions

```
mutation {
  customCatalogLabel {
    removeCustomCatalogLabelFromPublicPackageVersions(
      publicPackageVersionsLabel: {
        labelName:"my_label1" 
        publicPackageVersions:[
          {publicPackage:{name:"my_package", type:"npm"} version: "1.0.0"} 
          {publicPackage:{name:"my_package", type:"npm"} version: "1.0.1"}
        ]
      }
    ) 
  }
}
```

#### Update a label

```
mutation {
  customCatalogLabel {
    updateCustomCatalogLabel(
  	label: {name: "my_label", updatedName: "my_label_new", updatedDescription: "updated description"}
    ) {
  	name
  	description
    }
  }
}
```

#### Delete a label

```
mutation {
  customCatalogLabel {
    deleteCustomCatalogLabel(label:{name:"my_label"})
   }
}
```

#### Delete multiple labels

```
mutation {
  customCatalogLabel {
    deleteCustomCatalogLabels(labels:[{name:"x1"}, {name:"x2"}])
  }
}
```

#### GraphQL API Error Messages

| Error Message                                                                                                          | Description                                                                                                                                                                                                                                                                                                                                                                  |
| ---------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Creating more than 500 labels is not supported                                                                         | <p>Returned from </p><p><code>CreateCustomCatalogLabels</code> if given too many labels to create</p>                                                                                                                                                                                                                                                                        |
| Assigning more than 1 label is not supported                                                                           | <p>Returned from </p><p><code>AssignCustomCatalogLabelsToPublicPackage</code> and <code>AssignCustomCatalogLabelsToPublicPackageVersion</code> if given too many labels to assign</p>                                                                                                                                                                                        |
| Some of the labels already exist                                                                                       | <p>Returned from </p><p><code>CreateCustomCatalogLabels</code> and <code>CreateCustomCatalogLabel</code> if given labels that already exist.</p>                                                                                                                                                                                                                             |
| Deleting more than 500 labels is not supported                                                                         | <p>Returned from </p><p><code>DeleteCustomCatalogLabels</code>if given too many labels to delete</p>                                                                                                                                                                                                                                                                         |
| Removing more than 500 labels assignments in a single operation is not supported                                       | <p>Returned from </p><p><code>RemoveCustomCatalogLabelsFromPublicPackage</code> and <code>RemoveCustomCatalogLabelsFromPublicPackageVersion</code> if given too many labels to remove their assignment and from <code>RemoveCustomCatalogLabelFromPublicPackageVersions</code> if given too many versions to remove their assignment</p>                                     |
| Assigning a label to more than 500 package versions in a single operation is not supported                             | <p>Returned from </p><p><code>AssignCustomCatalogLabelToPublicPackageVersions</code> if given too many versions for label assignment</p>                                                                                                                                                                                                                                     |
| A label name cannot be empty                                                                                           | <p>Returned from </p><p><code>CreateCustomCatalogLabe</code>l,and <code>CreateCustomCatalogLabels</code> if given empty name for new label, and <code>UpdateCustomCatalogLabel</code> if given label to rename and the new name is empty.</p>                                                                                                                                |
| Labels must be specified for the assignment                                                                            | <p>Returned from </p><p><code>AssignCustomCatalogLabelsToPublicPackage</code> and <code>AssignCustomCatalogLabelsToPublicPackageVersion</code> if list of labels to assign is empty</p>                                                                                                                                                                                      |
| A requested package version already has a label assigned. More than one label per package version is not supported yet | <p>Returned from </p><p><code>AssignCustomCatalogLabelsToPublicPackageVersion</code> if the version already has a label, from <code>AssignCustomCatalogLabelToPublicPackageVersions</code> if one of the given versions already has a label</p>                                                                                                                              |
| A requested package already has a label assigned. More than one label per package is not supported yet                 | <p>Returned from </p><p><code>AssignCustomCatalogLabelsToPublicPackageVersion</code> if the package is already assigned a label, from AssignCustomCatalogLabelsToPublicPackageVersion if the version’s package has a label, and RemoveCustomCatalogLabelFromPublicPackageVersions if any of the versions’ packages already has a label</p>                                   |
| Label name is too long {label\_name}, must have fewer than 1000 characters                                             | <p>Returned from </p><p><code>CreateCustomCatalogLabels</code> and <code>UpdateCustomCatalogLabel</code> if given a label that’s too long</p>                                                                                                                                                                                                                                |
| Label description is too long {label\_description}, must have fewer than 10000 characters                              | <ul><li><code>{label_description}</code> will be the requested label description</li><li><p>Returned from </p><p><code>CreateCustomCatalogLabels</code>and <code>UpdateCustomCatalogLabel</code> if given a description that’s too long</p></li></ul>                                                                                                                        |
| Label {label\_name} does not exist                                                                                     | <ul><li><code>{label_name}</code> will be the requested label name</li><li><p>Returned from </p><p><code>UpdateCustomCatalogLabel</code>, if given a label to update that, doesn’t exist</p></li></ul>                                                                                                                                                                       |
| Label with name {label\_name} already exists                                                                           | <ul><li><code>{label_name}</code> will be the requested label name</li><li><p>Returned from </p><p><code>UpdateCustomCatalogLabel</code> if given a label to rename and the new name already exists as another label</p></li></ul>                                                                                                                                           |
| The following labels were not found:\[ {label\_names}]. All labels must exist when assigned                            | <ul><li><code>{label_names}</code> will be replaced with comma separated list of label names</li><li><p>Returned from </p><p><code>AssignCustomCatalogLabelsToPublicPackage</code>, <code>AssignCustomCatalogLabelsToPublicPackageVersion</code>, and <code>AssignCustomCatalogLabelToPublicPackageVersions</code> if labels given for assignments are missing</p></li></ul> |

<br>
