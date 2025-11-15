# Setup Field on Catalog Object

#### Creating a Custom Field in Salesforce: 2D Scene Settings

Follow these steps to create a custom field in Salesforce that matches the "2D Scene Settings" field shown in the image.

**Prerequisites**

* You must have the necessary permissions to create and modify fields in Salesforce.

**Step-by-Step Instructions**

1. **Navigate to Setup**:
   * Log in to your Salesforce account.
   * Click on the gear icon in the upper right corner and select "Setup."
2. **Go to Object Manager**:
   * In the Setup menu, find and click on "Object Manager."
3. **Select the Object**:
   * From the list of objects, find and select the object named `Category`.
4. **Fields & Relationships**:
   * In the left-hand sidebar, click on "Fields & Relationships."
5. **Create a New Field**:
   * Click on the "New" button to create a new field.
6. **Select Data Type**:
   * Choose "Long Text Area" as the data type.
   * Click "Next."
7. **Enter Field Details**:
   * **Field Label**: Enter `2D Scene Settings`.
   * **Field Name**: This will automatically populate based on the Field Label, but you can edit it if needed. Ensure it is `X2D_Scene_Settings`.
   * **Length**: Enter `131,072`.
   * **Number of Visible Lines**: Enter `3`.
8. **Set Field-Level Security**:
   * Click "Next" to proceed to the Field-Level Security settings.
   * Adjust the field visibility settings as required for your organization.
   * Click "Next."
9. **Add to Page Layouts**:
   * This is a hidden field only for internal settings, so we avoid adding it to any layouts.
   * Click "Save" to create the field.
10. **Verification**:
    * After saving, verify that the field has been created correctly by navigating to the "Fields & Relationships" section of the `Category` object.
    * Ensure the field appears as expected and matches the details shown in the provided image.

**Additional Notes**

* **Data Sensitivity Level**: Set according to your organization's data handling policies.
* **Compliance Categorization**: Ensure this field complies with your organization's compliance requirements.
* **Created By** and **Modified By**: These fields will automatically show the user who created and last modified the field along with the timestamp.

By following these steps, you will create a "2D Scene Settings" field in Salesforce that matches the one shown in the image.
