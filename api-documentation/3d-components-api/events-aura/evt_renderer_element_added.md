# EVT\_Renderer\_Element\_Added

### RDraw:EVT\_Renderer\_Element\_Added

#### Usage Notes

This event is raised when an element is added to the 3D scene. Handling this event allows for the receiving of the details of that 3D node that was added, specifically what type of element, and it's uniqueId to modify or reference in a later transaction.

#### Parameters

| **NAME**    | **TYPE** | **DESCRIPTION**                                                                           |
| ----------- | -------- | ----------------------------------------------------------------------------------------- |
| elementType | string   | The type of element added to the screen, one of 3DText,  photoDome, video, 2DImage, model |
| name        | string   | The name of the component selected                                                        |
| uniqueId    | string   | The uniqueId of the component selected.                                                   |

#### Example Usage

On selection of a 3D component subnode, the `RDraw:EVT_Renderer_Select_Component` event is raised, passing the id, name and uniqueId. These can then be processed/linked to a Salesforce record or process.&#x20;

Component

```
  <aura:component implements="lightning:availableForFlowScreens,flexipage:availableForAllPageTypes,force:hasRecordId">
      <aura:handler name="elementAdded" event="RDraw:EVT_Renderer_Element_Added" action="{!c.handleElementAdded}" />
  <RDraw:AdvancedRenderer displayContext="true" aura:id="renderer"
                            nodeIgnoreList="{!v.excludeMeshNames}" displayContextDetails="{!v.displayQuoteLineDetails}"
                            displaySidebar="{!v.showSidebar}" size="Medium" allowSelection="true"
                            brandImageURL="{!v.brandImageURL}" recordId="{!v.selectedQuoteLineId}">
                            ... 
                            </RDraw:AdvancedRenderer>
  </aura:component>
```

> Add 3D text, 2D text, a photodome, a 2D Image or a Video to the scene to raise the event

Controller

```
[{
  handleElementAdded: function (component, event, helper) {
        let shouldToast = component.get('v.displayToastOnElementAdded');
        if (shouldToast) {
            let elementType = event.getParam('elementType')
            let name = event.getParam('name')
            let uniqueId = event.getParam('uniqueId')
            var toastEvent = $A.get("e.force:showToast");
            toastEvent.setParams({
                message: 'A ' + elementType + ' was added to the scene, uniqueId=' + uniqueId,
            })
            toastEvent.fire();
        }
    },
}]
```
