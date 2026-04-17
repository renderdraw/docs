# Source Inventory: Aura Event Source/Handler Mapping

**Generated:** 2026-04-17 (Phase 3, Plan 03-01)
**Source:** Main RenderDraw package (`/Users/erikpilgrim/Documents/Dev/Personal/RenderDraw SFDC/RenderDraw/force-app/main/default/`)
**Scope:** 33 public-facing Aura events (excludes 23 internal settings-namespace events covering CRUD across the four `_mdt` custom metadata types)
**Supersedes:** Extends Phase 1 `source-lms-events.md` with firing/handling component mappings.

## Methodology

Firing ("Source") components were identified by `<aura:registerEvent type="RDraw:EVT_*">` declarations in `.cmp` files — the canonical declaration of an Aura component that *may fire* an application event. Legacy dotted-namespace form `type="RDraw.EVT_*"` was included (used by AdvancedRenderer and AdminTestRenderer for a handful of events).

Handling ("Handler") components were identified by `<aura:handler event="RDraw:EVT_*">` declarations in `.cmp` files.

LWC components do not use `aura:registerEvent`. One LWC (`annotations3D`) dispatches a DOM `CustomEvent("EVT_SceneSettings_Ready_For_Update")` that bubbles up to an Aura container — noted in Observations but not counted as a primary source.

## Summary by Category

| Category | Count | access=global | Source Components (distinct) | Handler Components (distinct) |
| --- | --- | --- | --- | --- |
| Renderer | 19 | 14 | SimpleRenderer, AdvancedRenderer, AdvancedLayout | AdvancedRenderer, AdminVisualSceneSetup, AdminVisualSceneParameters, AdminTestRenderer, SceneSetup, SetupElementMapping |
| Admin | 8 | 0 | AdminExplosionSetup, AdminVisualSceneParameters, AdminTestRenderer | AdminVisualSceneSetup, SceneSetup_InteractionEvents, AdminTestRenderer |
| Layout | 2 | 0 | AdminExplosionSetup | AdminVisualSceneSetup |
| Scene | 1 | 0 | SceneSetup_InteractionEvents, AdminVisualSceneSetup | SceneSetup |
| Interaction | 1 | 0 | AdvancedRenderer | AdminTestRenderer |
| Other | 2 | 0 | SimpleRenderer, AdminVisualSceneSetup | SceneSetup |
| **Total** | **33** | **14** | — | — |

## Event-by-Event Mapping

| Event | Category | access | Source Component(s) | Handler Component(s) | Notes |
| --- | --- | --- | --- | --- | --- |
| EVT_Add3DShape | Other | No | SimpleRenderer | (external) | Fires from SimpleRenderer; no in-package handler. |
| EVT_AdminTestRenderer_Cancel | Admin | No | AdminVisualSceneParameters, AdminTestRenderer | SceneSetup_InteractionEvents | — |
| EVT_AdminTestRenderer_ExplosionChanged | Admin | No | AdminExplosionSetup | AdminVisualSceneSetup | — |
| EVT_AdminTestRenderer_ExplosionEdit | Admin | No | AdminExplosionSetup | AdminVisualSceneSetup | — |
| EVT_AdminTestRenderer_GroupCreate | Admin | No | (none) | AdminVisualSceneSetup | No in-package source. |
| EVT_AdminTestRenderer_HideGroupDetails | Admin | No | (none) | AdminVisualSceneSetup | No in-package source. |
| EVT_AdminTestRenderer_ShowGroupCreate | Admin | No | AdminExplosionSetup | AdminVisualSceneSetup | — |
| EVT_AdminTestRenderer_ShowGroupDetails | Admin | No | (none) | AdminVisualSceneSetup | No in-package source. |
| EVT_AdminTestRenderer_Updated | Admin | No | AdminVisualSceneParameters, AdminTestRenderer | SceneSetup_InteractionEvents, AdminVisualSceneSetup | — |
| EVT_AdvancedLayout_HideContextDetailHeader | Layout | No | AdminExplosionSetup | AdminVisualSceneSetup | — |
| EVT_AdvancedLayout_ShowContextDetailHeader | Layout | No | AdminExplosionSetup | AdminVisualSceneSetup | — |
| EVT_InteractionEvent_Status_Log | Interaction | No | AdvancedRenderer | AdminTestRenderer | — |
| EVT_Renderer_Camera_Changed | Renderer | No | SimpleRenderer | (external) | No in-package handler. |
| EVT_Renderer_Component_Transformed | Renderer | No | SimpleRenderer | AdminVisualSceneParameters, AdminTestRenderer, AdminVisualSceneSetup | — |
| EVT_Renderer_Context_Details_Closed | Renderer | global | AdvancedLayout | SceneSetup, AdminVisualSceneSetup | — |
| EVT_Renderer_Element_Added | Renderer | global | SimpleRenderer | AdvancedRenderer | — |
| EVT_Renderer_Element_Verify | Renderer | global | SimpleRenderer | AdvancedRenderer | — |
| EVT_Renderer_Get_CameraPositionandTarget | Renderer | global | SimpleRenderer | AdvancedRenderer | — |
| EVT_Renderer_Get_Hierarchy | Renderer | global | SimpleRenderer | AdminVisualSceneParameters, AdvancedRenderer, AdminVisualSceneSetup | — |
| EVT_Renderer_Group_Transformed | Renderer | No | (none) | AdminVisualSceneSetup | No in-package source. |
| EVT_Renderer_Input | Renderer | public | (none) | (external) | No in-package source or handler — `access="public"` (not `global`). |
| EVT_Renderer_LabelStyling_Closed | Renderer | No | SimpleRenderer | AdminVisualSceneSetup | — |
| EVT_Renderer_LabelStyling_Updated | Renderer | No | SimpleRenderer | AdminVisualSceneSetup | — |
| EVT_Renderer_Loaded | Renderer | global | SimpleRenderer | AdminVisualSceneParameters, AdminTestRenderer, SetupElementMapping, AdvancedRenderer | — |
| EVT_Renderer_Mesh_Hovered | Renderer | global | SimpleRenderer | AdminVisualSceneParameters, AdvancedRenderer | — |
| EVT_Renderer_Mesh_Selected | Renderer | global | SimpleRenderer | AdminVisualSceneParameters, AdminTestRenderer, AdminVisualSceneSetup, AdvancedRenderer | — |
| EVT_Renderer_Mesh_Selection_Cleared | Renderer | global | SimpleRenderer | AdminVisualSceneParameters, AdminVisualSceneSetup, AdvancedRenderer | — |
| EVT_Renderer_RelatedRecord_Fetched | Renderer | global | AdvancedRenderer | (external) | No in-package handler. |
| EVT_Renderer_Screenshot_Taken | Renderer | global | SimpleRenderer | (external) | No in-package handler. |
| EVT_Renderer_Select_Component | Renderer | global | (none) | AdvancedRenderer | No in-package source — intended to be fired by external/consumer components to drive programmatic selection. |
| EVT_Renderer_Settings_Fetched | Renderer | No | SimpleRenderer | AdvancedRenderer, SetupElementMapping, SceneSetup | — |
| EVT_SceneSettings_Ready_For_Update | Scene | No | SceneSetup_InteractionEvents, AdminVisualSceneSetup | SceneSetup | Also dispatched as a DOM CustomEvent by LWC `annotations3D`. |
| EVT_Switch_Tab | Other | No | AdminVisualSceneSetup | SceneSetup | — |

## Event Detail (grouped by category)

### Renderer Events (19)

#### EVT_Renderer_Camera_Changed
- **access:** — | **attributes:** positionX, positionY, positionZ, alpha, beta, radius
- **Source Component(s):** SimpleRenderer
- **Handler Component(s):** None in main package — consumed by external implementing components
- **Bidirectional:** No
- **Notes:** —

#### EVT_Renderer_Component_Transformed
- **access:** — | **attributes:** name, id, uniqueId, type, data
- **Source Component(s):** SimpleRenderer
- **Handler Component(s):** AdminVisualSceneParameters, AdminTestRenderer, AdminVisualSceneSetup
- **Bidirectional:** No
- **Notes:** —

#### EVT_Renderer_Context_Details_Closed
- **access:** global | **attributes:** (none)
- **Source Component(s):** AdvancedLayout
- **Handler Component(s):** SceneSetup, AdminVisualSceneSetup
- **Bidirectional:** No
- **Notes:** —

#### EVT_Renderer_Element_Added
- **access:** global | **attributes:** elementType, name, uniqueId, transaction
- **Source Component(s):** SimpleRenderer
- **Handler Component(s):** AdvancedRenderer
- **Bidirectional:** No
- **Notes:** —

#### EVT_Renderer_Element_Verify
- **access:** global | **attributes:** name, isLoaded, isVisible, isFullyVisible, visibility, isEnabled, transaction (plus commented-out `isIsolated:Boolean` — see source-lms-events.md)
- **Source Component(s):** SimpleRenderer
- **Handler Component(s):** AdvancedRenderer
- **Bidirectional:** No
- **Notes:** —

#### EVT_Renderer_Get_CameraPositionandTarget
- **access:** global | **attributes:** data
- **Source Component(s):** SimpleRenderer
- **Handler Component(s):** AdvancedRenderer
- **Bidirectional:** No
- **Notes:** —

#### EVT_Renderer_Get_Hierarchy
- **access:** global | **attributes:** data, transaction
- **Source Component(s):** SimpleRenderer
- **Handler Component(s):** AdminVisualSceneParameters, AdvancedRenderer, AdminVisualSceneSetup
- **Bidirectional:** No
- **Notes:** —

#### EVT_Renderer_Group_Transformed
- **access:** — | **attributes:** model
- **Source Component(s):** None found in main package
- **Handler Component(s):** AdminVisualSceneSetup
- **Bidirectional:** No
- **Notes:** Handler registered but no in-package registerEvent — likely fired from a secondary package or from a runtime-only JS path not captured by grep. Flag for manual verification.

#### EVT_Renderer_Input
- **access:** public (not global) | **attributes:** name, type, label, value, metadata
- **Source Component(s):** None found in main package
- **Handler Component(s):** None in main package — consumed by external implementing components
- **Bidirectional:** No
- **Notes:** The event uses `access="public"` rather than `global`. Neither source nor handler found in main package — this event is defined solely for external (consumer-package) use.

#### EVT_Renderer_LabelStyling_Closed
- **access:** — | **attributes:** (none)
- **Source Component(s):** SimpleRenderer
- **Handler Component(s):** AdminVisualSceneSetup
- **Bidirectional:** No
- **Notes:** —

#### EVT_Renderer_LabelStyling_Updated
- **access:** — | **attributes:** lineColor, labelBold, lineThickness, fontSize, align, hideable, draggable
- **Source Component(s):** SimpleRenderer
- **Handler Component(s):** AdminVisualSceneSetup
- **Bidirectional:** No
- **Notes:** —

#### EVT_Renderer_Loaded
- **access:** global | **attributes:** (none)
- **Source Component(s):** SimpleRenderer
- **Handler Component(s):** AdminVisualSceneParameters, AdminTestRenderer, SetupElementMapping, AdvancedRenderer
- **Bidirectional:** No
- **Notes:** AdvancedRenderer handles this event from its nested `<RDraw:SimpleRenderer/>` child — this is the canonical bridge between the two renderer components.

#### EVT_Renderer_Mesh_Hovered
- **access:** global | **attributes:** name, id, uniqueId, context
- **Source Component(s):** SimpleRenderer
- **Handler Component(s):** AdminVisualSceneParameters, AdvancedRenderer
- **Bidirectional:** No
- **Notes:** —

#### EVT_Renderer_Mesh_Selected
- **access:** global | **attributes:** name, id, uniqueId, context
- **Source Component(s):** SimpleRenderer
- **Handler Component(s):** AdminVisualSceneParameters, AdminTestRenderer, AdminVisualSceneSetup, AdvancedRenderer
- **Bidirectional:** No
- **Notes:** Highest-fanout handler list (4 handlers) — core selection signal.

#### EVT_Renderer_Mesh_Selection_Cleared
- **access:** global | **attributes:** (none)
- **Source Component(s):** SimpleRenderer
- **Handler Component(s):** AdminVisualSceneParameters, AdminVisualSceneSetup, AdvancedRenderer
- **Bidirectional:** No
- **Notes:** —

#### EVT_Renderer_RelatedRecord_Fetched
- **access:** global | **attributes:** data, foundRecord
- **Source Component(s):** AdvancedRenderer
- **Handler Component(s):** None in main package — consumed by external implementing components
- **Bidirectional:** No
- **Notes:** Fired from AdvancedRenderer via legacy `type="RDraw.EVT_..."` dotted form.

#### EVT_Renderer_Screenshot_Taken
- **access:** global | **attributes:** data
- **Source Component(s):** SimpleRenderer
- **Handler Component(s):** None in main package — consumed by external implementing components
- **Bidirectional:** No
- **Notes:** —

#### EVT_Renderer_Select_Component
- **access:** global | **attributes:** name, id, uniqueId, context
- **Source Component(s):** None found in main package
- **Handler Component(s):** AdvancedRenderer
- **Bidirectional:** No
- **Notes:** Programmatic-select API — consumer-package components fire this event to instruct AdvancedRenderer to select a specific 3D component. AdvancedRenderer's `.cmp` carries a `description` attribute referring to this event.

#### EVT_Renderer_Settings_Fetched
- **access:** — | **attributes:** settings
- **Source Component(s):** SimpleRenderer
- **Handler Component(s):** AdvancedRenderer, SetupElementMapping, SceneSetup
- **Bidirectional:** No
- **Notes:** —

### Admin Events (8)

#### EVT_AdminTestRenderer_Cancel
- **access:** — | **attributes:** testType
- **Source Component(s):** AdminVisualSceneParameters, AdminTestRenderer
- **Handler Component(s):** SceneSetup_InteractionEvents
- **Bidirectional:** No
- **Notes:** —

#### EVT_AdminTestRenderer_ExplosionChanged
- **access:** — | **attributes:** model
- **Source Component(s):** AdminExplosionSetup
- **Handler Component(s):** AdminVisualSceneSetup
- **Bidirectional:** No
- **Notes:** —

#### EVT_AdminTestRenderer_ExplosionEdit
- **access:** — | **attributes:** framesData, annotationData
- **Source Component(s):** AdminExplosionSetup
- **Handler Component(s):** AdminVisualSceneSetup
- **Bidirectional:** No
- **Notes:** —

#### EVT_AdminTestRenderer_GroupCreate
- **access:** — | **attributes:** model
- **Source Component(s):** None found in main package
- **Handler Component(s):** AdminVisualSceneSetup
- **Bidirectional:** No
- **Notes:** Handler registered but no in-package `aura:registerEvent` — likely fired from a dynamic context or secondary package. Flag for manual verification.

#### EVT_AdminTestRenderer_HideGroupDetails
- **access:** — | **attributes:** (none)
- **Source Component(s):** None found in main package
- **Handler Component(s):** AdminVisualSceneSetup
- **Bidirectional:** No
- **Notes:** Handler registered but no in-package source. Flag for manual verification.

#### EVT_AdminTestRenderer_ShowGroupCreate
- **access:** — | **attributes:** callback
- **Source Component(s):** AdminExplosionSetup
- **Handler Component(s):** AdminVisualSceneSetup
- **Bidirectional:** No
- **Notes:** —

#### EVT_AdminTestRenderer_ShowGroupDetails
- **access:** — | **attributes:** group
- **Source Component(s):** None found in main package
- **Handler Component(s):** AdminVisualSceneSetup
- **Bidirectional:** No
- **Notes:** Handler registered but no in-package source. Flag for manual verification.

#### EVT_AdminTestRenderer_Updated
- **access:** — | **attributes:** type, model
- **Source Component(s):** AdminVisualSceneParameters, AdminTestRenderer
- **Handler Component(s):** SceneSetup_InteractionEvents, AdminVisualSceneSetup
- **Bidirectional:** No
- **Notes:** Fired via legacy `type="RDraw.EVT_..."` dotted form from both sources.

### Layout Events (2)

#### EVT_AdvancedLayout_HideContextDetailHeader
- **access:** — | **attributes:** (none)
- **Source Component(s):** AdminExplosionSetup
- **Handler Component(s):** AdminVisualSceneSetup
- **Bidirectional:** No
- **Notes:** The `event="..."` attribute in AdminVisualSceneSetup.cmp is on a continuation line — captured only by multi-attribute grep.

#### EVT_AdvancedLayout_ShowContextDetailHeader
- **access:** — | **attributes:** (none)
- **Source Component(s):** AdminExplosionSetup
- **Handler Component(s):** AdminVisualSceneSetup
- **Bidirectional:** No
- **Notes:** Same as above — handler attribute spans multiple lines in source.

### Scene Events (1)

#### EVT_SceneSettings_Ready_For_Update
- **access:** — | **attributes:** sceneSettings, callback, showBusy
- **Source Component(s):** SceneSetup_InteractionEvents, AdminVisualSceneSetup
- **Handler Component(s):** SceneSetup
- **Bidirectional:** No
- **Notes:** LWC `annotations3D` also dispatches a DOM `CustomEvent("EVT_SceneSettings_Ready_For_Update")` which bubbles up to its Aura container; `custom3DExplosion` (LWC) contains a commented-out dispatch of the same. Not counted as a primary source because LWCs cannot directly fire Aura application events.

### Interaction Events (1)

#### EVT_InteractionEvent_Status_Log
- **access:** — | **attributes:** severity, logMessage
- **Source Component(s):** AdvancedRenderer
- **Handler Component(s):** AdminTestRenderer
- **Bidirectional:** No
- **Notes:** Fired from AdvancedRenderer via legacy `type="RDraw.EVT_..."` dotted form.

### Other Events (2)

#### EVT_Add3DShape
- **access:** — | **attributes:** name, id, height, width, depth, color, label, PositionX, PositionY, PositionZ, type
- **Source Component(s):** SimpleRenderer
- **Handler Component(s):** None in main package — consumed by external implementing components
- **Bidirectional:** No
- **Notes:** —

#### EVT_Switch_Tab
- **access:** — | **attributes:** tabname
- **Source Component(s):** AdminVisualSceneSetup
- **Handler Component(s):** SceneSetup
- **Bidirectional:** No
- **Notes:** —

## Observations

- **SimpleRenderer is the primary Renderer-category source** — it registers 14 of the 19 Renderer events. AdvancedRenderer (which nests SimpleRenderer) handles many of these events and registers only 2 of its own (`EVT_InteractionEvent_Status_Log`, `EVT_Renderer_RelatedRecord_Fetched`) plus one Layout event (`EVT_Renderer_Context_Details_Closed` is registered by AdvancedLayout, not AdvancedRenderer).
- **AdvancedRenderer is the user-facing container.** For documentation purposes, consumers embed `<RDraw:AdvancedRenderer/>` and receive events from its nested `SimpleRenderer`. Per-event documentation pages should consider noting "fired by SimpleRenderer (embedded in AdvancedRenderer)" where relevant.
- **AdminVisualSceneSetup is the busiest handler** — subscribes to 16 distinct events, making it the hub of the admin/setup UI.
- **No bidirectional events detected** — no component both registers and handles the same event in the main package.
- **5 events have no in-package handler** (consumed externally): `EVT_Add3DShape`, `EVT_Renderer_Camera_Changed`, `EVT_Renderer_Input`, `EVT_Renderer_RelatedRecord_Fetched`, `EVT_Renderer_Screenshot_Taken`. These are the classic "fire-and-forget" public API events that consumer components are expected to listen for.
- **6 events have no in-package source**: `EVT_AdminTestRenderer_GroupCreate`, `EVT_AdminTestRenderer_HideGroupDetails`, `EVT_AdminTestRenderer_ShowGroupDetails`, `EVT_Renderer_Group_Transformed`, `EVT_Renderer_Input`, `EVT_Renderer_Select_Component`. All except `EVT_Renderer_Input` have in-package handlers. These are the classic "consumer fires, RenderDraw listens" public API events — consumer components call them to drive RenderDraw behavior (e.g. programmatic selection via `EVT_Renderer_Select_Component`).
- **`EVT_Renderer_Input` is isolated** — no source and no handler in the main package; defined purely as a public API surface for external components.
- **Legacy dotted namespace** `type="RDraw.EVT_*"` (using `.` instead of `:`) is used for 4 registerEvent declarations across AdminTestRenderer and AdvancedRenderer: `EVT_AdminTestRenderer_Cancel`, `EVT_AdminTestRenderer_Updated`, `EVT_InteractionEvent_Status_Log`, `EVT_Renderer_RelatedRecord_Fetched`. Handlers always use `event="RDraw:EVT_*"` (colon form). Both forms resolve to the same event in the Aura runtime.
- **LWC dispatch of Aura-style event name**: `annotations3D.js` dispatches `new CustomEvent("EVT_SceneSettings_Ready_For_Update", ...)` — a DOM event that bubbles to an Aura parent which then handles the Aura app event. Recorded but not counted as an Aura source.
- **`EVT_Renderer_Element_Verify`** carries a commented-out `isIsolated:Boolean` attribute (documented in Phase 1 `source-lms-events.md`). This inventory covers source/handler only; attribute documentation remains in `source-lms-events.md`.

## Notes for Plans 03-02 through 03-05

- **Events flagged "(none)" for source** need a manual note on the documentation page explaining they are fired by consumer components, not by RenderDraw itself (e.g. `EVT_Renderer_Select_Component` — "Fire this event from your own component to request that the renderer select a 3D node.").
- **Events flagged "(external)" for handler** should be documented as "fired by RenderDraw — subscribe from your own component to react."
- **Bidirectional annotations**: no events in this inventory are bidirectional. If Plans 03-02 through 03-05 discover a case via closer inspection, annotate `(bidirectional)` on the offending Source/Handler list to match the Phase 2 LMS convention.
- **Event Name (for handler) string**: always `RDraw:EVT_<Name>` (colon form). Use the colon form in `<aura:handler event="..."/>` samples even if the source package uses the dotted form in `aura:registerEvent` — the colon form is the modern convention and both resolve identically.
- **Renderer events source attribution**: when documenting Renderer events, the authoritative source is `SimpleRenderer`, but the user-facing embedder is `AdvancedRenderer`. Recommend consistent framing: "Fired by `SimpleRenderer` (exposed through `AdvancedRenderer`)" to avoid confusion. Plans 03-02 through 03-05 should agree on wording.
