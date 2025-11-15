# Integration User

*   Add Integration User

    Create an Integration User

    1. In Salesforce, click on `Setup` (gear icon in the upper right corner).
    2. In the Quick Find box, type `Users` and select `Users` under `Administer -> Manage Users`.
    3. Click on `New User`.
    4. Fill out the necessary details. Make sure you assign a Profile that has enough permissions for the tasks this Integration User will perform.
    5. Click `Save`.

{% hint style="info" %}
Name your user something meaningful. Having a single Integration user for all of your integrations can lead to confusion as to what records were created by what service. In this instance, we recommend naming your Integration User "RenderDraw Integration User" to avoid a general "Integration User" audit trail confusion.

<img src="../../../../.gitbook/assets/image (31).png" alt="" data-size="original">
{% endhint %}

* Assign Permission Set **RenderDraw Integration User** to the Integration User\
  This permission set provides access to  the integration user to raise platform events.
