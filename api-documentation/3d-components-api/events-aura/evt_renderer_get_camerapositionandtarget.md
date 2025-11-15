# EVT\_Renderer\_Get\_CameraPositionandTarget

### RDraw:EVT\_Renderer\_Get\_CameraPositionandTarget

#### Usage Notes

This event is raised when **getCameraPositionandTarget** is called on the AdvancedRenderer component. It returns a single. Handling this event allows for the receiving  of the details of that 3D node. These details can be used to apply 3D effects to the scene, or by looking up related data within the Salesforce platform.

#### Parameters

| **NAME** | **TYPE** | **REQUIRED** | **DESCRIPTION**                                      |
| -------- | -------- | ------------ | ---------------------------------------------------- |
| data     | object   | Yes          | The camera's position returned in JSON object format |

**“data” parameter structure**

```
{
   "target": object,
   "position": {
            "x": number,
            "y": number,
            "z": number,
            "alpha": number
            "beta": number
        }
}
```

#### &#x20;Example Usage

Choosing where to aim the camera is important when displaying 3D diagrams to users. Often, its easier to navigate where you want the users to look and get the position of the camera in order to re-use as part of a scene or a configuration.To do this, simply call the **getCameraPositionandTarget** on the instance of your renderer, after subscribing to the message type and you'll receive the position in JSON format.

Component

```
  <aura:component implements="lightning:availableForFlowScreens,flexipage:availableForAllPageTypes,force:hasRecordId">
      <aura:handler name="getCameraPostionandTarget" event="RDraw:EVT_Renderer_Get_CameraPositionandTarget"
        action="{!c.handleGetCameraPositionsandTarget}" />
         <lightning:card title="Get Camera Position">
         	<p class="slds-p-horizontal_small">
               <lightning:button title="Get Position"
                   onclick="{!c.handleGetCameraPositionButtonClicked}">Get Position
               </lightning:button>
            </p>
        </lightning:card>
  		<RDraw:AdvancedRenderer displayContext="true" aura:id="renderer"
                            nodeIgnoreList="{!v.excludeMeshNames}" displayContextDetails="{!v.displayQuoteLineDetails}"
                            displaySidebar="{!v.showSidebar}" size="Medium" allowSelection="true"
                            brandImageURL="{!v.brandImageURL}" recordId="{!v.selectedQuoteLineId}">
                            ... 
                            </RDraw:AdvancedRenderer>
  </aura:component>
```

Controller

```
[{
	handleGetCameraPositionButtonClicked: function (component, event, helper) {
        let renderer = component.find('renderer');
        renderer.getCameraPositionandTarget();
    },
    handleGetCameraPositionsandTarget: function (component, event, helper) {
        alert(JSON.stringify(event.getParam('data'), null, 2))
    },
}]
```
