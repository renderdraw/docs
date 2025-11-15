# Setup Custom Settings for Triggering Conversion

1. Click on `Setup` (gear icon on the upper right).
2. In the Quick Find search box, type `Custom Settings` and select it from the dropdown list.
3. You will see a list of all custom settings available in your organization. Find `CAD Conversion App Setting` (it may appear as `RDraw__CADConversionAppSetting__c` depending on your configuration) in the list and click `Manage` next to it.
4. Now you will see a list of existing settings. Click on `Edit` in the row of the `Default Organization Level Value` record.
5.  Adjust the following Custom Fields as per your requirements:

    **a. Trigger\_on\_Content\_Create\_\_c (Checkbox)**

    * This field determines if the CAD Conversion feature is enabled. If checked, the CAD conversion trigger will run when new ContentVersion records are created.

    **b. Related\_Objects\_\_c (Textarea)**

    * This field contains the names of the objects for which the CAD conversion feature should be applied. If it contains '\*', the conversion will be applicable to all objects. If it contains specific object API names (one per line), the conversion will only apply to those objects.
6. After you have made the changes, click `Save`.

Now the `RDraw__CADConversionAppSetting__c` Custom Setting is adjusted to your organization's requirements.

Please note changes in these settings will affect how the CAD Conversion feature works in your organization. Adjust them wisely, and contact us for any assistance or queries regarding these settings.
