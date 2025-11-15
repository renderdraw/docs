---
description: >-
  Have CAD files added to your Salesforce system in bulk, where manually
  converting would be a chore?
---

# Automatic Conversion in Salesforce

With just a few clicks, you can set up Salesforce to automatically convert CAD files when they are uploaded. Here's how:

**1.** [**Create an Integration User**](integration-user.md): We all need a trusted sidekick. In Salesforce, that's your Integration User. This user has the special permissions needed to perform specific tasks like raising platform events. Get your Integration User ready for action by setting them up with the 'RenderDraw Integration User' permission set.

**2.**[ **Register the Remote Site Setting**](remote-site-setting.md): Salesforce needs to know it can trust our RenderDraw CAD Conversion API, like a friend inviting you over to their house for the first time. You create a 'Remote Site Setting' to tell Salesforce it's okay to make callouts to our API endpoint. Just make sure 'Disable Protocol Security' is not checked - we want to keep this relationship secure!

**3.** [**Get Connected with the Connected App**](setup-connected-app.md): Think of the 'Connected App' as the secret handshake between Salesforce and RenderDraw. It's how Salesforce knows it's communicating with the real deal.

**4. Assign the Integration User to the Connected App**: Now that we've made the secret handshake, let's ensure our trusted Integration User knows it too. Assign your Integration User to the 'CADConversion' connected app.

**5. Let the Integration User take the stage with Client Credentials Flow**: In the world of Client Credentials Flow, the spotlight is on the user who created the connected app. Make sure that you log in as the Integration User to create or update the connected app.

**6.** [**Custom Settings, just the way you like it**](setup-custom-settings-for-triggering-conversion.md): Custom Settings are like your favorite sandwich - everyone likes it a bit different. Adjust the settings in 'CAD Conversion App Setting' to determine when the CAD Conversion feature is triggered and which objects it should apply to.

**7.** [**Test your work with some files**](test-your-files.md): Upload a file to a Salesforce Opportunity and watch the CADConversionContentVersionTrigger work its magic! The converted files will appear in the 'Related -> Files' section of the Opportunity record.

**8.** [**Extend your skills with Platform Events**](extending-the-integration-using-platform-events.md): Want to become the ultimate CAD Conversion Guru? You can create Flows that trigger when CAD Conversion events occur. With these Flows, you can update records, send notifications, or even call out to external systems!

Keep in mind, every great magician tests their tricks before a show. Make sure to test all changes in a sandbox or developer environment before deploying to production. Now, let the CAD Conversion magic begin!

<figure><img src="../../../../.gitbook/assets/ContentDocument API endpoint - external.png" alt=""><figcaption></figcaption></figure>

1.
