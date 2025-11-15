# Setup Connected App



**Step 1: Locate the Connected App**

1. From Salesforce home, click on the `App Launcher` (grid icon on the top left corner), then find and open `App Manager`.
2. In the App Manager, find the `CADConversion` connected app. You can use the search box to filter the results.

**Step 2: Update the Custom Setting**

1. From Salesforce home, click on the `App Launcher` again, then find and open `Custom Settings`.
2. On the `Custom Settings` page, find the `CAD Conversion App Setting`. Click on `Manage` next to it.
3. Click `New` to create a new setting, or `Edit` if a setting already exists.
4. In the new page, there should be fields for the objects to use and whether or not you want to enable the document trigger. A default of \* is in the object list, which means any document uploaded to any object type will be tested and converted if it is a CAD file. If you want to limit this to a certain set of objects, remove the \* entry and list each object you want to observe on a separate line, this will be the technical or API name of the object, e.g. Product2 vs Product etc.&#x20;
5. Click `Save`.
6.  Apply Integration User to the app&#x20;



    **Assign the Integration User to the Connected App**

    1. In Salesforce, click on `Setup`.
    2. In the Quick Find box, type `App Manager` and select `App Manager` under `Platform Tools -> Apps`.
    3. Find the `CADConversion` connected app. Click on the dropdown arrow at the end of the row and select `Manage`.
    4. Scroll down to the `Profiles` section. Click `Manage Profiles`.
    5. In the new page, find the profile of the Integration User you created. Check the box next to it, and then click `Save`.

    **Setup Client Credentials Flow Run As Integration User**

    In Salesforce, the "Run As" user for Client Credentials Flow is typically determined by the user who created the connected app. So you may not directly assign the Integration User as the "Run As" user for Client Credentials Flow in Salesforce UI. You have to log in as the Integration User to create or update the connected app to ensure that this user is the "Run As" user for Client Credentials Flow.

    To ensure that you have everything set up correctly, you might need to review the `OAuth policies` for your connected app and ensure that `Permitted Users` is set to `Admin approved users are pre-authorized` and that the integration user's profile is in the list of `Profiles` which are authorized to use the app.

    Remember to adjust the permissions and settings to fit the security model for your specific situation. Always be careful when working with integration users and OAuth, as incorrect configurations can create security vulnerabilities.
