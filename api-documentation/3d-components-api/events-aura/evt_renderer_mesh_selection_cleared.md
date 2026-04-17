# EVT\_Renderer\_Mesh\_Selection\_Cleared

### RDraw:EVT\_Renderer\_Mesh\_Selection\_Cleared

#### Usage Notes

This event is raised when a previously-selected mesh in a 3D scene is deselected — either because the user clicked empty canvas space, or because `clearSelection()` was called on the renderer. Handling this event allows consuming components to reset detail panels, clear related-record lookups, and revert any 3D effects applied on selection.

#### Parameters

This event has no parameters. Its presence alone signals the deselection.

#### Source Component

* SimpleRenderer

#### Handler Component

* AdminVisualSceneParameters
* AdminVisualSceneSetup
* AdvancedRenderer

#### Event Name (for handler)

```xml
<aura:handler event="RDraw:EVT_Renderer_Mesh_Selection_Cleared" action="{!c.handleMeshSelectionCleared}" />
```

#### Example Usage

Component

```
  <aura:component implements="lightning:availableForFlowScreens,flexipage:availableForAllPageTypes,force:hasRecordId">
      <aura:handler name="selectionCleared" event="RDraw:EVT_Renderer_Mesh_Selection_Cleared"
            action="{!c.handleSelectionCleared}" />
      <RDraw:AdvancedRenderer displayContext="true" aura:id="renderer"
                            nodeIgnoreList="{!v.excludeMeshNames}" displayContextDetails="{!v.displayQuoteLineDetails}"
                            displaySidebar="{!v.showSidebar}" size="Medium" allowSelection="true"
                            recordId="{!v.selectedQuoteLineId}">
                            ...
                            </RDraw:AdvancedRenderer>
  </aura:component>
```

Controller

```
({
    handleSelectionCleared: function (component, event, helper) {
        // Clear any record-detail UI and reset related state
        component.set('v.selectedLineItem', null);
        component.set('v.displayQuoteLineDetails', false);
    },
})
```
