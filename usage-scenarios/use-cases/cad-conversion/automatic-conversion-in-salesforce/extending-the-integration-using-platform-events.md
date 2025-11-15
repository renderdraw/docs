# Extending the integration using Platform Events

During the CAD Conversion process, there are two possible Platform Events that can be fired based on the success or failure of the conversion. \
The same process can be followed for both the `CAD_Conversion_Created` and `CAD_Conversion_Error` events. We will use `CAD_Conversion_Created` as an example.

{% embed url="https://app.tango.us/app/embed/2f043777-17b8-4f12-abf0-abb69221ec54?iframe=true" %}

**Step 1: Access Flow Builder**

1. Click on `App Launcher` (grid icon in the upper left corner).
2. In the search box, type `Flows` and select `Flows` from the dropdown.

**Step 2: Create a New Flow**

1. Click on `New Flow`.
2. Select `Autolaunched Flow`.
3. Click `Next`.

**Step 3: Configure Trigger for the Flow**

1. Click on `Trigger` on the flow canvas.
2. Choose `When a platform event message is received`.
3. Click `Done`.
4. In the right panel, under `Configure the Trigger`, select `CAD_Conversion_Created` for `Platform Event`.
5. Click `Done`.

**Step 4: Add Elements to the Flow**

1. Click `+ Add` in the `Start` element.
2. You can add different elements like Assignment, Decision, Loop, etc., according to the business logic you want to implement.

For example:

* If you want to send an email notification when the event is triggered, you can add an `Action` element and choose `Send Email`.
* If you want to update a related record based on the information in the event, you can add an `Update Records` element.
* If you want to make different actions based on whether the conversion was successful or not, you can add a `Decision` element to check the `Successful_Conversion__c` field and branch the flow accordingly.

**Step 5: Save and Activate the Flow**

1. Click `Save`.
2. Provide a `Flow Label` and `Flow API Name`.
3. Click `Save`.
4. To make the flow active, click `Activate`.

Once the Flow is set up, it will be triggered each time a `CAD_Conversion_Created` platform event is published. The actions you set up in the flow will be executed, providing automatic responses to these events. With the information provided in the platform event, such as `Content_Version__c` or `Original_Content_Version__c`, the flow could update related records, send notifications, create tasks, or even call out to external systems, all depending on how you configure it.

Remember, the design of the Flow will depend largely on the specific requirements and business processes of your Salesforce environment. Always test thoroughly in a sandbox or developer environment before deploying to production.
