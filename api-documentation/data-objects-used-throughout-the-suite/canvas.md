---
description: >-
  Used within 2D interactions to easily pass data back and forth to the
  Salesforce system
---

# Canvas

#### Canvas has the following properties that can be utilized within a Lightning flow or to pre-populate the 2D Component with Data

<table data-view="cards"><thead><tr><th>Name</th><th>Type</th><th>Description</th></tr></thead><tbody><tr><td>id</td><td>string</td><td>the unique id for this element</td></tr><tr><td>name</td><td>string</td><td>The name of the item defined during template creation</td></tr><tr><td>backgroundImageURL</td><td>string</td><td>the background image (if applied)</td></tr><tr><td>placedClickableShapes</td><td>List&#x3C;RDraw.BaseCanvasItem></td><td>A list of clickable shapes, and their locations if added to the canvas</td></tr><tr><td>placedDroppableAreas</td><td>List&#x3C;RDraw.DroppableArea></td><td>A list of droppable areas in order from left to right top to bottom that also includes elements that were placed in the area by the order in which they were placed</td></tr><tr><td>placedDraggableItems</td><td>List&#x3C;RDraw.BaseCanvasItem></td><td>A list of all of the Draggable items placed on the Canvas that are not related to a given Droppable Area</td></tr><tr><td>placedLayoutAreas</td><td>List&#x3C;RDraw.BaseCanvasItem></td><td>A list of layout areas and their related records</td></tr><tr><td>placedLayoutWalls</td><td>List&#x3C;RDraw.LayoutWall></td><td>A list of walls with their points added to the </td></tr></tbody></table>



