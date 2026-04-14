# Source Inventory: LMS Channels & Aura Events

**Generated:** 2026-04-14
**Source:** Main RenderDraw package (`force-app/main/default/`)

## LMS Message Channels (5)

All 5 channels have `isExposed: true`.

| Channel | Master Label | Fields | Publishers | Subscribers |
|---------|-------------|--------|------------|-------------|
| Canvas_Interaction | Canvas Interaction | contextId, name, parameters | canvas3D, standalone_DataTable | canvas3D, canvas2D |
| Canvas_Initialized | Canvas Initialized | renderContextId, sceneSettings | canvas3D, canvas2D | standalone_DataTable |
| Canvas_ElementSelected | Canvas Element Selected | contextId, elementId, elementType, elementName, record | canvas3D, canvas2D | standalone_DataTable, groupSelection |
| Canvas_ElementHovered | Canvas Element Hovered | contextId, elementId, elementType, elementName, record | canvas3D, canvas2D | standalone_DataTable |
| Record_Selected | Record Selected | record, ~~sender~~ (commented out) | standalone_DataTable | canvas3D, canvas2D |

### Channel Detail

#### Canvas_Interaction
- **File:** `messageChannels/Canvas_Interaction.messageChannel-meta.xml`
- **Description:** "Channel dedicated when a " (truncated in source)
- **Fields:**
  | Field Name | Description |
  |------------|-------------|
  | contextId | The Id for the context of the 2D or 3D canvas |
  | name | The Name of the Interaction |
  | parameters | The parameters you want to pass to the Interaction |
- **Published by:** canvas3D, standalone_DataTable
- **Subscribed by:** canvas3D (bidirectional), canvas2D

#### Canvas_Initialized
- **File:** `messageChannels/Canvas_Initialized.messageChannel-meta.xml`
- **Description:** Channel for canvas initialization
- **Fields:**
  | Field Name | Description |
  |------------|-------------|
  | renderContextId | The render context Id |
  | sceneSettings | The scene settings object |
- **Published by:** canvas3D, canvas2D
- **Subscribed by:** standalone_DataTable

#### Canvas_ElementSelected
- **File:** `messageChannels/Canvas_ElementSelected.messageChannel-meta.xml`
- **Description:** Channel dedicated when a element is selected within the canvas
- **Fields:**
  | Field Name | Description |
  |------------|-------------|
  | contextId | The Id for the context of the 2D or 3D canvas |
  | elementId | The Id of the element Selected |
  | elementType | The type of the element selected, in 2D the shape or canvas element type (e.g. layoutArea). In 3D, this will likely be component. |
  | elementName | The Name of the element Selected |
  | record | The associated record of the selected element, where applicable |
- **Published by:** canvas3D, canvas2D
- **Subscribed by:** standalone_DataTable, groupSelection

#### Canvas_ElementHovered
- **File:** `messageChannels/Canvas_ElementHovered.messageChannel-meta.xml`
- **Description:** Channel dedicated when a element is hovered within the canvas
- **Fields:**
  | Field Name | Description |
  |------------|-------------|
  | contextId | The Id for the context of the 2D canvas |
  | elementId | The Id of the element Selected |
  | elementType | The type of the element hovered, in 2D the shape or canvas element type (e.g. layoutArea). |
  | elementName | The Name of the element Hovered |
  | record | The associated record of the hovered element, where applicable |
- **Published by:** canvas3D, canvas2D
- **Subscribed by:** standalone_DataTable

#### Record_Selected
- **File:** `messageChannels/Record_Selected.messageChannel-meta.xml`
- **Description:** "Channel dedicated when a " (truncated in source)
- **Fields:**
  | Field Name | Description |
  |------------|-------------|
  | record | The current data representing the record that changed |
  | ~~sender~~ | ~~The source of the message~~ (commented out in XML) |
- **Published by:** standalone_DataTable
- **Subscribed by:** canvas3D, canvas2D

### LMS Notable Observations
- All channels are `isExposed: true` — accessible outside the managed package namespace
- `canvas3D` is both publisher and subscriber on `Canvas_Interaction` (bidirectional communication)
- `Record_Selected` has a commented-out `sender` field
- 2 channel descriptions are truncated in source XML
- No Aura component references found — all LMS usage is in LWC components

---

## Aura Events (56)

All 56 events are type `APPLICATION` (zero COMPONENT-type events). 14 events have `access="global"`.

### Summary by Category

| Category | Count | access=global | Likely Public | Likely Internal |
|----------|-------|---------------|---------------|-----------------|
| Renderer | 19 | 14 | 19 | 0 |
| Settings | 23 | 0 | 0 | 23 |
| Admin | 8 | 0 | 8 | 0 |
| Layout | 2 | 0 | 2 | 0 |
| Scene | 1 | 0 | 1 | 0 |
| Interaction | 1 | 0 | 1 | 0 |
| Other | 2 | 0 | 2 | 0 |
| **Total** | **56** | **14** | **33** | **23** |

### Event Inventory

| # | Event Name | Type | Category | Attributes | access=global | Likely Scope |
|---|-----------|------|----------|------------|---------------|-------------|
| 1 | EVT_Add3DShape | APP | Other | name:String, id:String, height:Double, width:Double, depth:Double, color:String, label:String, PositionX:Double, PositionY:Double, PositionZ:Double, type:String | No | Public |
| 2 | EVT_AdminTestRenderer_Cancel | APP | Admin | testType:String | No | Public |
| 3 | EVT_AdminTestRenderer_ExplosionChanged | APP | Admin | model:Object | No | Public |
| 4 | EVT_AdminTestRenderer_ExplosionEdit | APP | Admin | framesData:String, annotationData:String | No | Public |
| 5 | EVT_AdminTestRenderer_GroupCreate | APP | Admin | model:Object | No | Public |
| 6 | EVT_AdminTestRenderer_HideGroupDetails | APP | Admin | (none) | No | Public |
| 7 | EVT_AdminTestRenderer_ShowGroupCreate | APP | Admin | callback:Object | No | Public |
| 8 | EVT_AdminTestRenderer_ShowGroupDetails | APP | Admin | group:Object | No | Public |
| 9 | EVT_AdminTestRenderer_Updated | APP | Admin | type:string, model:object | No | Public |
| 10 | EVT_AdvancedLayout_HideContextDetailHeader | APP | Layout | (none) | No | Public |
| 11 | EVT_AdvancedLayout_ShowContextDetailHeader | APP | Layout | (none) | No | Public |
| 12 | EVT_InteractionEvent_Status_Log | APP | Interaction | severity:Integer, logMessage:String | No | Public |
| 13 | EVT_Renderer_Camera_Changed | APP | Renderer | positionX:Double, positionY:Double, positionZ:Double, alpha:Double, beta:Double, radius:Double | No | Public |
| 14 | EVT_Renderer_Component_Transformed | APP | Renderer | name:String, id:String, uniqueId:String, type:String, data:Object | No | Public |
| 15 | EVT_Renderer_Context_Details_Closed | APP | Renderer | (none) | Yes | Public |
| 16 | EVT_Renderer_Element_Added | APP | Renderer | elementType:String, name:String, uniqueId:String, transaction:String | Yes | Public |
| 17 | EVT_Renderer_Element_Verify | APP | Renderer | name:String, isLoaded:Boolean, isVisible:Boolean, isFullyVisible:Boolean, visibility:Double, isEnabled:Boolean, transaction:String | Yes | Public |
| 18 | EVT_Renderer_Get_CameraPositionandTarget | APP | Renderer | data:Object | Yes | Public |
| 19 | EVT_Renderer_Get_Hierarchy | APP | Renderer | data:Object, transaction:String | Yes | Public |
| 20 | EVT_Renderer_Group_Transformed | APP | Renderer | model:Object | No | Public |
| 21 | EVT_Renderer_Input | APP | Renderer | name:String, type:String, label:String, value:Object, metadata:Object | No (access="public") | Public |
| 22 | EVT_Renderer_LabelStyling_Closed | APP | Renderer | (none) | No | Public |
| 23 | EVT_Renderer_LabelStyling_Updated | APP | Renderer | lineColor:String, labelBold:Boolean, lineThickness:Decimal, fontSize:Decimal, align:String, hideable:Boolean, draggable:Boolean | No | Public |
| 24 | EVT_Renderer_Loaded | APP | Renderer | (none) | Yes | Public |
| 25 | EVT_Renderer_Mesh_Hovered | APP | Renderer | name:String, id:String, uniqueId:String, context:Object | Yes | Public |
| 26 | EVT_Renderer_Mesh_Selected | APP | Renderer | name:String, id:String, uniqueId:String, context:Object | Yes | Public |
| 27 | EVT_Renderer_Mesh_Selection_Cleared | APP | Renderer | (none) | Yes | Public |
| 28 | EVT_Renderer_RelatedRecord_Fetched | APP | Renderer | data:Object, foundRecord:Boolean | Yes | Public |
| 29 | EVT_Renderer_Screenshot_Taken | APP | Renderer | data:String | Yes | Public |
| 30 | EVT_Renderer_Select_Component | APP | Renderer | name:String, id:String, uniqueId:String, context:Object | Yes | Public |
| 31 | EVT_Renderer_Settings_Fetched | APP | Renderer | settings:Object | No | Public |
| 32 | EVT_SceneSettings_Ready_For_Update | APP | Scene | sceneSettings:Object, callback:Object, showBusy:Boolean | No | Public |
| 33 | EVT_Settings_Controls_CreateEditCancel | APP | Settings | (none) | No | Likely Internal |
| 34 | EVT_Settings_Controls_CreateEditComplete | APP | Settings | item:RenderDraw_Control_Setting__mdt | No | Likely Internal |
| 35 | EVT_Settings_Controls_InitCreate | APP | Settings | (none) | No | Likely Internal |
| 36 | EVT_Settings_Controls_List_Selected | APP | Settings | item:RenderDraw_Control_Setting__mdt | No | Likely Internal |
| 37 | EVT_Settings_Controls_RefreshList | APP | Settings | (none) | No | Likely Internal |
| 38 | EVT_Settings_Light_CreateEditCancel | APP | Settings | (none) | No | Likely Internal |
| 39 | EVT_Settings_Light_CreateEditComplete | APP | Settings | item:RenderDraw_Light_Setting__mdt | No | Likely Internal |
| 40 | EVT_Settings_Light_InitCreate | APP | Settings | (none) | No | Likely Internal |
| 41 | EVT_Settings_Light_List_Selected | APP | Settings | item:object | No | Likely Internal |
| 42 | EVT_Settings_Light_RefreshList | APP | Settings | (none) | No | Likely Internal |
| 43 | EVT_Settings_Related_DisplayRelated_RenderDraw | APP | Settings | item:object | No | Likely Internal |
| 44 | EVT_Settings_Relationship_CreateEditCancel | APP | Settings | (none) | No | Likely Internal |
| 45 | EVT_Settings_Relationship_CreateEditComplete | APP | Settings | item:RenderDraw_Relationship__mdt | No | Likely Internal |
| 46 | EVT_Settings_Relationship_InitCreate | APP | Settings | (none) | No | Likely Internal |
| 47 | EVT_Settings_Relationship_List_Selected | APP | Settings | item:RenderDraw_Relationship__mdt | No | Likely Internal |
| 48 | EVT_Settings_Relationship_RefreshList | APP | Settings | (none) | No | Likely Internal |
| 49 | EVT_Settings_RenderDraw_CreateEditCancel | APP | Settings | item:RenderDraw_Setting__mdt | No | Likely Internal |
| 50 | EVT_Settings_RenderDraw_CreateEditComplete | APP | Settings | item:RenderDraw_Setting__mdt | No | Likely Internal |
| 51 | EVT_Settings_RenderDraw_DisplayRelated_Control | APP | Settings | item:object | No | Likely Internal |
| 52 | EVT_Settings_RenderDraw_DisplayRelated_Light | APP | Settings | item:object | No | Likely Internal |
| 53 | EVT_Settings_RenderDraw_InitCreate | APP | Settings | (none) | No | Likely Internal |
| 54 | EVT_Settings_RenderDraw_List_Selected | APP | Settings | item:object | No | Likely Internal |
| 55 | EVT_Settings_RenderDraw_RefreshList | APP | Settings | (none) | No | Likely Internal |
| 56 | EVT_Switch_Tab | APP | Other | tabname:String | No | Public |

### Event Detail (grouped by category)

#### Renderer Events (19)

##### EVT_Renderer_Camera_Changed
- **File:** `aura/EVT_Renderer_Camera_Changed/EVT_Renderer_Camera_Changed.evt`
- **Type:** APPLICATION
- **Description:** "Raised when the 3D Camera changes"
- **Attributes:**
  | Name | Type | Description |
  |------|------|-------------|
  | positionX | Double | Camera Position X |
  | positionY | Double | Camera Position Y |
  | positionZ | Double | Camera Position Z |
  | alpha | Double | Camera alpha |
  | beta | Double | Camera beta |
  | radius | Double | Camera radius |

##### EVT_Renderer_Component_Transformed
- **File:** `aura/EVT_Renderer_Component_Transformed/EVT_Renderer_Component_Transformed.evt`
- **Type:** APPLICATION
- **Attributes:**
  | Name | Type | Description |
  |------|------|-------------|
  | name | String | — |
  | id | String | — |
  | uniqueId | String | — |
  | type | String | One of 'size','rotate','position' — the transformation type |
  | data | Object | The underlying data for the transformation |

##### EVT_Renderer_Context_Details_Closed
- **File:** `aura/EVT_Renderer_Context_Details_Closed/EVT_Renderer_Context_Details_Closed.evt`
- **Type:** APPLICATION | **access:** global
- **Attributes:** (none)

##### EVT_Renderer_Element_Added
- **File:** `aura/EVT_Renderer_Element_Added/EVT_Renderer_Element_Added.evt`
- **Type:** APPLICATION | **access:** global
- **Attributes:**
  | Name | Type | Required | access |
  |------|------|----------|--------|
  | elementType | String | true | global |
  | name | String | true | global |
  | uniqueId | String | true | global |
  | transaction | String | false | global |

##### EVT_Renderer_Element_Verify
- **File:** `aura/EVT_Renderer_Element_Verify/EVT_Renderer_Element_Verify.evt`
- **Type:** APPLICATION | **access:** global
- **Attributes:**
  | Name | Type | access |
  |------|------|--------|
  | name | String | global |
  | isLoaded | Boolean | global |
  | isVisible | Boolean | global |
  | isFullyVisible | Boolean | global |
  | visibility | Double | global |
  | isEnabled | Boolean | global |
  | transaction | String | global |
  Note: commented-out attribute `isIsolated:Boolean` exists but is inactive.

##### EVT_Renderer_Get_CameraPositionandTarget
- **File:** `aura/EVT_Renderer_Get_CameraPositionandTarget/EVT_Renderer_Get_CameraPositionandTarget.evt`
- **Type:** APPLICATION | **access:** global
- **Attributes:**
  | Name | Type | Required | access |
  |------|------|----------|--------|
  | data | Object | true | global |

##### EVT_Renderer_Get_Hierarchy
- **File:** `aura/EVT_Renderer_Get_Hierarchy/EVT_Renderer_Get_Hierarchy.evt`
- **Type:** APPLICATION | **access:** global
- **Attributes:**
  | Name | Type | Required | access |
  |------|------|----------|--------|
  | data | Object | true | global |
  | transaction | String | false | global |

##### EVT_Renderer_Group_Transformed
- **File:** `aura/EVT_Renderer_Group_Transformed/EVT_Renderer_Group_Transformed.evt`
- **Type:** APPLICATION
- **Attributes:**
  | Name | Type |
  |------|------|
  | model | Object |

##### EVT_Renderer_Input
- **File:** `aura/EVT_Renderer_Input/EVT_Renderer_Input.evt`
- **Type:** APPLICATION | **access:** public (not global)
- **Attributes:**
  | Name | Type | Description |
  |------|------|-------------|
  | name | String | The name of the action |
  | type | String | The type of the action, one of change, focus, focuslost |
  | label | String | The label of the interaction |
  | value | Object | The updated value from the interaction |
  | metadata | Object | Additional information for the event |

##### EVT_Renderer_LabelStyling_Closed
- **File:** `aura/EVT_Renderer_LabelStyling_Closed/EVT_Renderer_LabelStyling_Closed.evt`
- **Type:** APPLICATION
- **Attributes:** (none)

##### EVT_Renderer_LabelStyling_Updated
- **File:** `aura/EVT_Renderer_LabelStyling_Updated/EVT_Renderer_LabelStyling_Updated.evt`
- **Type:** APPLICATION
- **Attributes:**
  | Name | Type |
  |------|------|
  | lineColor | String |
  | labelBold | Boolean |
  | lineThickness | Decimal |
  | fontSize | Decimal |
  | align | String |
  | hideable | Boolean |
  | draggable | Boolean |

##### EVT_Renderer_Loaded
- **File:** `aura/EVT_Renderer_Loaded/EVT_Renderer_Loaded.evt`
- **Type:** APPLICATION | **access:** global
- **Attributes:** (none)

##### EVT_Renderer_Mesh_Hovered
- **File:** `aura/EVT_Renderer_Mesh_Hovered/EVT_Renderer_Mesh_Hovered.evt`
- **Type:** APPLICATION | **access:** global (on attributes)
- **Attributes:**
  | Name | Type | Required | access |
  |------|------|----------|--------|
  | name | String | true | global |
  | id | String | true | global |
  | uniqueId | String | true | global |
  | context | Object | false | global |

##### EVT_Renderer_Mesh_Selected
- **File:** `aura/EVT_Renderer_Mesh_Selected/EVT_Renderer_Mesh_Selected.evt`
- **Type:** APPLICATION | **access:** global
- **Attributes:**
  | Name | Type | Required | access |
  |------|------|----------|--------|
  | name | String | true | global |
  | id | String | true | global |
  | uniqueId | String | true | global |
  | context | Object | false | global |

##### EVT_Renderer_Mesh_Selection_Cleared
- **File:** `aura/EVT_Renderer_Mesh_Selection_Cleared/EVT_Renderer_Mesh_Selection_Cleared.evt`
- **Type:** APPLICATION | **access:** global
- **Attributes:** (none)

##### EVT_Renderer_RelatedRecord_Fetched
- **File:** `aura/EVT_Renderer_RelatedRecord_Fetched/EVT_Renderer_RelatedRecord_Fetched.evt`
- **Type:** APPLICATION | **access:** global
- **Attributes:**
  | Name | Type | Required | access |
  |------|------|----------|--------|
  | data | Object | true | global |
  | foundRecord | Boolean | true | global |

##### EVT_Renderer_Screenshot_Taken
- **File:** `aura/EVT_Renderer_Screenshot_Taken/EVT_Renderer_Screenshot_Taken.evt`
- **Type:** APPLICATION | **access:** global
- **Attributes:**
  | Name | Type | access |
  |------|------|--------|
  | data | String | global |

##### EVT_Renderer_Select_Component
- **File:** `aura/EVT_Renderer_Select_Component/EVT_Renderer_Select_Component.evt`
- **Type:** APPLICATION | **access:** global
- **Attributes:**
  | Name | Type | access |
  |------|------|--------|
  | name | String | global |
  | id | String | global |
  | uniqueId | String | global |
  | context | Object | global |

##### EVT_Renderer_Settings_Fetched
- **File:** `aura/EVT_Renderer_Settings_Fetched/EVT_Renderer_Settings_Fetched.evt`
- **Type:** APPLICATION
- **Attributes:**
  | Name | Type |
  |------|------|
  | settings | Object |

#### Admin Events (8)

##### EVT_AdminTestRenderer_Cancel
- **Attributes:** testType:String

##### EVT_AdminTestRenderer_ExplosionChanged
- **Attributes:** model:Object

##### EVT_AdminTestRenderer_ExplosionEdit
- **Attributes:** framesData:String, annotationData:String

##### EVT_AdminTestRenderer_GroupCreate
- **Attributes:** model:Object

##### EVT_AdminTestRenderer_HideGroupDetails
- **Attributes:** (none)

##### EVT_AdminTestRenderer_ShowGroupCreate
- **Attributes:** callback:Object

##### EVT_AdminTestRenderer_ShowGroupDetails
- **Attributes:** group:Object

##### EVT_AdminTestRenderer_Updated
- **Attributes:** type:string, model:object

#### Layout Events (2)

##### EVT_AdvancedLayout_HideContextDetailHeader
- **Attributes:** (none)

##### EVT_AdvancedLayout_ShowContextDetailHeader
- **Attributes:** (none)

#### Scene Events (1)

##### EVT_SceneSettings_Ready_For_Update
- **Attributes:** sceneSettings:Object, callback:Object, showBusy:Boolean

#### Interaction Events (1)

##### EVT_InteractionEvent_Status_Log
- **Attributes:** severity:Integer, logMessage:String

#### Settings Events (23 — Likely Internal)

CRUD pattern across 5 custom metadata entities:
- **Controls** (RenderDraw_Control_Setting__mdt): CreateEditCancel, CreateEditComplete, InitCreate, List_Selected, RefreshList
- **Light** (RenderDraw_Light_Setting__mdt): CreateEditCancel, CreateEditComplete, InitCreate, List_Selected, RefreshList
- **Relationship** (RenderDraw_Relationship__mdt): CreateEditCancel, CreateEditComplete, InitCreate, List_Selected, RefreshList
- **RenderDraw** (RenderDraw_Setting__mdt): CreateEditCancel, CreateEditComplete, InitCreate, List_Selected, RefreshList, DisplayRelated_Control, DisplayRelated_Light
- **Related**: DisplayRelated_RenderDraw

All Settings events pass an `item` attribute typed to their respective custom metadata type (or generic `object`). None have `access="global"`.

#### Other Events (2)

##### EVT_Add3DShape
- **Attributes:** name:String, id:String, height:Double, width:Double, depth:Double, color:String, label:String, PositionX:Double, PositionY:Double, PositionZ:Double, type:String

##### EVT_Switch_Tab
- **Attributes:** tabname:String

### Aura Events Notable Observations
- **All 56 are APPLICATION type** — no COMPONENT events exist
- **14 have access="global"** — all in Renderer category — confirming these as the public API surface accessible across namespaces
- **EVT_Renderer_Input** uniquely uses `access="public"` (not "global")
- **Most descriptions are generic** "Event template" — only EVT_Renderer_Camera_Changed has a meaningful description
- **Settings events follow consistent CRUD pattern** across 5 custom metadata entity groups
- **Custom metadata types referenced:** RenderDraw_Control_Setting__mdt, RenderDraw_Light_Setting__mdt, RenderDraw_Relationship__mdt, RenderDraw_Setting__mdt
- **Commented-out attribute:** EVT_Renderer_Element_Verify has inactive `isIsolated:Boolean`
