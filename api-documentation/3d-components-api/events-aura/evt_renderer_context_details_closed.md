# EVT\_Renderer\_Context\_Details\_Closed

### RDraw:EVT\_Renderer\_Context\_Details\_Closed

#### Usage Notes

This event is raised when the Context Details Back button is pressed.&#x20;

#### Parameters

There are no parameters for this event, it is only to notify when the Context Pane is going to reappear for re-fetching of data or updating the 3D scene.

### Example Usage

Component

```
  <aura:component implements="lightning:availableForFlowScreens,flexipage:availableForAllPageTypes,force:hasRecordId">
  <aura:handler name="contextDetailsClosed" event="RDraw:EVT_Renderer_Context_Details_Closed"
        action="{!c.handleContextDetailsClosed}" />
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
    handleContextDetailsClosed: function (component, event, helper) {
        component.set('v.displayQuoteLineDetails', false);
        component.set('v.selectedLineItem', null);
    },
}]
```
