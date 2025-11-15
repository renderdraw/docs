---
description: A sample component that can be added to a page for testing the LMS messages
---

# Code Example of Listening to LMS Events

{% tabs %}
{% tab title="test_LMS.js" %}
```javascript
import { LightningElement, wire, track } from "lwc";
import { publish, subscribe, MessageContext } from "lightning/messageService";
import CANVAS_INTERACTION_CHANNEL from "@salesforce/messageChannel/RDraw__Canvas_Interaction__c";
import CANVAS_INITIALIZED_CHANNEL from "@salesforce/messageChannel/RDraw__Canvas_Initialized__c";
import CANVAS_ELEMENTSELECTED_CHANNEL from "@salesforce/messageChannel/RDraw__Canvas_ElementSelected__c";
import CANVAS_ELEMENT_HOVERED_CHANNEL from "@salesforce/messageChannel/RDraw__Canvas_ElementHovered__c";

export default class Test_LMS extends LightningElement {
	@track receivedMessage = {};

	@wire(MessageContext) messageContext;
	subscription = null;

	@track renderContextId;
	@track sceneSettings;
	// Variables to store the input values
	title = "";
	mode = "";
	message = "";
	messageTemplate = "";
	iconName = "";
	type = "";
	duration = 0;
	messageTemplateData = "";
	eventName = "";
	connectedCallback() {
		this.subscribeToCanvasInitializedChannel();
		this.subscribeToElementClickedMessageChannel();
		this.subscribeToElementHoveredMessageChannel();
	}
	subscribeToElementClickedMessageChannel() {
		subscribe(this.messageContext, CANVAS_ELEMENTSELECTED_CHANNEL, (message) => {
			this.handleElementMessage(message, "Element Clicked");
		});
	}
	subscribeToElementHoveredMessageChannel() {
		subscribe(this.messageContext, CANVAS_ELEMENT_HOVERED_CHANNEL, (message) => {
			this.handleElementMessage(message, "Element Hovered");
		});
	}
	handleElementMessage(message, messageType) {
		let param = { ...message };
		if (param.recordId) {
			param.recordId = JSON.stringify({ ...param.recordId }, null, 2);
		}
		this.receivedMessage = param;
		this.eventName = messageType;
	}
	subscribeToCanvasInitializedChannel() {
		if (!this.subscription) {
			this.subscription = subscribe(this.messageContext, CANVAS_INITIALIZED_CHANNEL, (message) => this.handleCanvasInitializedMessage(message));
		}
	}
	handleCanvasInitializedMessage(message) {
		this.renderContextId = message.renderContextId;
		this.sceneSettings = message.sceneSettings;
	}

	// Event handlers to capture the input values
	handleTitleChange(event) {
		this.title = event.target.value;
	}
	handleModeChange(event) {
		this.mode = event.target.value;
	}
	handleMessageChange(event) {
		this.message = event.target.value;
	}
	handleMessageTemplateChange(event) {
		this.messageTemplate = event.target.value;
	}
	handleIconNameChange(event) {
		this.iconName = event.target.value;
	}
	handleTypeChange(event) {
		this.type = event.target.value;
	}
	handleDurationChange(event) {
		this.duration = event.target.value;
	}
	handleMessageTemplateDataChange(event) {
		this.messageTemplateData = event.target.value;
	}

	publishShowToastNotificationMessage() {
		const payload = {
			contextId: this.renderContextId,
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
	}
}
```
{% endtab %}

{% tab title="test_LMS.html" %}
```html
<template>
	<lightning-card title="LMS Messaging testing harness">
		<div class="slds-var-m-around_small" style="background: white">
			<h5>{renderContextId}</h5>

			<lightning-tabset>
				<lightning-tab label="Received Messages">
					<template if:true={receivedMessage}>
						<div>
							<p><strong>contextId:</strong> {receivedMessage.contextId}</p>
							<p><strong>elementName:</strong> {receivedMessage.elementName}</p>
							<p><strong>elementId:</strong> {receivedMessage.elementId}</p>
							<p><strong>elementType:</strong> {receivedMessage.elementType}</p>
							<p><strong>record:</strong> {receivedMessage.record}</p>
							<p><strong>eventName:</strong> {eventName}</p>
						</div>
					</template>
				</lightning-tab>
				<lightning-tab label="Send Message">
					<!-- UI elements to capture the method parameters -->
					<lightning-input label="Title" onchange={handleTitleChange}></lightning-input>
					<lightning-input label="Mode" onchange={handleModeChange}></lightning-input>
					<lightning-input label="Message" onchange={handleMessageChange}></lightning-input>
					<lightning-input label="Message Template" onchange={handleMessageTemplateChange}></lightning-input>
					<lightning-input label="Icon Name" onchange={handleIconNameChange}></lightning-input>
					<lightning-input label="Type" onchange={handleTypeChange}></lightning-input>
					<lightning-input label="Duration" onchange={handleDurationChange} type="number"></lightning-input>
					<lightning-input label="Message Template Data" onchange={handleMessageTemplateDataChange}></lightning-input>

					<!-- Button to trigger the method call -->
					<lightning-button
						variant="brand"
						label="Show Toast Notification"
						title="Show Toast Notification"
						onclick={publishShowToastNotificationMessage}
						class="slds-m-left_x-small"
					></lightning-button>
				</lightning-tab>
			</lightning-tabset>
		</div>
	</lightning-card>
</template>
```
{% endtab %}

{% tab title="test_LMS.js-meta.xml" %}
```xml
<?xml version="1.0" encoding="UTF-8"?>
<LightningComponentBundle xmlns="http://soap.sforce.com/2006/04/metadata">
    <apiVersion>57.0</apiVersion>
    <isExposed>true</isExposed>
    <masterLabel>test_LMS</masterLabel>
    <targets>
        <target>lightning__RecordPage</target>
        <target>lightningCommunity__Page</target>
        <target>lightningCommunity__Default</target>   
        <target>lightning__FlowScreen</target>
        <target>lightning__AppPage</target>
        <target>lightning__UtilityBar</target>
    </targets> 
</LightningComponentBundle> 
```
{% endtab %}
{% endtabs %}
