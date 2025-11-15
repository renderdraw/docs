# Custom Component Interaction with Renderer

### D**igital Twin Action Metadata: Customizing Your DigitalTwin LWC Component Experience**

As you dive deep into the immersive world of asset visualization with the RenderDraw Digital Twin package, we understand that customization is crucial. That's why we've introduced the Custom Metadata Type: **RenderDraw Digital Twin Action**, allowing Salesforce administrators to tailor the DigitalTwin component's UI to meet specific business needs.&#x20;

<figure><img src="../../../.gitbook/assets/image (63).png" alt=""><figcaption></figcaption></figure>

Here's a quick guide to understanding and utilizing these settings:

<figure><img src="../../../.gitbook/assets/image (64).png" alt=""><figcaption></figcaption></figure>

#### **Fields Overview:**

1. **Label**: Assign a unique name to the action
   1. This will be your reference point
2. **RenderDraw Digital Twin Action Name**: Auto populates based on Label field
3. **Display in Popup**: Decide where you want the action to display&#x20;
   1. If set to `true`, your action will appear in a pop-up window that overlays the drawing
   2. If set to `false`, it will be neatly integrated into a sidebar alongside the drawing
4. **Flow Name**: Input the **API name** of the **Lightning flow** you wish to display
   1. This is typically a screen flow tailored for the chosen action
5. **Action Label**: Craft a user-friendly label
   1. This is what your **users will see** in the action menu when they wish to invoke your flow
6. **Action Icon**: Define the look of your action using any Salesforce icon name
   1. This icon will be showcased in the action menu
7. **Order**: Determine the sequence of your action in the context menu.&#x20;
   1. A lower order will prioritize its position
8. **RenderDraw Digital Twin Settings**: Link your action to a specific digital twin setting
   1. This dictates when your action will be displayed

#### **Interacting with the DigitalTwin Component:**

When designing your custom flows, remember to set up **string input parameters** for **both** `recordId` and `contextId`. These parameters are essential to retrieve relevant data and ensure seamless interaction between the flow and the DigitalTwin component.

#### **Advanced: Interacting with the Renderer**

For those looking to create even more dynamic interactions, our renderer's public API is at your disposal. Utilize the following format to call any of our public API methods:

```javascript
const payload = {
	contextId: this.contextId,
	name: "showToastNotification",
	parameters: {
		title: this.title,
		mode: this.mode,
		message: this.message,
		messageTemplate: this.messageTemplate,
		iconName: this.iconName,
		type: this.type,
		duration: this.duration,
		messageTemplateData: this.messageTemplateData
	}
};
publish(this.messageContext, CANVAS_INTERACTION_CHANNEL, payload);

```

To facilitate these interactions, ensure you have the necessary imports in your module:

```javascript
import { publish, subscribe, MessageContext } from "lightning/messageService";
import CANVAS_INTERACTION_CHANNEL from "@salesforce/messageChannel/RDraw__Canvas_Interaction__c";
```

The RenderDraw Digital Twin package offers you a world of customizability. By understanding and leveraging the Digital Twin Action metadata, you can enhance the user experience and meet the unique demands of your business. Dive in, customize, and let your DigitalTwin component truly reflect your vision.
