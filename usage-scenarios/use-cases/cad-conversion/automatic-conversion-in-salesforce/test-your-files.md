# Test your Files



**Step 1: Access the Record**

1. Click on `App Launcher` (grid icon in the upper left corner).
2. In the search box, type `Opportunity` and select `Opportunity` from the dropdown.
3. Select the specific Opportunity you want to work with.

**Step 2: Upload a File to Salesforce Files**

1. In the Opportunity record, click on `Related`.
2. Scroll down to `Files` section.
3. Click on `Upload Files` button.
4. Browse and select the file from your computer you want to upload.
5. Click on `Open` to start the upload process.

**Step 3: Activate the CADConversionContentVersionTrigger**

1. After the file upload is complete, `CADConversionContentVersionTrigger` should be automatically activated and start the CAD Conversion process.
2. Wait for a few minutes for the conversion process to finish. The duration will depend on the size and complexity of the file.

**Step 4: Check the Results**

1. Refresh the page.
2. Go back to `Related` -> `Files` section.
3. You should now see additional files which are the result of the CAD Conversion process.

**Step 5: Interact with the Converted Files**

1. If the RenderDraw File Attachment Renderer is added to the layout, you can use it to interact with the converted files.
2. Click on the file you want to interact with and it should open with the RenderDraw File Attachment Renderer.

If you don't see additional files after the conversion, or if you have any trouble interacting with them, there might be an issue with the trigger or renderer. Make sure they are configured correctly and active. Always follow best practices for managing changes in your Salesforce environment.
