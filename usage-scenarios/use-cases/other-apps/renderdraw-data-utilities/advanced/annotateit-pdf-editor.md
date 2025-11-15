# AnnotateIt! PDF Editor

{% embed url="https://youtu.be/MmD_M98Y0fI" fullWidth="true" %}

AnnotateIt - PDF Editor is a Salesforce Lightning Web Component (LWC) that provides functionality for users to select, edit, and save PDF files. The component can be used on lightning homepages, record pages, and within flow screens. It allows users to annotate and save PDFs natively within the Salesforce platform.

#### Key Features

1. **PDF Selection and Editing**: Users can select a PDF file and edit it directly within Salesforce. This file can either be one already stored in Salesforce, or an external PDF file.
2. **Saving and Downloading PDFs**: Once a PDF has been edited, it can be saved within Salesforce or downloaded for external use.
3. **Toast Messages**: Provides users with success or error messages after saving or downloading a PDF.
4. **Flow Navigation**: Within a Lightning Flow, you can use the PDF Editor to navigate between different flow screens.

#### Configuration

The AnnotateIt - PDF Editor module can be configured with the following properties:

* `pdfDocId`: Enter the Document Id of the PDF to be annotated.
* `showSaveAs`: If you enable this option (set to `true`), it will show the 'Save As' dialog, allowing the user to save the image as a new ContentDocument.
* `recordId`: Optionally, you can set the record Id to relate the edit/annotation. This is used when the 'Save As' dialog is shown.
* `callFlowNextOnProceed`: If a file is saved as a new ContentDocument, the `pdfDocId` will be updated with the newly saved document. If you enable this (set to `true`), it will trigger the 'Next' or 'Finish' within a Lightning Flow when 'Save' is clicked.

To set these properties, navigate to the configuration section of the LWC where you're deploying the AnnotateIt - PDF Editor. This could be the Lightning App Builder for a homepage or record page, or the Flow Builder for a flow screen.

This tool provides a powerful way for users to interact with PDFs directly within Salesforce, adding a new layer of flexibility and interactivity to your Salesforce environment.
