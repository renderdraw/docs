---
description: Powerful,  Salesforce Native, event-driven 3D Canvas
---

# 3D Interaction Canvas (LWC)

The 3D Interaction Canvas is a custom Lightning Web Component that allows users to interact with 3D models within Salesforce. It provides a high-quality visualization environment and can be used in both Salesforce flows and record pages.

<figure><img src="../../../.gitbook/assets/image (39).png" alt=""><figcaption></figcaption></figure>

<details>

<summary>Action Menu</summary>

The 3D Interaction Canvas includes an action menu that provides several options for users to interact with the 3D models and the environment.

Here's an overview of each option:

* **Reset Camera**: This option allows the user to reset the camera view to its original state.
* **Show Explosion Handle**: When selected, a slider appears that allows the user to "explode" the 3D model, separating its components in space to view them individually.
* **Slice**: Enables the user to "slice" through the 3D model along the X or Y axis. This is useful for examining the interior of complex models.
* **Take Snapshot**: This option allows the user to take a snapshot of the current view of the 3D model. The snapshot is saved as a .png image.
* **Auto Rotate**: When selected, the 3D model slowly rotates around a central axis, giving the user a 360-degree view of the model.
* **Environment Color**: Allows the user to change the background color of the environment in which the 3D model is displayed.
* **Outline**: This option gives all components of the 3D model an outline, making it easier to distinguish individual parts.
* **Shine**: Adds a "shine" effect to the 3D model, making it appear glossy.
* **Technical Drawing**: Enables a "technical drawing" mode, which renders the model with a simplified schematic appearance.
* **Show All Labels**: If the model has labels, this option will display all of them.
* **Show Label Editor**: If all labels are being shown, this option will enable the user to edit these labels.

**Developer Options**

The following options are available when you press the Alt key. Releasing the Alt key will hide the options again. These are meant to be used during implementation or to debug an issue.

* **Show Debugger**: If developer options are enabled, this option will open a debugger. (only enabled when&#x20;
* **Log 3D Node Structure**: Logs the 3D node structure of the model to the console for debugging purposes.
* **Get Camera Position**: Logs the camera's current position to the console for debugging purposes.

</details>

<details>

<summary>Interactions</summary>

**Click Events**

We automatically highlight the selected component in the 3D scene, we then raise an event for component (`componentselected`) and also raise a lightning

On selection, we will attempt to lookup related records based on the Child\_Node\_Related\_Object Child\_Node\_Lookup\_Field. These should at least be a partial match for a selected component’s name. If found, we raise a `rendererrelatedrecordfetched` event with a property of `foundRecord`, if the record was found. If the record was found, we pass the selected record & it’s Standard Fieldset along for you to handle. If `displayActionInformationPaneOnSelection` is set to true, we automatically expand that slot, exposing whatever components are passed in, with the expectation that a handler will set the context to the selected record.\
![](<../../../.gitbook/assets/image (36).png>)

To clear the selection, simply press the clear selection button or click on any empty space in the scene to refocus on the entire model and remove highlighting.

**Hover Events**

When a component is hovered, We'll raise `componenthovered` with the name, as well as the position of the hover. If `showComponentInformationOnHover` is set to true, we'll attempt to lookup the appropriate record based on the name of the component selected. With this option selected, we'll show the `Name` field of the related record.

![](<../../../.gitbook/assets/image (51).png>)

If you choose to use the `showRelatedRecordDetailsOnHover` we will show the related record Id for the found record inline in a popover component.&#x20;

![](<../../../.gitbook/assets/image (33).png>)

**Metadata lookup**

Linkage for both hover and click actions are available on the Custom Metadata RenderDraw relationship record for the object you are looking into

![](<../../../.gitbook/assets/image (45).png>)\




</details>

<details>

<summary>Slots</summary>

![](<../../../.gitbook/assets/image (49).png>)



The component contains multiple slots, conditionally rendered sections, and nested components.

**Slots**

The `Canvas3D` component exposes the following slots:

1.  `contextDetailContent` slot: It allows you to pass custom content to be displayed in the 'context detail' area. You can pass any HTML or LWC component to this slot as per your requirement.

    Example:

    ```php-template
    phpCopy code<c-canvas3d>
        <div slot="contextDetailContent">Your custom content here</div>
    </c-canvas3d>
    ```
2.  `contextContent` slot: Similar to `contextDetailContent` slot, this slot is designed to pass the content that should be displayed in the 'context' area.

    Example:

    ```php-template
    phpCopy code<c-canvas3d>
        <div slot="contextContent">Your custom content here</div>
    </c-canvas3d>
    ```
3.  `actionInformationPane` slot: This slot is used to pass information regarding various actions. You can place an HTML or a LWC component inside this slot as per your requirement.

    Example:

    ```php-template
    phpCopy code<c-canvas3d>
        <div slot="actionInformationPane">Your custom content here</div>
    </c-canvas3d>
    ```
4.  `sidebarContent` slot: If you need to pass custom content to be displayed in the sidebar, this slot is for you.

    Example:

    ```php-template
    phpCopy code<c-canvas3d>
        <div slot="sidebarContent">Your custom content here</div>
    </c-canvas3d>
    ```

**Showing/Hiding Slots**

To control the visibility of the slots, there are boolean properties:

1. `displaySidebar` - controls the visibility of `sidebarContent` slot.
2. `displayContext` - controls the visibility of `contextContent` slot.
3. `displayContextDetails` - controls the visibility of `contextDetailContent` slot.
4. `displayActionInformationPane` - controls the visibility of `actionInformationPane` slot.

You can toggle these properties to control the visibility of the respective slots.

**Passing Information**

Information can be passed into these slots using attributes/properties and events.

Attributes/Properties:

* `size`, `contextSize`, `sidebarSize` - control the size of the overall layout and individual sections.
* `contextDetailHeaderText` - sets the text of the context detail header.

Events:

* `handleCloseContextDetails` - handles the action when the context details are closed.

</details>

<details>

<summary>Properties</summary>

{% code fullWidth="true" %}
```javascript

@api allowSelection = false; // Allow the selection of subcomponents either by ComponentTouch(Click) or programmatically using the selectComponent method
@api salesforceContent // The Salesforce Content Document Id of the 3D model to be rendered
@api brandImageURL //The branded logo image displayed in the bottom right corner of the rendering components. Pass an empty string if no branding is desired.
@api spitShine // Whether or not to display the spit shine effect on the 3D model
@api cachedHierarchy = {}; // The 3D nodes of the scene, cached after
@api childComponentPrefixToFilter = []; // A list of strings to ignore if they follow the name value, e.g. a value of ['_ASM'] passed along with the 'name' parameter of IceCream would successfully return a 3D node named 'IceCream_ASM'
@api childComponentSuffixToFilter = []; // A list of strings to ignore if they precede the name value, e.g. a value of ['ASD_'] passed along with the 'name' parameter of IceCream would successfully return a 3D node named 'ASD_IceCream'
@api contextDetailHeaderText = "Details"; // The header text that is displayed next to the back button on the contextDetail facet. This describes the content that is passed via contextDetailsContent, typically the name of a line item or detail item within a list presented in the contextContent
@api contextSize = 4; // The size in units, up to 12, for how wide the Context and Context Details slots are
@api displayActionInformationPane = false; // Whether or not to display the Action information pane slot (top slot) and components passed into actionInformationPane parameter
@api displayActionInformationPaneOnSelection = false; // Whether or not to display the Action information pane slot (top slot) when a selection is made via ComponentTouch or programmatically
@api displayContext // Whether or not to display the context slot (left side slot) and components passed into contextContent parameter
@api displayContextDetails // Whether or not to display the context slot details and components passed into contextDetailContent parameter. Use this for displaying detail components related to contextContent, e.g. Line item details for for an order item listed in contextContent. This cannot be used at the same time as displayContext
@api displaySidebar = false; // Whether or not to display the sidebar slot (right side slot) and components passed into sidebarContent parameter
@api loadingImage = ""; // The image URL to display while the 3D model is loading
@api nodeIgnoreList // A list of strings that contain names of nodes to ignore when traversing the 3D structure during ComponentTouch or Finding a component by name
@api useDigitalExperience = false; // Whether or not to use the Digital Experience URL for the renderer
@api overrideURL// The absolute URL to render.
@api sceneSettings // The Scene Settings loaded from the record
@api selectedComponentName = ""; // The node name of the selected component in the 3D model
@api sidebarSize = 4; // The size in units, up to 12, for how wide the Context and Context Details slots are
@api size = "Large"; // Size of the component, either Stretch, Small, Medium, Large, Jumbo
@api showComponentInformationOnHover = false; // shows the popover with the component information on hover if there is a related record based on lookup field under child object in medatada
@api showRelatedRecordDetailsOnHover = false; // show a record detail page instead of the name alone
@api finishedLoading //Whether the scene has initialized and loaded it's assets
@api environmentColor //the hex color to use for the environment
@api outlineComponents // outline the components in a scene
@api enableTechnicalDrawingMode // show in simplistic black and white line drawing
@api playground // Setup a renderer without loading a model for custom interactions
@api recordId // the contextual Salesforce Record to load a 3D scene/model from.
@api showMedia // Show a media element in place of the 3D scene
@api autoRotate // Slowly spin the 3D model around it's central axis	



```
{% endcode %}

</details>

<details>

<summary>Methods</summary>

```dart
add2DImage(id, imageURL, width, height, positionX, positionY, positionZ) // Add a floating image in 3D space
add2DText(id, text, size, color, componentName, showOnlyOnHover) // Add floating 2D text that can be attached to a 3D component/node in the scene
add3DTextToScene(id, text, font, anchor, letterHeight, letterThickness, color, secondaryColor, positionX, positionY, positionZ) // Add 3D text to a given Scene
addComponentTransformHandles(
	componentName,
	enableSizeHandles,
	enableRotationHandles,
	enablePositionHandles,
	usePointerToAttachHandles,
	clearHandlesOnEmptyPointerEvent
) // Used to add position, rotation and size handles to a set of components by name.
addComponentTransformHandlesToMultipleComponents(
	componentNames,
	componentIds,
	componentUniqueIds,
	enableSizeHandles,
	enableRotationHandles,
	enablePositionHandles,
	usePointerToAttachHandles,
	clearHandlesOnEmptyPointerEvent
) // Used to add position, rotation and size handles to a set of components by name.
addCubeShapeToScene(name, id, height, width, depth, color, label, positionX, positionY, positionZ) // Add a 3D Cube/Prism model to the scene."></aura:method
addLight(name, lightType, positionX, positionY, positionZ, lightIntensity, diffuseColor, specularColor, directionX, directionY, directionZ) // Add a new light to the scene
addModelToScene(
	nodeName,
	URL,
	fileName,
	positionX,
	positionY,
	positionZ,
	rotationX,
	rotationY,
	rotationZ,
	scaleX,
	scaleY,
	scaleZ,
	transaction
) // Add an additional model to the scene.
addPhotoDome(name, photoURL, size, limitCamera, x, y, z, infiniteDistance)  // Add 360° photo as a sphere where models can be rendered
addVideoPlayer(id, videoURL, width, height, positionX, positionY, positionZ, placeholderImageURL) // Add a floating video Player in 3D space
addWidget(name, type, positionX, positionY, positionZ, reotationX, rotationY, rotationZ, scaleX, scaleY, scaleZ) // Still in our 'labs' status. Adds a widget to our scene.
aimAndPositionCamera(positionx, positiony, positionz, positionalpha, positionbeta, aimx, aimy, aimz, nodeName) // Position the camera in 3D space and aim at a subject.
aimCamera(x, y, z, nodeName)  // Aim the camera in 3D space either at a component or some coordinates.
autoLabelComponents()  // Automatically add labels to components
clearAllHighlights()  // Clear all highlights from the Scene.
clearSelections()  // Clear all selections from the Scene.
displayMedia(imageUrl, allowClose) // Display related media instead of the 3D drawing
findNode(name, prefixesToIgnore, suffixesToIgnore) // Returns an object containing the Node information from the 3D scene. If no node is found, ths returns nothing
getCameraPositionandTarget() // Fetch the camera's current position and where it is aiming.
getFixedComponentName(name)// Retrieves fixed component name based on prefix and suffixes
getHierarchy() // Fetch the 3D model's hierarchy. Must subscribe to RDraw:EVT_Renderer_Get_Hierarchy for response/
getListOfComponentNames() // Fetch a flat list of all of the names of each 3D Node in the scene 
async getRenderContextForId(recordId) // Retrieves RenderContext from server for a given recordId
hide2DCanvasComponent() // Show the 2D Canvas component
hideActionInformationPane()// Hide the Action information pane
hideAllLabels() // Hide all labels added to the 3D Scene
hideAllNodes() // Hide all nodes in a 3D Scene
hideContextContent() // Hide the context content pane
hideContextDetailContent()// Hide the context detail content (details beneath the context content), displays the ContextContent instead 
hideLabelManager() // Hide label manager to apply styles to labels added to the 3D Scene
hideMedia() // Hide displayed related media that is presented in the content area of this component
hideMultipleNodes(componentNames, componentIds)  // Hide several components in the scene
hideNode(componentName)  // Hide a node in a 3D Scene
hideSidebar()  // Hide the sidebar
highlightComponent(nodeId, name, enabled, color, zoomAndFocusOnElement)  // Find a component by name or Id and highlight it with the color provided
highlightMultipleComponents(componentNames, componentIds, color)  // // Highlight several components in the scene
is3DSceneDisplayed() // Check if a 3D scene is displayed in the Main Content of this component
isMediaDisplayed() // Check if media is displayed instead of a 3D scene in the Main Content of this component
isolateComponent(componentName)  // Isolate the individual component by hiding all other components in the scene
isolateGroup(
	componentNames,
	componentIds,
	componentUniqueIds,
	enableSizeHandles,
	enableRotationHandles,
	enablePositionHandles,
	usePointerToAttachHandles,
	clearHandlesOnEmptyPointerEvent
)// Isolate a group of components by hiding all other components in the scene
isolateMultipleComponents(componentNames, componentIds, componentUniqueIds)  // Isolate the several components by hiding other components in the scene
loadAndApplyTextureMaterialToModel(textureImageURL, nodeUniqueId, materialName)  // Load a diffuse texture and add it to a model.
pause(seconds = 1)  // Pause before comitting another action
positionCamera(x, y, z, alpha, beta) // Position the camera in 3D space.
raiseInteractionEvent(name, type, label, value, metadata) // Used to call actions that were setup within the 'interactions' section of the Scene setup
reintegrateAllComponents()  // Re-integrate all components that have been isolated.
reintegrateComponent(componentName)  // Re-integrate a component that has been isolated.
reloadToInitialScene() // Reload to the initial scene (post initial model load)
removeComponent(uniqueId, name) // Removes the given component from a scene
removeComponentHandles() // Used to remove position, rotation and size handles to a set of components by name.
resetCamera() // Reset the camera to it's initial position in the scene
selectComponent(name, id, uniqueId, context, ignoreList) // Programmatically select a component node within the 3D model. Raises event on successful selection
setLabelStyling(lineThickness, fontSize, color, bold, align, hideable, draggable) // Hide label manager to apply styles to labels added to the 3D Scene
setLayoutContent(layoutElement, componentType, content) // Set the content of a layout element, either Context, ActionInformationPane or Sidebar. The Record Id and renderer will be passed to the component
setupGround(imageURL, heightMapURL, width, height, maxheight, minheight, subdivisions, groundY)  // Add a ground for your 3D scene, with or without a heightmap
show2DCanvasComponent()  // Show the 2D Canvas component
showActionInformationPane() // Show the action information pane
showAllLabels()  // Show all labels added to the 3D Scene
showAllNodes()  // Show all nodes that have been hidden in a 3D Scene
showContextContent()// Show the context content pane
showContextDetailContent()  // Hide the context detail content (details beneath the context content)
showLabelManager(admin)  // Show label manager to apply styles to labels added to the 3D Scene
showNode(componentName) // Show a node that has been hidden in a 3D Scene
showSidebar() // Show the sidebar
showToastNotification(title, mode, message, messageTemplate, iconName, type, duration, messageTemplateData) // Displays a toast notification to the user
takeSnapshot(download)  // Take a snapshot of the scene
toggleEnableComponent(name, id, uniqueId, isEnabled)  // Enable or disable a given 3D node by passing a uniqueId, name or id
toggleEnableGroup(name)  // Enable or disable a given group by passing a name
transformComponent(name, id, uniqueId, positionX, positionY, positionZ, rotateX, rotateY, rotateZ, scaleX, scaleY, scaleZ) // Position, rotate or scale a given component
updateBackgroundImage(imageURL) // Update background to a image
updateComponentColor(name, id, uniqueId, colorHex) // Update a given 3D component node to the passed hex color code.
updateEnvironmentLightTexture(includedTextureName)  // Change the lighting texture to use (for refraction)
updateExistingLabel(labelId, labelText) // Update an existing Label
updateLight(name, enable, intensity, diffuseColor, specularColor) // Add a new light to the scene
updateMaterial(materialName, color) // Update a material within the scene.
verifyComponent(componentName, componentId, componentUniqueId) // Verify a component exists in the scene, is enabled and visible.	

```

</details>

<details>

<summary>Events</summary>

`contextdetailsclose`: Dispatched when the context details pane is closed.

`hidemedia`: Dispatched when the media display is hidden.

`explosionamountchanged`: Dispatched when the explosion amount changes.

`toggleslicing`: Dispatched when slicing is toggled.

`clipXChanged`: Dispatched when the slice value for the X-axis changes.

`clipYChanged`: Dispatched when the slice value for the Y-axis changes.

`environmentcolorchanged`: Dispatched when the environment color changes.

`clearselection`: Dispatched when the selected components are cleared.

`popovermouseover`: Dispatched when the mouse hovers over a popover.

`popovermouseout`: Dispatched when the mouse moves out of a popover.

`screenshottaken`: Dispatched when a screenshot is taken.

* `data`: The base64 string of the taken screenshot.

`finishedloading`: Dispatched when the rendering has finished loading.

`hierarchyfetched`: Dispatched when the component hierarchy has been fetched from the 3D renderer.

* `data`: The structure of the component hierarchy.

`getcamerapostionandtarget`: Dispatched when the camera position and target are updated.

* `data`: The object containing updated camera position and target.

`elementadded`: Dispatched when a new element is added to the scene.

* `elementType`: The type of the added element.
* `name`: The name of the added element.
* `uniqueId`: The unique ID of the added element.

`componenttransformed`: Dispatched when a component has been transformed.

* `name`: The name of the transformed component.
* `id`: The ID of the transformed component.
* `uniqueId`: The unique ID of the transformed component.
* `type`: The type of the transformed component.
* `data`: The data of the transformed component.

`componentverified`: Dispatched when a component has been verified.

* `name`: The name of the verified component.
* `isLoaded`: The loaded status of the verified component.
* `isVisible`: The visibility status of the verified component.
* `isFullyVisible`: The full visibility status of the verified component.
* `visibility`: The visibility level of the verified component.
* `isEnabled`: The enabled status of the verified component.

`labelstylingclosed`: Dispatched when the label styling dialog is closed.

`labelstylingupdated`: Dispatched when the label settings have been saved.

* `lineColor`: The color of the line for the label.
* `labelBold`: The boldness of the label.
* `fontSize`: The font size of the label.
* `lineThickness`: The thickness of the line for the label.
* `align`: The alignment of the label.
* `hideable`: The hideability of the label.
* `draggable`: The draggable status of the label.

`componenthovered`: Dispatched when a component is hovered.

* `data`: The data of the hovered component.

`componenthoverreleased`: Dispatched when a hover is released from a component.

* `data`: The data of the released hover component.

`camerachanged`: Dispatched when the camera has been moved or rotated.

* `positionX`: The x-position of the camera.
* `positionY`: The y-position of the camera.
* `positionZ`: The z-position of the camera.
* `alpha`: The rotation of the camera around the y-axis.
* `beta`: The rotation of the camera around the x-axis.
* `radius`: The distance of the camera from the target.

</details>

<details>

<summary>Developing with 3D Interaction Canvas</summary>

**Add the Component to the HTML**: In the HTML file of the parent component, include the Canvas3D component and pass any necessary attributes or public properties:

```html
htmlCopy code<template>
    <!-- Some code... -->
    <RDraw-canvas-3-d 
        record-id={recordId}
        size={size}
        salesforce-content={salesforceContent}
        use-digital-experience={useDigitalExperience}
        allow-selection={allowSelection}
    ></RDraw-canvas-3-d>
    <!-- Some code... -->
</template>
```

In the above code, `{recordId}`, `{size}`, `{salesforceContent}`, `{useDigitalExperience}`, and `{allowSelection}` You'll need to define the properties in your parent component's JavaScript file.

**Wait for the `finishedloading` event before attempting to interact or call methods on the 3D Canvas**

**Listen to Events**: If your parent component needs to react to events emitted by the Canvas3D component, you can add event listeners:

```html
<template>
    <!-- Some code... -->
    <RDraw-canvas-3-d 
        record-id={recordId}
        size={size}
        use-digital-experience={useDigitalExperience}
        allow-selection={allowSelection}
        onfinishedloading={handleFinishedLoading}
    ></RDraw-canvas-3-d>
    <!-- Some code... -->
</template>
```

In your parent component's JavaScript file, handle the event:

```javascript
handleFinishedLoading(event) {
    // Handle the event
}
```

\


</details>

<details>

<summary>End-User Usage</summary>

The 3D Interaction Canvas component can be added to a Flow or a Record Page in your Salesforce organization. It offers several customizable properties to configure its behavior and interaction with data.

#### As a Flow Screen Component

When using this component in a Flow, you have the following input properties available:

* `recordId`: This property accepts a `String` that corresponds to the Salesforce record Id you want to interact with.
* `size`: This property accepts a `String` that sets the size of the component. It could be Small, Medium or Large.
* `salesforceContent`: This property accepts a `String` that corresponds to the Salesforce Content Id for the 3D model to be displayed.
* `useDigitalExperience`: This property is a `Boolean`. If it's set to true, the component will be configured to be used in Salesforce's Digital Experience (previously known as Community).
* `allowSelection`: This property is a `Boolean`. If it's set to true, users will be allowed to select individual components of the 3D model.

To use the 3D Interaction Canvas in a Flow, add a new Screen, then add a custom component to the Screen. From the list of available components, choose the 3D Interaction Canvas.

#### As a Record Page Component

When using this component on a Record Page, you have the following properties available:

* `recordId`: This property is automatically filled by Salesforce with the Id of the current record.
* `size`: This property accepts a `String` that sets the size of the component. It could be Small, Medium or Large.

To use the 3D Interaction Canvas on a Record Page, simply edit your Lightning Page, drag the 3D Interaction Canvas component from the Custom - Managed section of the Lightning Components list and drop it in the desired place on your Lightning Page. Click on the component to see the property options available.

### Supported Form Factors

The 3D Interaction Canvas supports both `Small` and `Large` form factors, making it adaptable for usage on various devices and screen sizes.

</details>
