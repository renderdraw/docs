# RenderDraw Documentation Gap Report

**Generated:** 2026-04-17
**Source:** Phase 1 Audit & Gap Analysis (Plans 01-01 through 01-05)

## Executive Summary

| Metric | Count | % |
|--------|-------|---|
| Total source API items (main package) | 295 | — |
| Documented | 32 | 11% |
| Partially documented | 15 | 5% |
| Undocumented | 225 | 76% |
| Covered by extracted docs (not in GitBook) | 2 | 1% |
| Internal only (excluded) | 21 | 7% |
| Empty stub pages to populate | 26 | — |
| Empty index pages to populate | 14 | — |
| Secondary package items (PropelPLM + ADT) | 30 | — |

**Breakdown of 295 main package source items:**
- 5 LMS Message Channels
- 56 Aura Events (23 internal = excluded)
- 136 LWC components with @api (+ 33 without @api)
- 35 Aura components (excluding EVT_*)
- 64 Apex classes (34 global + 30 public with annotations)

---

## Gap by API Surface Type

### LMS Message Channels

All 5 channels are `isExposed: true` and documented in GitBook.

| Channel | Doc Status | Doc Page | Missing Fields | Action Needed |
|---------|-----------|----------|----------------|---------------|
| Canvas_Interaction | Documented | `lms/canvas-interaction.md` | None | Verify field descriptions match source |
| Canvas_Initialized | Documented | `lms/canvas-initialized.md` | None | Verify field descriptions match source |
| Canvas_ElementSelected | Documented | `lms/canvas-element-selected.md` | None | Verify field descriptions match source |
| Canvas_ElementHovered | Documented | `lms/canvas-element-hovered.md` | None | Verify field descriptions match source |
| Record_Selected | Documented | `lms/record-selected.md` | `sender` (commented out in source) | Note commented-out field; verify `record` description |

**Summary:** 5/5 documented. Phase 2 work is verification, not creation. Publisher/subscriber mapping not in docs.

---

### Aura Events

56 total events. 23 Settings events classified as Internal only. 33 public-facing events.

#### Global Events (14) -- access="global"

| Event | Doc Status | Doc Page | Missing Attrs | Phase |
|-------|-----------|----------|---------------|-------|
| EVT_Renderer_Loaded | Documented | `events-aura/evt_renderer_loaded.md` | None | 3 (verify) |
| EVT_Renderer_Context_Details_Closed | Documented | `events-aura/evt_renderer_context_details_closed.md` | None | 3 (verify) |
| EVT_Renderer_Element_Added | Documented | `events-aura/evt_renderer_element_added.md` | `transaction` not in docs | 3 (update) |
| EVT_Renderer_Element_Verify | Undocumented | — | All: name, isLoaded, isVisible, isFullyVisible, visibility, isEnabled, transaction | 3 |
| EVT_Renderer_Get_CameraPositionandTarget | Documented | `events-aura/evt_renderer_get_camerapositionandtarget.md` | None | 3 (verify) |
| EVT_Renderer_Get_Hierarchy | Documented | `events-aura/evt_renderer_get_hierarchy.md` | `transaction` not in docs | 3 (update) |
| EVT_Renderer_Mesh_Hovered | Undocumented | — | All: name, id, uniqueId, context | 3 |
| EVT_Renderer_Mesh_Selected | Partially documented | `events-aura/evt_renderer_mesh_selected.md` | Source has `name` attr; docs show `context` but may differ | 3 (verify) |
| EVT_Renderer_Mesh_Selection_Cleared | Empty stub | `events-aura/evt_renderer_mesh_selection_cleared.md` | Page exists but empty | 3 (populate) |
| EVT_Renderer_RelatedRecord_Fetched | Undocumented | — | All: data, foundRecord | 3 |
| EVT_Renderer_Screenshot_Taken | Documented | `events-aura/evt_renderer_screenshot_taken.md` | None | 3 (verify) |
| EVT_Renderer_Select_Component | Documented | `events-aura/evt_renderer_select_component.md` | None | 3 (verify) |
| EVT_Renderer_Loaded | Documented | `events-aura/evt_renderer_loaded.md` | None | 3 (verify) |
| EVT_Renderer_Mesh_Selected | See above | See above | See above | 3 |

#### Non-Global Public Events (19)

| Event | Doc Status | Category | Attrs | Phase |
|-------|-----------|----------|-------|-------|
| EVT_Renderer_Camera_Changed | Undocumented | Renderer | positionX/Y/Z, alpha, beta, radius | 3 |
| EVT_Renderer_Component_Transformed | Undocumented | Renderer | name, id, uniqueId, type, data | 3 |
| EVT_Renderer_Group_Transformed | Undocumented | Renderer | model | 3 |
| EVT_Renderer_Input | Undocumented | Renderer | name, type, label, value, metadata | 3 |
| EVT_Renderer_LabelStyling_Closed | Undocumented | Renderer | (none) | 3 |
| EVT_Renderer_LabelStyling_Updated | Undocumented | Renderer | lineColor, labelBold, lineThickness, fontSize, align, hideable, draggable | 3 |
| EVT_Renderer_Settings_Fetched | Undocumented | Renderer | settings | 3 |
| EVT_AdminTestRenderer_Cancel | Undocumented | Admin | testType | 3 |
| EVT_AdminTestRenderer_ExplosionChanged | Undocumented | Admin | model | 3 |
| EVT_AdminTestRenderer_ExplosionEdit | Undocumented | Admin | framesData, annotationData | 3 |
| EVT_AdminTestRenderer_GroupCreate | Undocumented | Admin | model | 3 |
| EVT_AdminTestRenderer_HideGroupDetails | Undocumented | Admin | (none) | 3 |
| EVT_AdminTestRenderer_ShowGroupCreate | Undocumented | Admin | callback | 3 |
| EVT_AdminTestRenderer_ShowGroupDetails | Undocumented | Admin | group | 3 |
| EVT_AdminTestRenderer_Updated | Undocumented | Admin | type, model | 3 |
| EVT_AdvancedLayout_HideContextDetailHeader | Undocumented | Layout | (none) | 3 |
| EVT_AdvancedLayout_ShowContextDetailHeader | Undocumented | Layout | (none) | 3 |
| EVT_SceneSettings_Ready_For_Update | Undocumented | Scene | sceneSettings, callback, showBusy | 3 |
| EVT_InteractionEvent_Status_Log | Undocumented | Interaction | severity, logMessage | 3 |
| EVT_Add3DShape | Undocumented | Other | 11 attrs | 3 |
| EVT_Switch_Tab | Undocumented | Other | tabname | 3 |

#### Internal Events (23 -- excluded from documentation scope)

All 23 Settings events (EVT_Settings_Controls_*, EVT_Settings_Light_*, EVT_Settings_Relationship_*, EVT_Settings_RenderDraw_*, EVT_Settings_Related_*) are internal CRUD events for custom metadata admin UIs. None have `access="global"`.

**Summary:** 9 documented (7 with content + 1 empty stub + 1 partial), 3 need updates, 24 undocumented public events, 23 internal.

---

### LWC Component APIs

136 LWC components have @api properties/methods. Key components by documentation status:

#### Core Components (high priority)

| Component | Doc Status | @api Props | @api Methods | Total @api | Doc Page | Missing | Phase |
|-----------|-----------|------------|--------------|------------|----------|---------|-------|
| canvas2D | Partially documented | 21 | 99 | 120 | `2d-components-api/2d-interaction-canvas.md` | Doc shows 9+2 props, 28 methods. Source has 21 props, 99 methods | 4/7 |
| canvas3D | Partially documented | 22 | 92 | 114 | `3d-components-api/components-aura-lwc/3d-interaction-canvas-lwc.md` | Doc shows 31 props, 68 methods. Source has 22 props, 92 methods | 4/7 |
| interactiveMap | Undocumented (API) | 6 | 19 | 25 | Usage docs exist (`interactive-maps/`) but no API ref | All API props/methods | 4 |
| annotateIt | Undocumented (API) | 17 | 0 | 17 | Usage docs exist (`annotateit-images/`) but no API ref | All 17 props | 4 |
| pdfEditor | Undocumented (API) | 18 | 0 | 18 | Usage docs exist (`annotateit-pdf-editor.md`) but no API ref | All 18 props | 4 |
| pdfEditorDigitalExperience | Undocumented | 16 | 0 | 16 | — | All | 4 |
| setupDecalRegion_Editor | Undocumented | 15 | 1 | 16 | — | All | 4 |
| popup | Undocumented | 12 | 0 | 12 | — | All | 4 |
| snapshotPopup | Undocumented | 12 | 0 | 12 | — | All | 4 |
| utilitiesRDSceneSettings | Undocumented | 0 | 23 | 23 | — | All 23 methods | 4 |
| standalone_DataTable | Partially documented | 6 | 0 | 6 | `universal-components/dynamiccontentcomponent_treegrid.md` (partial) | Full API surface | 4 |
| custom3DExplosion | Undocumented | 8 | 1 | 9 | — | All | 4 |
| groupSelection | Undocumented | 6 | 4 | 10 | — | All | 4 |
| layout | Partially documented | 3 | 0 | 3 | `universal-components/rdraw-layout.md` | Verify props match | 4 |
| dynamicContentComponent_treeGrid | Partially documented | 7 | 5 | 12 | `universal-components/dynamiccontentcomponent_treegrid.md` | Doc has headers only, no data | 4 |

#### Extracted Docs Available (not yet in GitBook)

| Component | Status | Extracted Doc | @api Count | Phase |
|-----------|--------|--------------|------------|-------|
| canvas2D | Covered by extracted docs | Canvas2D_API_Documentation.md | 120 | 7 |
| canvas3D | Covered by extracted docs | Canvas3D_API_Documentation.md | 114 | 7 |

#### Secondary Components (lower priority -- undocumented)

All remaining 121 LWC components with @api are **undocumented**. Top 20 by @api count:

| Component | @api Props | @api Methods | Total @api |
|-----------|------------|--------------|------------|
| canvas2D | 21 | 99 | 120 |
| canvas3D | 22 | 92 | 114 |
| interactiveMap | 6 | 19 | 25 |
| utilitiesRDSceneSettings | 0 | 23 | 23 |
| pdfEditor | 18 | 0 | 18 |
| annotateIt | 17 | 0 | 17 |
| pdfEditorDigitalExperience | 16 | 0 | 16 |
| internalLookup | 12 | 4 | 16 |
| setupDecalRegion_Editor | 15 | 1 | 16 |
| popup | 12 | 0 | 12 |
| snapshotPopup | 12 | 0 | 12 |
| dynamicContentComponent_treeGrid | 7 | 5 | 12 |
| adminLogicSceneParameters | 7 | 3 | 10 |
| buttonIconPopover | 6 | 4 | 10 |
| groupSelection | 6 | 4 | 10 |
| admin2DLogicSceneParameters | 6 | 2 | 8 |
| adminLogicTestRenderer | 8 | 0 | 8 |
| dynamicContentComponent_richTextEditor | 8 | 0 | 8 |
| sceneSetup_InteractionEventDetail | 7 | 1 | 8 |
| progressIndicator | 8 | 0 | 8 |

**Summary:** 4 partially documented, 2 covered by extracted docs, 130 undocumented.

---

### Aura Component APIs

35 Aura components (excluding EVT_* event definitions). 7 have `global` access.

| Component | Doc Status | Global | Attr Count | Doc Page | Missing | Phase |
|-----------|-----------|--------|-----------|----------|---------|-------|
| AdvancedRenderer | Partially documented | Yes | 266 | `3d-components-api/components-aura-lwc/3d-advanced-renderer-aura.md` | Doc lists 30 attrs + 42 methods; source has 266 attrs (many are method params) | 5 |
| SimpleRenderer | Partially documented | Yes | 234 | `3d-components-api/components-aura-lwc/3d-simple-renderer-aura.md` | Doc lists 10 attrs; source has 234 (many are method params) | 5 |
| AdvancedLayout | Undocumented | Yes | 18 | — | All 18 global attrs | 5 |
| FileSelector | Partially documented | Yes | 6 | `3d-components-api/components-aura-lwc/3d-file-attachment-viewer-aura.md` | Doc lists 2 attrs; source has 6 | 5 |
| SceneSetup | Undocumented | Yes | 26 | — | All | 5 |
| Settings | Undocumented | Yes | 6 | — | All | 5 |
| FlowData_Canvas2D_ReplaceSceneSettingsElement | Undocumented | Yes | 4 | — | All | 5 |
| AdminExplosionSetup | Undocumented | No | 24 | — | All | 5 |
| AdminTestRenderer | Undocumented | No | 18 | — | All | 5 |
| AdminVisualSceneParameters | Undocumented | No | 24 | — | All | 5 |
| AdminVisualSceneSetup | Undocumented | No | 65 | — | All | 5 |
| SceneSetup_InteractionEvents | Undocumented | No | 17 | — | All | 5 |
| SetupElementMapping | Undocumented | No | 38 | — | All | 5 |
| DynamicContentComponent | Undocumented | No | 1 | — | All | 5 |
| LocalizedSpinner | Undocumented | No | 1 | — | Internal? | 5 |
| Modal | Undocumented | No | 11 | — | All | 5 |
| ReadOnlyLabel | Undocumented | No | 2 | — | Internal? | 5 |
| Settings_Controls | Internal only | No | 5 | — | Settings admin UI | — |
| Settings_Controls_Form | Internal only | No | 7 | — | Settings admin UI | — |
| Settings_Controls_Form_ReadOnly | Internal only | No | 4 | — | Settings admin UI | — |
| Settings_Controls_List | Internal only | No | 7 | — | Settings admin UI | — |
| Settings_Header | Internal only | No | 4 | — | Settings admin UI | — |
| Settings_Light | Internal only | No | 5 | — | Settings admin UI | — |
| Settings_Light_Form | Internal only | No | 7 | — | Settings admin UI | — |
| Settings_Light_Form_ReadOnly | Internal only | No | 4 | — | Settings admin UI | — |
| Settings_Light_List | Internal only | No | 7 | — | Settings admin UI | — |
| Settings_Relationship | Internal only | No | 7 | — | Settings admin UI | — |
| Settings_Relationship_Form | Internal only | No | 11 | — | Settings admin UI | — |
| Settings_Relationship_Form_ReadOnly | Internal only | No | 4 | — | Settings admin UI | — |
| Settings_Relationship_List | Internal only | No | 7 | — | Settings admin UI | — |
| Settings_RenderDraw | Internal only | No | 5 | — | Settings admin UI | — |
| Settings_RenderDraw_Form | Internal only | No | 8 | — | Settings admin UI | — |
| Settings_RenderDraw_Form_ReadOnly | Internal only | No | 8 | — | Settings admin UI | — |
| Settings_RenderDraw_List | Internal only | No | 7 | — | Settings admin UI | — |
| Settings_About | Undocumented | No | 0 | — | No attrs | — |

**Summary:** 3 partially documented, 4 undocumented global, 10 undocumented non-global, 17 internal (Settings_* admin UI), 1 no attrs.

---

### Apex Public APIs

64 Apex classes with annotated methods (34 global, 30 public).

#### Global Classes -- Data Models

| Class | Doc Status | Doc Page | Properties Documented | Missing | Phase |
|-------|-----------|----------|----------------------|---------|-------|
| CanvasScene | Partially documented | `data-objects/canvas.md` (as Canvas) | Partial -- old property set | New properties: gridSize, seedStartX, seedStartY, maxWidthOfAreas, fixAreasToGrid, snapshots, placedSelectableShapes, placedNotes, droppableAreaTemplates, draggableItemTemplates. Methods: toJSON, fromJSON | 6 |
| BaseCanvasItem | Partially documented | `data-objects/basecanvasitem.md` | id, name, recordId, value, x, y, width, height, templateId | Missing: length, rotation, points, metadata | 6 |
| Canvas | Partially documented | `data-objects/canvas.md` | Partial | Missing: placedSelectableShapes, droppableAreas, draggableItems, layoutAreas | 6 |
| DroppableArea | Partially documented | `data-objects/droppablearea.md` | Partial | Verify completeness | 6 |
| DropZone | Partially documented | `data-objects/dropzone.md` | Partial | Verify completeness | 6 |
| LayoutWall | Partially documented | `data-objects/layoutwall.md` | id, x1, y1, x2, y2, points | Missing: height, windows, doors | 6 |
| RenderContext | Undocumented | — | — | All properties + inner classes | 6 |
| SnapShot | Undocumented | — | — | rawData, type, formattedImage | 6 |
| LayoutDoor | Undocumented | — | — | All properties | 6 |
| LayoutWindow | Undocumented | — | — | All properties | 6 |
| DraggableItemTemplate | Undocumented | — | — | All properties + constructor | 6 |
| DroppableAreaTemplate | Undocumented | — | — | All properties + constructor | 6 |
| MetadataEntry | Undocumented | — | — | All properties + methods | 6 |
| MetadataEntryList | Undocumented | — | — | All properties + methods | 6 |
| SObjectMap | Undocumented | — | — | All | 6 |
| SObjectMapping | Undocumented | — | — | All | 6 |
| FileInputWrapper | Undocumented | — | — | All | 6 |

#### Global Classes -- Controllers

| Class | Doc Status | Methods | Documented Methods | Missing | Phase |
|-------|-----------|---------|-------------------|---------|-------|
| CTRL_Renderer | Undocumented | 15 @AuraEnabled | 0 | All methods | 6 |
| CTRL_Settings | Undocumented | 6 @AuraEnabled | 0 | All methods | 6 |
| CTRL_File | Undocumented | 10 methods (incl. @InvocableMethod) | 0 | All methods | 6 |
| CTRL_Mapping | Undocumented | 14 @AuraEnabled | 0 | All methods | 6 |
| CTRL_InteractionDefinition | Undocumented | 11 @AuraEnabled | 0 | All methods | 6 |
| CTRL_ControlSettings | Undocumented | 4 @AuraEnabled | 0 | All methods | 6 |
| CTRL_LightSettings | Undocumented | 4 @AuraEnabled | 0 | All methods | 6 |
| CTRL_RelationshipSettings | Undocumented | 7 @AuraEnabled | 0 | All methods | 6 |
| CTRL_AITakeoff | Undocumented | 3 methods (incl. @InvocableMethod) | 0 | All methods | 6 |
| CTRL_AIVision | Undocumented | 8 methods (incl. @InvocableMethod) | 0 | All methods | 6 |
| CTRL_CustomFurniture | Undocumented | 4 @AuraEnabled | 0 | All methods | 6 |
| CTRL_PolyHaven | Undocumented | 2 @AuraEnabled | 0 | All methods | 6 |
| VirtualTourViewController | Undocumented | 9 @AuraEnabled | 0 | All methods | 6 |
| SwiperController | Undocumented | 3 @AuraEnabled | 0 | All methods | 6 |

#### Global Classes -- Utilities

| Class | Doc Status | Methods | Phase |
|-------|-----------|---------|-------|
| UTIL_InteractionDefinition | Undocumented | 3 @AuraEnabled | 6 |
| UTIL_InteractiveMap | Undocumented | 1 @AuraEnabled | 6 |
| UTIL_OCR | Undocumented | 2 @AuraEnabled | 6 |
| ContentVersionCADConversionHelper | Undocumented | 2 (Future + InvocableMethod) | 6 |
| RenderDrawMeasureProWallAreaHelper | Undocumented | 1 @InvocableMethod | 6 |

#### Global Classes -- VisualEditor Picklists

| Class | Doc Status | Phase |
|-------|-----------|-------|
| CustomExplosion_RecordPicklist | Undocumented | 6 |
| Standalone_DataTable_RecordPicklist | Undocumented | 6 |

#### Public Classes with @AuraEnabled/@InvocableMethod

| Class | Doc Status | Methods | Phase |
|-------|-----------|---------|-------|
| CTRL_AITakeoffSymbolDefs | Undocumented | 3 @AuraEnabled | 6 |
| CTRL_CsvFileUpload | Undocumented | 4 @AuraEnabled | 6 |
| UTIL_Permissions | Undocumented | 5 @AuraEnabled | 6 |
| UTIL_Record | Undocumented | 10 @AuraEnabled | 6 |
| UTIL_Metadata | Undocumented | 4 @AuraEnabled | 6 |
| PageAnnotateController | Undocumented | 5 @AuraEnabled | 6 |
| DynamicRecordQueryController | Undocumented | 2 @AuraEnabled | 6 |
| SpreadsheetImportController | Undocumented | 6 @AuraEnabled | 6 |
| Flow_cadConversionController | Undocumented | 2 @AuraEnabled | 6 |
| FlowJsonWrapper | Undocumented | 1 @InvocableMethod | 6 |
| ObjectGraphBuilder | Undocumented | 1 @AuraEnabled | 6 |
| FilePicker | Undocumented | 2 @AuraEnabled | 6 |
| UserProfileService | Undocumented | 1 @AuraEnabled | 6 |

**Summary:** 6 partially documented (data models with incomplete coverage), 58 undocumented.

---

### Empty Stub Pages

26 empty stub pages exist in GitBook that need content:

| Stub Page | Likely Content Source | Phase |
|-----------|----------------------|-------|
| `diving-deeper/relationships/why-metadata-matters/advanced-metadata-relationships/child-lookup.md` | Relationship architecture | 2 or 6 |
| `diving-deeper/relationships/why-metadata-matters/advanced-metadata-relationships/parent-child-relationships.md` | Relationship architecture | 2 or 6 |
| `usage-scenarios/use-cases/2d/part-finder/parse-pdf-catalogs-to-attach-images.md` | PDF parsing workflow | 4 |
| `usage-scenarios/use-cases/2d/part-finder/base-setup-for-initial-catalog-page/sharing-of-files.md` | File sharing config | 4 |
| `usage-scenarios/use-cases/2d/part-finder/base-setup-for-initial-catalog-page/clone-pages.md` | Page cloning workflow | 4 |
| `usage-scenarios/use-cases/2d/part-finder/create-callouts-for-parts.md` | 2D callout creation | 4 |
| `usage-scenarios/use-cases/2d/part-finder/utilize-ocr-to-highlight-callouts.md` | OCR callout workflow | 4 |
| `usage-scenarios/use-cases/2d/part-finder/optionally-show-inventory-or-availability-based-on-data.md` | Data binding | 4 |
| `usage-scenarios/use-cases/2d/part-finder/create-interactions-for-hover-and-click-actions.md` | Interaction events | 4 |
| `usage-scenarios/use-cases/2d/part-finder/create-a-reusable-connected-datatable.md` | standalone_DataTable | 4 |
| `usage-scenarios/use-cases/2d/custom-2d-app-development-using-salesforce.md` | canvas2D API | 4/7 |
| `usage-scenarios/use-cases/2d/2d-admin-guide-clicks-not-code/show-additional-drawings-with-your-2d-canvas.md` | canvas2D multi-drawing | 4 |
| `usage-scenarios/use-cases/2d/2d-admin-guide-clicks-not-code/use-color-selection-to-add-clickable-regions-to-your-2d-scene.md` | Color selection API | 4 |
| `usage-scenarios/use-cases/3d/admin/examples/asset-management.md` | Digital Twin / Asset | 9 |
| `usage-scenarios/use-cases/3d/admin/examples/product-visualization.md` | 3D product rendering | 5 |
| `usage-scenarios/use-cases/3d/admin/examples/setup-for-3d-visual-configuration-scenarios/conga-cpq.md` | Conga integration | 10 |
| `usage-scenarios/use-cases/3d/admin/examples/setup-for-3d-visual-configuration-scenarios/custom-configuration-scenarios.md` | Custom config patterns | 5 |
| `usage-scenarios/use-cases/3d/admin/examples/3d-product-photography.md` | Screenshot/rendering API | 5 |
| `usage-scenarios/use-cases/3d/admin/examples/renderdraw-templates-for-product-personalization/add-decal-region-to-3d-model.md` | setupDecalRegion_Editor | 5 |
| `usage-scenarios/use-cases/3d/admin/setup-3d-scene/visual-scene-setup/interaction-events.md` | Interaction event config | 3 |
| `usage-scenarios/use-cases/3d/admin/setup-3d-scene/visual-scene-setup/grouping.md` | Component grouping | 5 |
| `usage-scenarios/use-cases/3d/admin/setup-3d-scene/visual-scene-setup/attributes-look-and-feel.md` | Visual attributes | 5 |
| `usage-scenarios/use-cases/3d/admin/setup-3d-scene/configuration/interaction-events/action-items.md` | Action item config | 3 |
| `usage-scenarios/use-cases/3d/admin/setup-3d-scene/configuration/interaction-events/conditions.md` | Condition config | 3 |
| `api-documentation/3d-components-api/events-aura/evt_renderer_mesh_selection_cleared.md` | EVT_Renderer_Mesh_Selection_Cleared | 3 |
| `api-documentation/2d-components-api/2d-scene-director.md` | 2D Scene Director API | 4 |

---

### Secondary Packages

#### PropelPLM Integration

| Item | Type | Doc Status | Doc Page | Phase |
|------|------|-----------|----------|-------|
| itemRevisionAttachmentAnnotation (LWC) | Component | Partially documented | `other-apps/renderdraw-for-propel/` (usage docs exist) | 8 |
| ItemRevisionAttachmentController (Apex) | Controller | Undocumented | — | 8 |

**Summary:** Usage documentation exists in GitBook (`renderdraw-for-propel/` section with 4 pages). API surface (1 LWC, 1 Apex class) is not documented at API reference level. Phase 8 scope is small.

#### AssetDigitalTwin Package

| Item | Type | Doc Status | Doc Page | Phase |
|------|------|-----------|----------|-------|
| AssetDigitalTwinController (7 methods) | Apex | Undocumented | — | 9 |
| AssetDigitalTwin (Aura) | Component | Partially documented | `digital-twin/` section | 9 |
| AutoCompleteController (2 methods) | Apex | Undocumented | — | 9 |
| FlowFindCollection (1 @InvocableMethod) | Apex | Undocumented | — | 9 |
| globalLookup (LWC, 18+ @api) | Component | Undocumented | — | 9 |
| createReport (LWC) | Component | Undocumented | — | 9 |
| parallaxcmp (LWC) | Component | Undocumented | — | 9 |
| spotterConfig (LWC) | Component | Undocumented | — | 9 |
| spotterEmbed (LWC) | Component | Undocumented | — | 9 |
| ChecklistRemoter (5 @RemoteAction) | Apex | Undocumented | — | 9 |
| ServiceChecklistRemoter (5 @RemoteAction) | Apex | Undocumented | — | 9 |
| CustomerInsightsRemoter (5 @RemoteAction) | Apex | Undocumented | — | 9 |
| RevInsightsRemoter (5 @RemoteAction) | Apex | Undocumented | — | 9 |
| CPQB_QuickSelect (Aura) | Component | Undocumented | — | 9 |
| 3 ADT Aura events | Events | Undocumented | — | 9 |

**Note:** Many ADT classes (Remoters, CPQ) may be demo/analytics infrastructure rather than public API. Phase 9 should triage scope.

**Summary:** Digital Twin section exists in GitBook (9 pages, mostly setup guides). API reference for controllers and components is absent. Many items may be demo infrastructure.

---

## Prioritized Action List by Phase

### Phase 2: LMS Message Channels
- Items to document/verify: 5 channels (all currently documented)
- Work: Verify field descriptions match source XML, add publisher/subscriber mapping, note commented-out `sender` field on Record_Selected
- Estimated scope: **Small** (~1 plan, verification only)

### Phase 3: Aura Events
- Items to document: 24 undocumented public events
- Items to classify (likely internal): 0 (23 already classified as internal)
- Items to verify/update: 9 documented events (3 need attribute updates)
- Empty stubs to populate: 1 (EVT_Renderer_Mesh_Selection_Cleared)
- Related stub pages: 3 (interaction-events.md, action-items.md, conditions.md)
- Estimated scope: **Medium** (~2-3 plans)

### Phase 4: LWC Component APIs
- Items to document: 136 components with @api
- Priority components (top 10 by @api count): canvas2D (120), canvas3D (114), interactiveMap (25), utilitiesRDSceneSettings (23), pdfEditor (18), annotateIt (17), pdfEditorDigitalExperience (16), internalLookup (16), setupDecalRegion_Editor (16), popup (12)
- Empty stubs to populate: 12 (2D-related stubs)
- Estimated scope: **Large** (~4-6 plans, many components)

### Phase 5: Aura Component APIs
- Items to document: 7 global-access components + ~10 non-global public components
- Items internal (excluded): 17 Settings_* components
- Priority: AdvancedRenderer (266 attrs), SimpleRenderer (234 attrs), AdvancedLayout (18 attrs), SceneSetup (26 attrs)
- Empty stubs to populate: 5 (3D admin stubs)
- Estimated scope: **Medium** (~2-3 plans)

### Phase 6: Apex Public APIs
- Items to document: 64 classes total (34 global + 30 public with annotations)
- Priority classes: CTRL_Renderer (15 methods), CTRL_Mapping (14 methods), CTRL_InteractionDefinition (11 methods), UTIL_Record (10 methods), CTRL_File (10 methods), CTRL_AIVision (8 methods)
- Data model classes to update: 6 partially documented (CanvasScene, BaseCanvasItem, Canvas, DroppableArea, DropZone, LayoutWall)
- Data model classes to create: 11 undocumented (RenderContext, SnapShot, LayoutDoor, LayoutWindow, DraggableItemTemplate, DroppableAreaTemplate, MetadataEntry, MetadataEntryList, SObjectMap, SObjectMapping, FileInputWrapper)
- ~82 @AuraEnabled methods total + 7 @InvocableMethod
- Estimated scope: **Large** (~4-6 plans)

### Phase 7: Canvas2D/Canvas3D Delta
- Empty stubs to populate from extracted docs: 2 main pages + related stubs
- Extracted docs exist: Canvas2D_API_Documentation.md, Canvas3D_API_Documentation.md
- Work: Diff extracted docs against GitBook pages, merge missing content
- canvas2D: GitBook shows 9 props + 28 methods vs source 21 props + 99 methods
- canvas3D: GitBook shows 31 props + 68 methods vs source 22 props + 92 methods
- Estimated scope: **Medium** (~2-3 plans)

### Phase 8: PropelPLM
- Items to document: 1 LWC component, 1 Apex controller
- Existing coverage: 4 usage/setup pages in GitBook
- Work: Add API reference for component and controller
- Estimated scope: **Small** (~1 plan)

### Phase 9: AssetDigitalTwin
- Items to document: 7 Apex controllers/classes, 5 LWC components, 2 Aura components, 3 Aura events
- Existing coverage: 9 pages in `digital-twin/` section (setup guides)
- Triage needed: Many items may be demo/analytics infrastructure
- Estimated scope: **Medium** (~2 plans, after triage)

## Recommendations

1. **Phase 2 could be fast-tracked** -- all 5 LMS channels are already documented. Phase 2 is verification work, not creation. Consider combining with Phase 3 planning.

2. **Phases 4 and 6 are the largest** -- LWC components (136 items) and Apex classes (64 items) represent the bulk of undocumented API surface. Consider sub-dividing into smaller plans by priority tier.

3. **Phase 7 should leverage extracted docs** -- Canvas2D and Canvas3D have comprehensive extracted documentation that covers most of the gap. Reconciliation rather than creation.

4. **Phase 9 needs triage** -- AssetDigitalTwin contains significant demo/analytics infrastructure (Remoters, Wave template modifiers, CPQ components). Scope the public API surface before documenting.

5. **Settings_* components and events should remain excluded** -- 17 Aura components and 23 Aura events are internal settings admin UI. Documenting them would not serve customers/partners.

6. **Consider combining Phases 8 and 9** -- Both secondary packages are relatively small and follow the same pattern. Could be a single phase.

7. **Empty stub pages are a quick win** -- 26 stub pages and 14 empty index pages already exist in GitBook structure. Populating these with content from source inventories can happen in parallel with API documentation work.
