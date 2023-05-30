# Data Transformation Script ContentStore to UDM

This repository contains a data transformation script that facilitates the transformation of documents and folders between two MongoDB databases. The script performs various operations to transform the data and migrate it to a target database.
The data used for this has been extracted from Alfresco. To make it work with other source systems you will need to adjust it accordingly.

## Main

The entry point of the script is the `transformAll()` function. It performs the following steps:

1. Connects to the source and target MongoDB databases.
2. Groups the documents by version series ID.
3. Retrieves the latest version document from each group.
4. Calls the `transformRecordOrContainer()` function for each latest version document.

## Functions and Query

This script contains several functions to handle different aspects of the data transformation process. Here are the key functions:

- `getAcls(_id)`: Retrieves the ACLs (Access Control Lists) associated with a document.
- `getBinaryInfo(_id)`: Retrieves the binary information (extension, size, references) of a given record.
- `groupDocByVersion()`: Groups the documents by version series ID.
- `transformRecordOrContainer(doc, versionDocs)`: Transforms a document or folder, including required and optional properties, ACLs, and versions.
- `mapObjectACL(_id)`: Maps the ACLs to a common ACL model.
- `mapVersions(versionDocs)`: Maps the versions of a document to the desired format.
- `mapDocument(doc, versionDocs)`: Maps a document to the transformed model, including file information, MIME type, versions, and properties.
- `mapFolder(doc, versionDocs)`: Maps a folder to the transformed model, including container information and properties.

## Usage

To use this script, follow these steps:

1. Update the `targetDBName` and `sourceDBName` variables in the script to match your MongoDB database names.
