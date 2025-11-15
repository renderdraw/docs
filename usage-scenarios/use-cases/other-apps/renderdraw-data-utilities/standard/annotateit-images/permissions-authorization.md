# Permissions / Authorization

{% hint style="info" %}
By default, a user can upload their own files to Salesforce, so no user permissions are needed.
{% endhint %}

{% hint style="info" %}
Unlike our other components, there is no Administration aspect to AnnotateIt, only allowing users to edit photos and attachments within Salesforce
{% endhint %}

### Special Access Rules for users that are not Administrators that need to edit other images

* Customer and Partner Portal users must have the “View Content in Portal” permission to query content in libraries where they have access.
* Customer and Partner Portal users can only publish, version, or edit documents if they have a Salesforce CRM Content feature license.
* All users with a content feature license can create versions in their personal library.
* Users (including users with the “View All Data” permission) can only query files they have access to, including:
  * All Salesforce CRM Content files in libraries they're a member of and in their personal library, regardless of library permissions (API version 17.0 and later).
  * All Chatter files they own, posted on their profile, posted on groups they can see, and shared directly with them (API version 21.0 and later).
* All users can update versions in their personal library.
* The owner of a version or document can update the document if they are a member of the library, regardless of library permissions.
* To update a Salesforce CRM Content document, the user must be a member of the library with one of these library privileges enabled:
  * “Add Content”
  * “Add Content On Behalf of Others”
  * “Manage Library”
* \
