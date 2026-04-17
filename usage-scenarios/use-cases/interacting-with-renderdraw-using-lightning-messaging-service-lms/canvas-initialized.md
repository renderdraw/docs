# Canvas Initialized

**Overview:**\
This channel is used to signal the initialization of the canvas. It's relevant for setting up the rendering context and scene settings at the start.

**Usage:**\
Triggered during the setup phase of the canvas to ensure proper configuration and initialization of the rendering context.

**Parameters:**

* **renderContextId**: The render context ID.
* **sceneSettings**: An object representing the scene settings.

**Channel Name (for import):**

```javascript
import CANVAS_INITIALIZED_CHANNEL from "@salesforce/messageChannel/RDraw__Canvas_Initialized__c";
```

**Publisher Components:**

* canvas3D
* canvas2D

**Subscriber Components:**

* standalone\_DataTable
