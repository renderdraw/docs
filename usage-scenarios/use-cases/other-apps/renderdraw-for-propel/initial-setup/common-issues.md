# Common Issues

### Issues during Conversion

#### Was there an issue communicating with the Conversion API?

If the Salesforce Org's settings were changed, you can setup the CSP and CORS/ Secure site settings by reviewing this document [cad-conversion](../../../cad-conversion/ "mention")&#x20;

#### Did the file get successfully converted but is not showing under attachments?

This is typically an issue with your org and data settings. Check the Item revision to ensure it is not marked "Released". There are often rules in orgs that restrict adding Item Attachments. Check your org's Files tab to see if your file was added (it should share a filename with a different extension).&#x20;



