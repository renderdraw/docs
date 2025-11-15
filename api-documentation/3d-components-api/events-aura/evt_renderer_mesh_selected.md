# EVT\_Renderer\_Mesh\_Selected

### RDraw:EVT\_Renderer\_Mesh\_Selected

#### Usage Notes

This event is raised when a subcomponent of a 3D drawing is selected using ComponentTouch. Handling this event allows for the receiving  of the details of that 3D node. These details can be used to apply 3D effects to the scene, or by looking up related data within the Salesforce platform.

#### Parameters

| **NAME** | **TYPE** | **REQUIRED** | **DESCRIPTION**                                                    |
| -------- | -------- | ------------ | ------------------------------------------------------------------ |
| context  | object   |              | Additional information provided with the selection of a component. |
| id       | string   |              | The Id of the component selected                                   |
| name     | string   |              | The name of the component selected                                 |
| uniqueId | string   |              | The uniqueId of the component selected.                            |

#### Example Usage

On selection of a 3D component subnode, the `RDraw:EVT_Renderer_Select_Component` event is raised, passing the id, name and uniqueId. These can then be processed/linked to a Salesforce record or process.&#x20;

Component

```
  <aura:component implements="lightning:availableForFlowScreens,flexipage:availableForAllPageTypes,force:hasRecordId">
  <aura:handler name="selectComponent" event="RDraw:EVT_Renderer_Select_Component"
        action="{!c.handleSelectComponent}" />
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
 handleSelectComponent: function (component, event, helper) {
        let renderer = component.find('renderer');
        let functionParams = event.getParams();
        renderer.selectComponent(functionParams.arguments.name,
            functionParams.arguments.id,
            functionParams.arguments.uniqueId, undefined,
            component.get('v.nameIgnoreList')
        );
    },
}]
```
