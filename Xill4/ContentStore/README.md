# Script Documentation

## Setup
- Set the `targetDBName` variable to the name of the target database.
- Connect to the target database using `Mongo.connect()`.
- Connect to the source database using `Mongo.connect(")`.

## Main Functionality

### `transformAllVersions()`
- This function transforms all document versions.
- It iterates over each document in the `allDocsVersions()` result.
- For each document, it iterates over its versions and performs the following steps:
  - Creates a transformed document object.
  - Creates a model object.
  - Sets required properties in the model using the `mapVersionsRequiredProperties()` function.
  - Maps the document properties using the `mapDocument()` function.
  - Sets additional version-related properties.
  - Updates the transformed document in the target database.
  - Maps ACL document using the `mapACLDoc()` function.
  - Creates a binary object using the `createBinary()` function.

### `transformAllFolders()`
- This function transforms all folders.
- It iterates over each folder in the `allFolders()` result.
- For each folder, it performs the following steps:
  - Transforms the container using the `transformContainer()` function.
  - Maps the ACL folder using the `mapACLFolder()` function.

## Functions and Queries

### `allDocsVersions()`
- Retrieves all documents with versions from the source database.
- Returns the result of the MongoDB aggregation pipeline.

### `allFolders()`
- Retrieves all folders from the source database.
- Returns the result of the MongoDB find query.

### `transformContainer(doc)`
- Transforms a container document.
- It creates a transformed document object and a model object.
- Sets required properties based on the document kind.
- Updates the transformed document in the target database.

### `mapVersionsRequiredProperties(v)`
- Maps the required properties for document versions.
- Returns a model object with the mapped properties.

### `mapRequiredProperties(doc)`
- Maps the common required properties for containers and records.
- Returns a model object with the mapped properties.

### `mapObjectOptional(doc)`
- Maps the optional properties for containers and records.
- Returns a model object with the mapped properties.

### `mapDocument(doc)`
- Maps the document properties.
- Returns a model object with the mapped properties.

### `createBinary(doc)`
- Creates a binary object for each version.
- Updates the binary object in the target database.
- Updates the source document with the ID of the created binary object.

### `mapFolder(doc)`
- Maps the folder properties.
- Returns a model object with the mapped properties.

### `mapACLFolder(doc)`
- Maps the ACL properties for folders.
- Creates ACL objects and updates the source folder with the ACL IDs.

### `mapACLDoc(doc)`
- Maps the ACL properties for documents.
- Creates ACL objects and updates the source document with the ACL IDs.

