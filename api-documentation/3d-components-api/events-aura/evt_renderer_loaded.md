# EVT\_Renderer\_Loaded

### RDraw:EVT\_Renderer\_Loaded

#### Usage Notes

This event is raised when the renderer has created a scene and fully loaded a 3D drawing into that scene.&#x20;

#### Parameters

There are no parameters for this event, it is only to notify the consuming component when a scene is displayed

#### Example Usage

Component

```
  <aura:component implements="lightning:availableForFlowScreens,flexipage:availableForAllPageTypes,force:hasRecordId">
  <aura:handler name="rendererLoaded" event="RDraw:EVT_Renderer_Loaded" action="{!c.handleRendererLoaded}" />
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
 	handleRendererLoaded: function (component, event, helper) {
       	//display options for configuration or add items to the scene based off it loading
    },
}]
```

.
