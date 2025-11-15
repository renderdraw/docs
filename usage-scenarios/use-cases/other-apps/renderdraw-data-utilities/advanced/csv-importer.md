# CSV Importer

The CSV Import - File Uploader is a Salesforce Lightning Web Component (LWC) that allows users to upload, map, and process CSV data files, including hierarchical data extracted from 3D models, directly into their Salesforce organization. The component provides visual feedback on data processing progress and offers functionalities to handle duplicate records.

#### Key Features

1. **CSV File Upload**: Users can upload a CSV file that they wish to import into Salesforce. This includes data extracted from 3D models, allowing users to represent complex hierarchical data structures within Salesforce.
2. **Object Selection**: After the CSV file has been uploaded, users can select the Salesforce object into which they want to import the CSV data.
3. **Column Mapping**: Users can map the CSV file columns to the fields of the selected Salesforce object, ensuring accurate translation of hierarchical data into Salesforce's data structure.
4. **Data Processing and Feedback**: Upon confirmation, the data import process begins. A progress indicator shows the current status of the import operation.
5. **Duplicate Records Handling**: If duplicate records are found, a popup window appears showing the duplicate records and providing options for handling these duplicates (e.g., skip or update).

#### Configuration

The CSV Import - File Uploader module comes with several customization options:

* **Spinner Display**: You can control the display of a spinner during loading processes with the `showSpinner` and `spinnerText` attributes.
* **Upload File Prompt**: The `showUploadFile` attribute controls the display of the file upload prompt.
* **Navigation Buttons**: Control the display and disabled state of Back and Next navigation buttons with the `showNavigation`, `backBtnDisabled`, and `nextBtnDisabled` attributes.
* **Process Indicator**: If you wish to display progress steps during the data processing phase, you can enable it using `showProgressSteps`.
* **Modal Popup for Duplicate Records**: Handle the visibility of the modal popup using the `showExistingRecords` attribute.

This component is designed to be embedded on lightning homepages, record pages, or flow screens. Use Salesforce's Lightning App Builder or Flow Builder to deploy it.

The CSV Import - File Uploader LWC not only simplifies the data import process, but it also opens up new possibilities for managing complex hierarchical data, including data from 3D models, within Salesforce.
