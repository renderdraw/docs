# EVT\_Renderer\_Get\_Hierarchy

### RDraw:EVT\_Renderer\_Get\_Hierarchy

#### Usage Notes

This event is raised when the **getHierarchy**  method is called on the AdvancedRenderer component. A parameter is passed back (data) that represents the 3D structure of the Scene being rendered.&#x20;

#### Parameters

| **NAME** | **TYPE** | **REQUIRED** | **DESCRIPTION**                                       |
| -------- | -------- | ------------ | ----------------------------------------------------- |
| data     | object   |              | The JSON hierarchical representation of the 3D scene  |

#### Example Usage

Component

```
<aura:component implements="lightning:availableForFlowScreens,flexipage:availableForAllPageTypes,force:hasRecordId"
   access="public">
    <aura:handler name="componentSelected" event="RDraw:EVT_Renderer_Mesh_Selected"
        action="{!c.handleComponentSelected}" />
    <aura:handler name="selectionCleared" event="RDraw:EVT_Renderer_Mesh_Selection_Cleared"
        action="{!c.handleSelectionCleared}" />
    <aura:handler name="getCameraPostionandTarget" event="RDraw:EVT_Renderer_Get_CameraPositionandTarget"
        action="{!c.handleGetCameraPositionsandTarget}" />
    <aura:handler name="hierarchyFetched" event="RDraw:EVT_Renderer_Get_Hierarchy" action="{!c.handleGetHierarchy}" />

<RDraw:AdvancedRenderer aura:id="renderer" displayContext="true" spitShine="true"
    allowSelection="true" recordId="{!v.recordId}" size="Medium">
   <aura:set attribute="contextContent">
       <lightning:card title="Get Hierarchy">
          <p class="slds-p-horizontal_small">
              <!-- button for image replacement -->
              <lightning:button title="Get Hierarchy"
                  onclick="{!c.handleTestGetHierarchy}">Get Hierarchy
              </lightning:button>
          </p>
      </lightning:card>
   </aura:set>
</aura:component>
```

Controller

```
({
    handleTestGetHierarchy: function (component, event, helper) {
        let renderer = component.find('renderer');
        renderer.getHierarchy();
    },
    handleGetHierarchy: function (component, event, helper) {
        alert(JSON.stringify(event.getParam('data'), null, 2))
    },
    
    handleGetCameraPositionsandTarget: function (component, event, helper) {
        alert(JSON.stringify(event.getParam('data'), null, 2))
    },
     handleComponentSelected: function (component, event, helper) {
        alert('Selected name = ' + event.getParams().name);
        //todo do something with the selected component data like fetch salesforce data 
    },
    
})
```
