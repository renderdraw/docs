# RenderDraw Relationship Settings

#### Setup a RenderDraw Relationship Custom Metadata record for the Product Object

We also set up a custom field for "Drawing Reference". We'll use this field to map the 3D elements to a given record. It was set up as a text field of 255 length.

<figure><img src="../../../.gitbook/assets/image (55).png" alt=""><figcaption></figcaption></figure>

#### Setup a RenderDraw Relationship Custom Metadata Record for the Asset object:

This configuration will rely on the Product2 Relationship, referencing the Product Id on the Parent Relationship Settings Lookup field. We use the standard Asset object for this, and no other settings are needed, as they are controlled and provided by the parent settings on the Product Record we set up previously. \


<figure><img src="../../../.gitbook/assets/image (54).png" alt=""><figcaption></figcaption></figure>

#### Create a relay formula field for the Asset object.

We need a way to reference what field will be used to isolate and select elements related to a record in Salesforce. Due to system limitations, we need to reference the Drawing Reference field from the Asset directly. For this, we create a new field on the Asset object as a _formula_ field that returns text. The field is named "Drawing Reference", and will have a value of

Product2.Drawing\_Reference\_\_c

Referencing the field we created previously in a read-only way.

#### Create a Digital Twin Setting

We will edit the provided Asset Digital Twin record, and because we are using the standard Asset object, the provided fields all work out of the box.&#x20;

<figure><img src="../../../.gitbook/assets/image (56).png" alt=""><figcaption></figcaption></figure>

#### Ensure Lightning Web Security is enabled

<figure><img src="../../../.gitbook/assets/image (58).png" alt=""><figcaption></figcaption></figure>

To use the Digital Twin components, we have to enable the new Lightning Web Security so our packages can communicate &#x20;

The settings are now complete for Standard visual interaction for an Asset Digital Twin visualization. If you need to extend the standard functionality you can add Digital Twin Action records&#x20;
