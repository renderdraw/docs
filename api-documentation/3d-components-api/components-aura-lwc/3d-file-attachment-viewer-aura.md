# 3D File Attachment Viewer (Aura)

### Description

Salesforce doesn't have a file preview for 3D filetypes like GLTF, GLB, STL and OBJ. The FileSelector component allows for users to upload and view 3D files and associate them to a given record object.

### When to use the FileSelector&#x20;

Any time you want to display and allow users to view 3D files on a Salesforce Record.&#x20;

### Attributes

| **NAME**       | **TYPE** | **REQUIRED** | **DEFAULT** | **DESCRIPTION**                                                               |
| -------------- | -------- | ------------ | ----------- | ----------------------------------------------------------------------------- |
| recordId       | string   | false        |             | Id of the Salesforce Record in which you fetch the associated rendering files |
| showFileUpload | boolean  | false        | TRUE        | Id of the Salesforce Record in which you fetch the associated rendering files |
