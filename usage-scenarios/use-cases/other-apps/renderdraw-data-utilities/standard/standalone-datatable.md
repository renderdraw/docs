# Standalone Datatable

**Component Overview** The `Standalone_DataTable` is a powerful, customizable Lightning Web Component that can be used to display data in a flexible table format. Its primary use cases include:

1. Displaying data from a standalone component definition record specified by the `recordname` property.
2. Displaying the data in different sizes (`Small`, `Medium`, `Large`, `Jumbo`, `Stretch`) controlled by the `size` property.
3. Selecting a record and triggering a flow or raising an event for other components to handle.

**Usage** This component can be used on three types of pages:

1. Record Pages: Use it to display related data on a record page.
2. App Pages: Use it to show relevant data on a custom app page.
3. Flow Screens: Use it within a flow to show data and select a record to perform actions.

**Configuration** Here are the component properties that you can set in the Lightning App Builder or a Flow:

* `recordname`: This property sets the standalone component definition record. Use the record picker to select the appropriate record.
* `size`: This property determines the height of the data table component. Choose from `Small`, `Medium`, `Large`, `Jumbo`, or `Stretch` based on your layout requirements.
* `recordId`: (Only for flows) This property holds the selected record's ID. It can be used to perform further actions in the flow.

**Events** The `Standalone_DataTable` component raises an event when a record is selected in the table:

* `recordselected`: This event is fired when a user selects a record from the table. The event includes the `recordId` of the selected record, which can be captured and used in your custom event handler or flow.

Remember that to use this component, you'll need to have it installed in your org and have the necessary permissions to access and configure Lightning Web Components in the Lightning App Builder.

This component is a powerful way to present tabular data in your Salesforce org and can be tailored to your specific requirements using its properties and events.
