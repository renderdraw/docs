---
description: API for interacting with the canvas2D component
---

# 2D Interaction Canvas

\
The Canvas 2D Lightning Web Component (LWC) offers a dynamic and interactive way to engage with Salesforce data, bypassing the traditional table or form-based data interaction. Seamlessly integrated into Lightning flows, App Screens, or Record Pages, this component transforms data visualization and interaction into an intuitive canvas-based experience.

<figure><img src="../../.gitbook/assets/image (28).png" alt=""><figcaption></figcaption></figure>

**Key Features:**

1. **Interactive Elements**: Users can utilize a range of pre-defined templates, including clickable shapes and images, droppable areas, sticky notes, draggable items, layout areas, and layout walls. These elements can be related to Salesforce records for more contextual interactions.
2. **Data Connectivity**: The DataSource elements enable administrators to define Salesforce queries that auto-execute upon scene loading. This feature allows for conditional customization of the canvas elements based on real-time data.
3. **Flow-Based Interactions**: The component supports multiple interactions like hovering and selection, which can trigger flow-based actions.
4. **APEX Output**: The canvas interactions can be captured and processed through an APEX class, which can then be utilized in custom components or flows.
5. **Mobile-Friendly**: Designed with mobility in mind, the component is particularly tablet-friendly.
6. **Additional User Actions**: An optional menu provides users with extra capabilities like setting zoom levels, re-centering the canvas, adding layout elements, and saving or proceeding further.

**Ideal Use Cases**:

* **Floor Planning**: Generate quotations by adding and spatially positioning products within a scene.
* **2D Configuration**: Customization through drag-and-drop or click-based interactions.
* **Part Diagrams**: Create clickable exploded diagrams for easy spare part ordering or detailed views.

This Canvas 2D LWC provides a powerful toolset for creating immersive and interactive data experiences within Salesforce.

### Attributes

| Name             | Description                                                                                                                                        |
| ---------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| canvasresults    | The resulting RDraw:CanvasScene Apex class after user interaction                                                                                  |
| canvassource     | The Input RDraw:CanvasScene Apex class to load prior to user interaction                                                                           |
| model            | JSON object that represents the scene and the templates/placed items on the scene. Pass this in if you want to manually compose a scene using code |
| recordId         | Salesforce recordId to fetch the Scene settings from                                                                                               |
| renderContextId  | The context id (unique Identifier) for the given canvas instance                                                                                   |
| resultAreas      | deprecated                                                                                                                                         |
| resultItems      | deprecated                                                                                                                                         |
| screenshot       | Image Data captured from canvas stored as base 64 encoded image                                                                                    |
| serializedResult | Serialized Scene Settings for manually saving after processing                                                                                     |
| serializedSource | Serialized Scene Settings for manually loading a scene via serialized JSON                                                                         |

### Methods

| Method                                   | Description                                                                                               |
| ---------------------------------------- | --------------------------------------------------------------------------------------------------------- |
| addArrow(arrowParam)                     | Adds an arrow shape to the canvas.                                                                        |
| addCircle(circleParam)                   | Adds a circle shape to the canvas.                                                                        |
| addClickableImage(imageParam)            | Adds a clickable image to the canvas.                                                                     |
| addDraggableItem(itemParam)              | Adds a new draggable item to the canvas.                                                                  |
| addDroppableArea(areaParam)              | Adds a droppable area to the canvas.                                                                      |
| addDropZone(zoneParams)                  | Adds a new drop zone with specified parameters.                                                           |
| addSquare(squareParam)                   | Adds a square shape to the canvas.                                                                        |
| addTransformHandles(param)               | Adds transform handles to a specified element for resizing and rotation.                                  |
| addTransformHandlesToArea(prop)          | Adds transform handles to a specific area for resizing and rotation.                                      |
| createArea(areaParam)                    | Creates a new area with specified parameters.                                                             |
| createWall(wallParam)                    | Creates a new wall with specified parameters.                                                             |
| displaySourceDataTemplate()              | Displays the template of source data connected to the canvas as a popup for the user to modify the query. |
| executeDataSource(dataSource)            | Executes the specified data source to fetch data into the canvas.                                         |
| flashElement(flashParam)                 | Flashes a specified element for visual emphasis.                                                          |
| getCurrentScale()                        | Fetches the current scale level of the canvas.                                                            |
| getItemsOnCanvas()                       | Retrieves all items currently present on the canvas.                                                      |
| removeArea(areaId)                       | Removes a specified area based on its ID.                                                                 |
| removeElement(param)                     | Removes a specified element from the canvas.                                                              |
| removeTransformHandles()                 | Removes all transform handles from the canvas.                                                            |
| removeTransformHandlesForArea()          | Removes transform handles for a specific area on the canvas.                                              |
| resetEnvironment()                       | Resets the canvas environment to its initial state.                                                       |
| setScale(scale)                          | Sets the scale level of the canvas.                                                                       |
| setupBackgroundColor(colorParam)         | Sets the background color of the canvas.                                                                  |
| setupBackgroundImage(imageParam)         | Sets the background image of the canvas.                                                                  |
| startDrawingAreas()                      | Initiates the drawing of areas on the canvas.                                                             |
| startDrawingWalls()                      | Initiates the drawing of walls on the canvas.                                                             |
| stopDrawingAreas()                       | Stops the drawing of areas on the canvas.                                                                 |
| stopDrawingWalls()                       | Stops the drawing of walls on the canvas.                                                                 |
| takeSnapShot(downloadSnapshot, callback) | Takes a snapshot of the canvas, with options to download and callback functions.                          |
| updateArea(areaParam)                    | Updates an existing area with new parameters.                                                             |
| updateCircle(circleParam)                | Updates the parameters of an existing circle.                                                             |
| updateClickableImage(imageParam)         | Updates the parameters of an existing clickable image.                                                    |
| updateDroppableArea(areaParam)           | Updates the parameters of an existing droppable area.                                                     |
| updateDropZone(zoneParams)               | Updates an existing drop zone with new parameters.                                                        |
| updateEnvironment()                      | Updates the environment settings of the canvas.                                                           |
| updateTemplates(templateParam)           | Updates the existing templates with new parameters.                                                       |

### Events

| Event                             | Description                                                                                                    |
| --------------------------------- | -------------------------------------------------------------------------------------------------------------- |
| addItemTemplateToDropZone         | Raised when an item has been added to a drop zone                                                              |
| areaadded                         | Raised when a layout Area has been added (via API)                                                             |
| areachanged                       | Raised when a layout Area has changed, either sizing or position                                               |
| areacreated                       | Raised when an Layout Area is created (drawn) to the canvas                                                    |
| arearemoved                       | Raised when a Layout Area has been removed from the canvas                                                     |
| areaselected                      | Raised when a Layout Area has been selected or tapped                                                          |
| canvasloaded                      | Raised when the initial canvas has loaded, this is raised before any placed items have been added to the scene |
| canvasloadedandenvironmentupdated | Raised when the environment is fully loaded                                                                    |
| draggableadd                      | Raised when a draggable item is added to the canvas                                                            |
| droppableadd                      | Raised when a droppable area has been added to the canvas                                                      |
| dropzoneclicked                   | Raised when a drop zone is clicked                                                                             |
| elementclicked                    | Raised when a clickable element is clicked or tapped on the canvas                                             |
| elementremoved                    | Raised when a clickable element is clicked or tapped on the canvas                                             |
| elementtransformed                | Raised when the element is transformed, either position size or rotation                                       |
| errorloadingdatasourceresults     | Raised when there is an issue loading a DataSource Query for the Canvas                                        |
| results                           | Raised when the "Next" button is pressed, all items on the canvas are passed via parameters                    |
| scaleset                          | Raised when the scale (zoom) changes on the canvas                                                             |
| settingsfetched                   | Raised when the 2D Canvas settings are loaded from Salesforce's Servers                                        |
| stageclicked                      | Raised when the 2D Canvas is clicked directly, typically used to cancel interactions like editing or resizing  |
| stickynoteadded                   | Raised when a sticky note is added to the canvas                                                               |
| stickynotechanged                 | Raised when a sticky note is changed, e.g. position, size or text have changed                                 |
| stickynoteremoved                 | Raised when a sticky note has been removed                                                                     |
| updateitems                       | Raised when items are reordered or added to a droppable area                                                   |
| walladded                         | Raised when a Layout Wall is added to the scene                                                                |
| wallchanged                       | Raised when a Layout Wall is changed on the canvas (size, position)                                            |
| wallcreated                       | Raised when a user adds a Layout Wall to the canvas (not via API)                                              |
| wallremoved                       | Raised when a Layout wall is removed from the canvas                                                           |
| wallselected                      | Raised when a user clicks or taps on a Layout Wall in a canvas                                                 |
