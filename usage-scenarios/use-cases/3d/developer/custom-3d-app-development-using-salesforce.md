# Custom 3D App Development using Salesforce

### Creating a custom Component using AdvancedRenderer and Composition

Creating a custom component that wraps a 3D experience is simple. [Create a new Aura Component](https://developer.salesforce.com/docs/atlas.en-us.lightning.meta/lightning/components_create_cli.htm) and add the RDraw:AdvancedRenderer component to your component. Take a look at the Slots section of the AdvancedRenderer page.

```
<aura:component implements="lightning:availableForFlowScreens,flexipage:availableForAllPageTypes,force:hasRecordId"
    controller="TestCustomRenderDrawDevHelperController" access="public">
	<RDraw:AdvancedRenderer aura:id="renderer" displayContext="true"
                                loadingImage="{!v.loadingImage}" displaySidebar="{!v.showSidebar}" spitShine="True"
                                allowSelection="true" recordId="{!v.recordId}" size="Medium">
     	
     </RDraw:AdvancedRenderer>
</aura:component>
```

### &#x20;Interacting with our components

Currently, we support a wide variety Aura interactions, and our components can be  utilized directly due to their ever growing APIs. We follow a unidirectional data flow pattern by enabling our rendering components to respond to events, functions and attribute changes, then raising events to respond if data is to be returned. To respond, simply register a handler for that given event type.   More information about this can be found in Scene Data Interaction.

### Branding

#### Branding with Static Resources

Our image attributes (loadingImage, the imageURL parameter in the displayMedia method and the brandImageURL) all utilize the direct path to the image in order to render to your screen. If your org has access to the URL you supply for these parameters, your images will display properly.&#x20;

Often times, security is locked down within your org, causing images not to display whenever they are used from outside servers. To get around this, we can use Static Resources as the values for the url like this:&#x20;

This value represents an image we uploaded to a Static Resource, by name like this:

