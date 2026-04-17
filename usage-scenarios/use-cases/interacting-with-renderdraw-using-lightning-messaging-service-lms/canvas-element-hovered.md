# Canvas Element Hovered

**Overview:**\
Fires when the user hovers over an element in either a 2D or 3D canvas.

**Usage:**\
Utilized to trigger actions or display information related to the hovered element in either a 2D or 3D canvas context.

**Parameters:**

* **contextId**: The ID for the context of the 2D or 3D canvas.
* **elementId**: The ID of the hovered element.
* **elementType**: The type of the hovered element, indicating the shape or canvas element type in 2D (e.g., layoutArea), or component in 3D.
* **elementName**: The name of the hovered element.
* **record**: The associated record of the hovered element, where applicable.

**Channel Name (for import):**

```javascript
import CANVAS_ELEMENT_HOVERED_CHANNEL from "@salesforce/messageChannel/RDraw__Canvas_ElementHovered__c";
```

**Publisher Components:**

* canvas3D
* canvas2D

**Subscriber Components:**

* standalone\_DataTable

\
