# EVT\_Renderer\_Screenshot\_Taken

### RDraw:EVT\_Renderer\_Screenshot\_Taken

#### Usage Notes

This event is raised when a screenshot is taken, typically from the action menu. This can be used to save the image of the 3D scene to Salesforce, or to download the image for further usage.&#x20;

#### Parameters

| **NAME** | **TYPE** | **DESCRIPTION**          |
| -------- | -------- | ------------------------ |
| data     | string   | A base64 encoded string  |

#### Source Component

* SimpleRenderer

#### Handler Component

* None in main package — consumed by external implementing components.

#### Event Name (for handler)

```xml
<aura:handler event="RDraw:EVT_Renderer_Screenshot_Taken" action="{!c.handleScreenshotTaken}" />
```
