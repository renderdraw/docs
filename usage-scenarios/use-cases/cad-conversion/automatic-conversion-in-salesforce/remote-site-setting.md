# Remote Site Setting

In Salesforce, a Remote Site Setting is a security feature that allows for external network connections from your Salesforce instance to an external server via protocols like HTTP and HTTPS. It's used to register and whitelist the external server endpoint that your org will communicate with.

In this case, you're wanting to create a Remote Site Setting for the RenderDraw CAD Conversion API endpoint. This is necessary because any Apex callouts to this external server would fail unless the server is first registered in the Remote Site Settings. This includes both synchronous and asynchronous Apex callouts.

By creating this Remote Site Setting, you are allowing your Salesforce org to communicate with the RenderDraw CAD Conversion API to convert CAD files inside Salesforce.

**Step-by-step guide to create a Remote Site Setting in Salesforce:**

1. Log in to your Salesforce org.
2. Click on the App Launcher (grid icon on the upper left).
3. In the App Launcher search box, type `Remote Site Settings` and select it from the dropdown list.
4. Click the `New Remote Site` button.
5. In the `Remote Site Name` field, enter `renderdrawCADConversion`.
6. In the `Remote Site URL` field, enter `https://convert.renderdraw.us`.
7. Make sure `Disable Protocol Security` is not checked. If it is, uncheck it.
8. In the `Description` field, enter `RenderDraw CAD Conversion API endpoint used when automation or APEX callouts are used to convert CAD files inside Salesforce.`
9. Click the `Save` button.

The new Remote Site Setting for the RenderDraw CAD Conversion API is now created and active.

**Security Implications:**

It's important to note that adding a Remote Site Setting reduces the protections of your Salesforce org's data to external servers. Only add Remote Site Settings for trusted external servers.

Always ensure the endpoint server is secure, and the data transmitted between Salesforce and the server is encrypted, ideally via HTTPS. Also, limit the data transmitted to what's strictly necessary to fulfill the purpose of the interaction.

Lastly, review your Remote Site Settings periodically and deactivate or delete those that are no longer needed to minimize potential attack vectors.
