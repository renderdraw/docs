# Source Inventory: Apex Public APIs

## Main Package Apex Classes

### Summary

| Global | Public (non-test) | Test/Private | Total |
|--------|-------------------|--------------|-------|
| 34     | 30                | 46           | 110   |

**Global classes** include controllers (CTRL_*), data model wrappers (CanvasScene, BaseCanvasItem, etc.), utility classes (UTIL_*), and VisualEditor picklists.

**Public classes** include LWC controllers, data wrappers, helpers, and a query library.

### Annotated Methods Summary

| Annotation | Count | Classes |
|------------|-------|---------|
| @AuraEnabled (on methods) | ~82 | CTRL_Renderer (15), CTRL_Mapping (14), CTRL_InteractionDefinition (11), CTRL_AIVision (7), CTRL_File (9), CTRL_Settings (6), CTRL_RelationshipSettings (7), CTRL_ControlSettings (4), CTRL_LightSettings (4), VirtualTourViewController (8), SwiperController (3), CTRL_CustomFurniture (4), CTRL_PolyHaven (2), CTRL_CsvFileUpload (4), UTIL_Permissions (5), UTIL_Record (10), UTIL_Metadata (4), UTIL_OCR (2), UTIL_InteractionDefinition (3), UTIL_InteractiveMap (1), PageAnnotateController (5), DynamicRecordQueryController (2), SpreadsheetImportController (6), Flow_cadConversionController (2), ObjectGraphBuilder (1), FilePicker (2), UserProfileService (1), CTRL_AITakeoff (2), CTRL_AITakeoffSymbolDefs (3) |
| @InvocableMethod | 7 | CTRL_AITakeoff, CTRL_AIVision, CTRL_File, FlowJsonWrapper, ContentVersionCADConversionHelper, RenderDrawMeasureProWallAreaHelper, Test_CanvasTransform |
| @InvocableVariable | many | CanvasScene, BaseCanvasItem, DroppableArea, DropZone, SnapShot, LayoutWall, LayoutDoor, LayoutWindow, Canvas, MetadataEntry, MetadataEntryList, DraggableItemTemplate, DroppableAreaTemplate, FileInputWrapper, CTRL_AITakeoff, CTRL_AIVision |
| @RemoteAction | 0 | (none) |
| @Http* (REST) | 0 | (none) |
| @Future(Callout=true) | 1 | ContentVersionCADConversionHelper |

---

## Global Classes (34) -- Customer-Facing API

### CTRL_AITakeoff

- **File:** `classes/CTRL_AITakeoff.cls`
- **Sharing:** with sharing
- **Description:** AI-powered takeoff/BOM creation -- creates line items from recognized symbols
- **Inner classes:** `CreateLineItemsInput` (global), `CreateLineItemsOutput` (global)

| Visibility | Annotation | Return Type | Method | Parameters |
|------------|------------|-------------|--------|------------|
| global static | @InvocableMethod | `List<CreateLineItemsOutput>` | `createLineItemsInvocable` | `List<CreateLineItemsInput>` |
| public static | @AuraEnabled | `String` | `createLineItems` | `String bomJson, String targetRecordId, String targetObject, String pricebookId` |
| public static | @AuraEnabled(cacheable=true) | `String` | `getParentRecordType` | `String recordId` |

### CTRL_AIVision

- **File:** `classes/CTRL_AIVision.cls`
- **Sharing:** with sharing
- **Description:** AI vision analysis -- analyzes drawings/images for symbols, extracts BOMs, locates devices
- **Inner classes:** `AnalyzeDrawingInput` (global), `AnalyzeDrawingOutput` (global)

| Visibility | Annotation | Return Type | Method | Parameters |
|------------|------------|-------------|--------|------------|
| global static | @InvocableMethod | `List<AnalyzeDrawingOutput>` | `analyzeDrawingInvocable` | `List<AnalyzeDrawingInput>` |
| public static | @AuraEnabled | `String` | `analyzeImage` | `String contentVersionId, String promptName, String additionalContext` |
| public static | @AuraEnabled | `String` | `analyzeImageDirect` | `String contentVersionId, String apiKey, String model, String promptText, String systemPrompt` |
| public static | @AuraEnabled | `String` | `extractBOM` | `String contentVersionId, String promptName` |
| public static | @AuraEnabled | `String` | `locateDevices` | `String contentVersionId, String promptName, String symbolDefinitionsJson` |
| public static | @AuraEnabled | `String` | `generateBOM` | `String recognitionResultJson, String symbolDefinitionsJson` |
| public static | @AuraEnabled(cacheable=true) | `List<Map<String, String>>` | `getAvailablePrompts` | -- |
| public static | @AuraEnabled(cacheable=true) | `Map<String, String>` | `getActiveProviderInfo` | -- |

### CanvasScene

- **File:** `classes/CanvasScene.cls`
- **Sharing:** with sharing
- **Description:** Top-level scene data model -- holds all canvas items, snapshots, templates, grid settings
- **Inner classes:** `JSONException` (global)

**Properties (all global, @AuraEnabled + @InvocableVariable):**

| Type | Property |
|------|----------|
| `String` | id, name, bgImg |
| `Decimal` | gridSize, seedStartX, seedStartY, maxWidthOfAreas |
| `Boolean` | fixAreasToGrid |
| `List<RDraw.SnapShot>` | snapshots |
| `List<RDraw.BaseCanvasItem>` | placedSelectableShapes, placedNotes, placedDraggableItems, placedLayoutAreas |
| `List<RDraw.DroppableArea>` | placedDroppableAreas |
| `List<RDraw.LayoutWall>` | placedLayoutWalls |
| `List<RDraw.DroppableAreaTemplate>` | droppableAreaTemplates |
| `List<RDraw.DraggableItemTemplate>` | draggableItemTemplates |

| Visibility | Annotation | Return Type | Method | Parameters |
|------------|------------|-------------|--------|------------|
| global | -- | `String` | `toJSON` | -- |
| global static | -- | `RDraw.CanvasScene` | `fromJSON` | `String jsonStr, Boolean replaceContentDocsWithBase64` |

### DraggableItemTemplate

- **File:** `classes/DraggableItemTemplate.cls`
- **Sharing:** (none -- no sharing keyword)
- **Description:** Template definition for draggable items (image, dimensions, position, scale)

**Properties (all global, @AuraEnabled + @InvocableVariable):**

| Type | Property |
|------|----------|
| `String` | imageURL, id, listLabel, name |
| `Decimal` | width, height, scaleX, scaleY, scaleZ, transformX, transformY, transformZ |
| `Boolean` | removable |

| Visibility | Annotation | Return Type | Method | Parameters |
|------------|------------|-------------|--------|------------|
| global | -- | -- | `DraggableItemTemplate()` | (constructor) |

### DroppableAreaTemplate

- **File:** `classes/DroppableAreaTemplate.cls`
- **Sharing:** (none -- no sharing keyword)
- **Description:** Template definition for droppable areas (dimensions, position, padding, sorting)

**Properties (all global, @AuraEnabled + @InvocableVariable):**

| Type | Property |
|------|----------|
| `String` | imageURL, name, id, listLabel, itemsAlign |
| `Decimal` | width, height, depth, x, y, z, padLeft, padTop, padRight, padBottom |
| `Boolean` | allowItemOverlap, enableSorting, draggable, removable |

| Visibility | Annotation | Return Type | Method | Parameters |
|------------|------------|-------------|--------|------------|
| global | -- | -- | `DroppableAreaTemplate()` | (constructor) |

### MetadataEntry

- **File:** `classes/MetadataEntry.cls`
- **Sharing:** (none -- no sharing keyword)
- **Description:** Key-value metadata container with typed value support (String, Integer, Boolean, Decimal)
- **Inner enum:** `MetadataValueType` (public) -- STRING_TYPE, INTEGER_TYPE, BOOLEAN_TYPE, DECIMAL_TYPE

**Properties (all global, @AuraEnabled + @InvocableVariable where noted):**

| Type | Property | InvocableVariable |
|------|----------|--------------------|
| `String` | key, name, stringValue, valueType | yes (key, name, stringValue, valueType) |
| `Object` | value (getter/setter with type detection) | -- |
| `Integer` | intValue | yes |
| `Boolean` | boolValue | yes |
| `Decimal` | decimalValue | yes |

| Visibility | Annotation | Return Type | Method | Parameters |
|------------|------------|-------------|--------|------------|
| global | -- | -- | `MetadataEntry()` | (constructor) |
| global | -- | `void` | `setValue` | `Object value` |
| global static | -- | `RDraw.MetadataEntry` | `createMetadataEntry` | `String key, Object value` |
| public | -- | `MetadataValueType` | `getValueType` | -- |

### MetadataEntryList (MetadataList)

- **File:** `classes/MetadataEntryList.cls`
- **Sharing:** (none -- no sharing keyword)
- **Description:** Named collection of MetadataEntry items with utility methods

**Properties (all global, @AuraEnabled + @InvocableVariable):**

| Type | Property |
|------|----------|
| `String` | id |
| `List<MetadataEntry>` | entries |

| Visibility | Annotation | Return Type | Method | Parameters |
|------------|------------|-------------|--------|------------|
| global | -- | -- | `MetadataEntryList()` | (constructor) |
| global | -- | -- | `MetadataEntryList(String id)` | (constructor) |
| global | -- | -- | `MetadataEntryList(String id, List<MetadataEntry> entries)` | (constructor) |
| global static | -- | `MetadataEntryList` | `createMetadataEntryList` | `String id, List<MetadataEntry> entries` |
| global | -- | `void` | `addEntry` | `MetadataEntry entry` |
| global | -- | `void` | `addEntries` | `List<MetadataEntry> entries` |
| global | -- | `MetadataEntry` | `getEntryByName` | `String name` |
| global static | @AuraEnabled | `MetadataEntryList` | `addEntryToList` | `MetadataEntryList metadataList, MetadataEntry entry` |
| global static | @AuraEnabled | `MetadataEntryList` | `addEntriesToList` | `MetadataEntryList metadataList, List<MetadataEntry> entries` |
| global static | @AuraEnabled | `MetadataEntry` | `findEntryByName` | `MetadataEntryList metadataList, String name` |

### VirtualTourViewController

- **File:** `classes/VirtualTourViewController.cls`
- **Sharing:** with sharing
- **Description:** Controller for virtual tour / 360-degree walkthrough viewer
- **Inner classes:** `ImageMapWrapper` (global), `RelatedImagesWrapper` (global), `Image` (global), `Hotspot` (global)

| Visibility | Annotation | Return Type | Method | Parameters |
|------------|------------|-------------|--------|------------|
| public static | @AuraEnabled | `Boolean` | `checkPermission` | `String permissionName` |
| public static | @AuraEnabled | `Boolean` | `getIsWalkThroughAdminEnabled` | -- |
| public static | @AuraEnabled | `Boolean` | `getIsWalkThroughEnabled` | -- |
| public static | @AuraEnabled(cacheable=true) | `Map<String, Object>` | `getRecordTourSettings` | `Id recordId` |
| public static | @AuraEnabled | `void` | `updateVirtualTourSettings` | `Id recordId, String settings` |
| public static | @AuraEnabled(cacheable=true) | `List<ContentVersion>` | `getAllRelatedImages` | `String recordId` |
| public static | @AuraEnabled(cacheable=true) | `ContentVersion` | `getContentVersionId` | `Id contentDocumentId` |
| public static | @AuraEnabled(cacheable=true) | `String` | `getBase64` | `String docId` |
| public static | @AuraEnabled(cacheable=true) | `Map<String, ImageMapWrapper>` | `getImageMapList` | `Id recordId` |

---

### Additional Global Classes -- Controllers

#### CTRL_Renderer

- **File:** `classes/CTRL_Renderer.cls`
- **Sharing:** with sharing
- **Description:** Core rendering controller -- scene setup, context, file handling
- **Inner classes:** `FieldAccessException` (public)

| Visibility | Annotation | Return Type | Method | Parameters |
|------------|------------|-------------|--------|------------|
| global static | @AuraEnabled | `List<String>` | `getAllowedFileExtensions` | -- |
| public static | @AuraEnabled | `UTIL_Permissions.RDPermissions` | `getRenderDrawRelatedPermissions` | -- |
| public static | @AuraEnabled(cacheable=false) | `ContentVersion` | `getLatestContentVersionForContentDocumentId` | `String contentDocumentId` |
| public static | @AuraEnabled | `ContentVersion` | `getContentVersionForId` | `String contentVersionId` |
| public static | @AuraEnabled | `Boolean` | `checkForValidFileExtensions` | `String extension` |
| public static | @AuraEnabled | `RenderContext` | `getRenderContextForSceneSetup` | `String recordId` |
| global static | @AuraEnabled | `Boolean` | `updateSceneSetup` | `String recordId, String objectName, String fieldName, String settings` |
| global static | @AuraEnabled | `RenderContext` | `getRenderContext` | `String recordId` |
| global static | @AuraEnabled | `RenderContext.SceneSettings` | `getSceneSettings` | `String recordId, Boolean get2D` |
| global static | @AuraEnabled | `RenderContext.SceneSettings` | `getSceneSettings3D` | `Map<String, String> pageParams` |
| global static | @AuraEnabled | `String` | `getDynamicSceneSettings` | `String objectName, String fieldName, String recordId` |
| public static | @AuraEnabled | `String` | `getSerializedRenderContext` | `String recordId` |
| public static | @AuraEnabled | `String` | `findObjectNameFromRecordIdPrefix` | `String recordId` |
| public static | @AuraEnabled(cacheable=true) | -- | (additional methods) | -- |

#### CTRL_Settings

- **File:** `classes/CTRL_Settings.cls`
- **Sharing:** with sharing
- **Description:** RenderDraw settings CRUD controller (custom metadata)
- **Inner classes:** `VM_RenderDrawSettings` (public), `SettingFieldAccessException` (public)

| Visibility | Annotation | Return Type | Method | Parameters |
|------------|------------|-------------|--------|------------|
| global static | @AuraEnabled | `String` | `getRenderDrawSettings` | -- |
| global static | @AuraEnabled | `String` | `getRenderDrawSettingsById` | `String id` |
| global static | @AuraEnabled | `String` | `getCreateViewModel` | -- |
| global static | @AuraEnabled | `String` | `getRelatedControlModel` | `String model` |
| global static | @AuraEnabled | `String` | `getRelatedLightModel` | `String model` |
| global static | @AuraEnabled | `String` | `createRenderDrawSettings` | `String model` |

#### CTRL_File

- **File:** `classes/CTRL_File.cls`
- **Sharing:** with sharing
- **Description:** File management -- upload, retrieve, associate files to records, CAD conversion logging

| Visibility | Annotation | Return Type | Method | Parameters |
|------------|------------|-------------|--------|------------|
| public static | @AuraEnabled | `ContentVersion` | `getLatestContentVersionFromContentVersionId` | `String contentVersionId` |
| public static | @AuraEnabled | `ContentVersion` | `getLatestContentVersionFromContentDocumentId` | `String contentDocumentId` |
| public static | @AuraEnabled | `List<ContentVersion>` | `getLatestContentVersionsForRecordId` | `String recordId` |
| global static | @InvocableMethod | `List<String>` | `invokeSaveFileAndAssociate` | `List<FileInputWrapper> fileDataList` |
| global static | @AuraEnabled | `String` | `getBase64ImageFromContent` | `String contentId` |
| global static | @AuraEnabled | `String` | `saveFileAndAssociateToRecord` | `String fileData, String filename, String fileExtension, String title, String recordId` |
| public static | @AuraEnabled | `String` | `getContentDocumentIdFromContentVersionId` | `String contentVersionId` |
| public static | @AuraEnabled | `String` | `getTitleFromContentVersionId` | `String contentVersionId` |
| public static | @AuraEnabled | `String` | `updateRecords` | `List<SObject> sObjects` |
| public static | @AuraEnabled | `void` | `createConversionLog` | `String filename, String originalFormat, String destinationFormat, Boolean success` |

#### CTRL_Mapping

- **File:** `classes/CTRL_Mapping.cls`
- **Sharing:** with sharing
- **Description:** Object/field mapping -- dynamic queries, schema introspection, mesh mapping

| Visibility | Annotation | Return Type | Method | Parameters |
|------------|------------|-------------|--------|------------|
| public static | @AuraEnabled | `sObject` | `getSObjectForSelection` | `String recordId, String value` |
| public static | @AuraEnabled | `sObject` | `dynamicallyFetchObjectForParam` | `String sObj, String field, String value, Boolean exactMatch` |
| public static | @AuraEnabled(cacheable=true) | `List<ListSelection>` | `getSalesforceObjects` | -- |
| public static | @AuraEnabled(cacheable=true) | `List<ListSelection>` | `getObjectLabelsByApiNames` | `List<String> objectApiNames` |
| public static | @AuraEnabled | `List<DynamicHierarchyDataWrapper>` | `getDataForHierarchicalDataSource` | `DynamicQueryHierarchicalDataSource dataSource` |
| public static | @AuraEnabled(cacheable=false) | `List<ListSelection>` | `getFieldListSelectionsForSalesforceObjectName` | `String salesforceObject` |
| public static | @AuraEnabled(cacheable=true) | `List<ListSelection>` | `getFieldListSelectionsForSalesforceObject` | `ListSelection salesforceObject` |
| public static | @AuraEnabled | `List<Map<String, String>>` | `getParentReferences` | `String salesforceObject` |
| public static | @AuraEnabled | `String` | `getIconName` | `String sObjectName` |
| public static | @AuraEnabled | `List<String>` | `getLightningComponentsInOrg` | -- |
| global static | @AuraEnabled | `sObject` | `getFieldValuesForObject` | `String id, List<String> fields` |
| public static | @AuraEnabled | `Map<String, String>` | `getMeshMappingContext` | `String recordId` |
| public static | @AuraEnabled | `String` | `bulkUpdateFieldForMeshMapping` | `(multiple params)` |
| public static | @AuraEnabled(cacheable=true) | `List<Map<String, String>>` | `getPicklistValuesForField` | `String objectName, String fieldName` |
| public static | @AuraEnabled(cacheable=true) | `List<Map<String, Object>>` | `getFieldMetadataEnriched` | `String objectName` |

#### CTRL_InteractionDefinition

- **File:** `classes/CTRL_InteractionDefinition.cls`
- **Sharing:** with sharing
- **Description:** CRUD controller for Interaction Definition records

| Visibility | Annotation | Return Type | Method | Parameters |
|------------|------------|-------------|--------|------------|
| public static | @AuraEnabled | `List<Interaction_Definition__c>` | `getInteractionsForObjectType` | `String ObjectType` |
| public static | @AuraEnabled | `List<Interaction_Definition__c>` | `getInteractionsForInteractionType` | `String interactionType` |
| public static | @AuraEnabled | `List<Interaction_Definition__c>` | `getInteractionsForRecord` | `String recordId` |
| public static | @AuraEnabled | `Interaction_Definition__c` | `getInteractionByTypeAndObjectTypeAndName` | `String interactionType, String objectType, String name` |
| public static | @AuraEnabled | `Interaction_Definition__c` | `getInteractionByTypeAndName` | `String interactionType, String name` |
| public static | @AuraEnabled | `Interaction_Definition__c` | `createOrUpdateInteractionEventSettingsField` | `Interaction_Definition__c idef` |
| public static | @AuraEnabled | `List<Interaction_Definition__c>` | `getInteractionByTypeAndObjectType` | `String interactionType, String objectType` |
| public static | @AuraEnabled | `Interaction_Definition__c` | `getInteractionById` | `String recordId` |
| public static | @AuraEnabled(cacheable=true) | `SObject` | `getRecordById` | `String objectApiName, Id recordId, String fieldNames` |
| public static | @AuraEnabled | `Boolean` | `updateValueInDesignTemplate` | `Id templateId, String nodeId, String updatedValue` |
| public static | @AuraEnabled | `void` | `deleteInteractionDefinition` | `String recordId` |

#### CTRL_ControlSettings

- **File:** `classes/CTRL_ControlSettings.cls`
- **Sharing:** with sharing
- **Description:** Control settings CRUD controller (custom metadata)

| Visibility | Annotation | Return Type | Method | Parameters |
|------------|------------|-------------|--------|------------|
| global static | @AuraEnabled | `String` | `getRenderDrawControlSettings` | -- |
| global static | @AuraEnabled | `String` | `getSerializedRenderDrawControlSettingsById` | `String id` |
| global static | @AuraEnabled | `String` | `getCreateViewModel` | -- |
| global static | @AuraEnabled | `String` | `createControlSettings` | `String model` |

#### CTRL_LightSettings

- **File:** `classes/CTRL_LightSettings.cls`
- **Sharing:** with sharing
- **Description:** Light settings CRUD controller (custom metadata)

| Visibility | Annotation | Return Type | Method | Parameters |
|------------|------------|-------------|--------|------------|
| global static | @AuraEnabled | `String` | `getRenderDrawLightingSettings` | -- |
| global static | @AuraEnabled | `String` | `getSerializedRenderDrawLightingSettingsById` | `String id` |
| global static | @AuraEnabled | `String` | `getCreateViewModel` | -- |
| global static | @AuraEnabled | `String` | `createLightSettings` | `String model` |

#### CTRL_RelationshipSettings

- **File:** `classes/CTRL_RelationshipSettings.cls`
- **Sharing:** with sharing
- **Description:** Relationship settings CRUD controller (custom metadata)

| Visibility | Annotation | Return Type | Method | Parameters |
|------------|------------|-------------|--------|------------|
| global static | @AuraEnabled | `String` | `getCreateViewModel` | -- |
| global static | @AuraEnabled | `String` | `getAllRelationshipSettings` | -- |
| global static | @AuraEnabled | `String` | `getRelationshipSettings` | `String id` |
| global static | @AuraEnabled | `RenderDraw_Relationship__mdt` | `getRelationshipMetadataByObjectName` | `String objectName` |
| global static | @AuraEnabled | `String` | `createNewRelationship` | `String model` |
| public static | @AuraEnabled | `String` | `getObjectFieldsForObject` | `String technicalObjectName` |
| public static | @AuraEnabled | `String` | `getRelatedRenderDrawModel` | `String model` |

#### SwiperController

- **File:** `classes/SwiperController.cls`
- **Sharing:** with sharing
- **Description:** Controller for Swiper (image gallery/slider) component

| Visibility | Annotation | Return Type | Method | Parameters |
|------------|------------|-------------|--------|------------|
| public static | @AuraEnabled | `Boolean` | `getIsSwiperAdmin` | -- |
| public static | @AuraEnabled | `SwiperWrapper` | `getSwiperWrapper` | `String recordId` |
| public static | @AuraEnabled | `void` | `updateSwiperSetting` | `Id recordId, String settingJSON` |

#### CTRL_CustomFurniture

- **File:** `classes/CTRL_CustomFurniture.cls`
- **Sharing:** public with sharing
- **Description:** Custom furniture catalog for 3D scenes -- configurable SObject-backed model sources

| Visibility | Annotation | Return Type | Method | Parameters |
|------------|------------|-------------|--------|------------|
| public static | @AuraEnabled(cacheable=true) | `List<FieldOption>` | `getEligibleFields` | `String objectApiName` |
| public static | @AuraEnabled(cacheable=false) | `List<FurnitureItem>` | `getCustomFurnitureCatalog` | `String configJson` |
| public static | @AuraEnabled(cacheable=false) | `String` | `resolveContentDownloadUrl` | `Id contentId` |
| public static | @AuraEnabled(cacheable=false) | `String` | `resolveRecordModelUrl` | `Id recordId, String configJson` |

#### CTRL_PolyHaven

- **File:** `classes/CTRL_PolyHaven.cls`
- **Sharing:** public with sharing
- **Description:** Server-side proxy for Poly Haven HDRI API (environment lighting)

| Visibility | Annotation | Return Type | Method | Parameters |
|------------|------------|-------------|--------|------------|
| public static | @AuraEnabled(cacheable=true) | `String` | `listHdris` | -- |
| public static | @AuraEnabled(cacheable=true) | `String` | `getHdriFiles` | `String slug` |

---

### Additional Global Classes -- Utilities

#### UTIL_InteractionDefinition

- **File:** `classes/UTIL_InteractionDefinition.cls`
- **Sharing:** with sharing
- **Description:** Utility for Interaction Definition CRUD (global methods)

| Visibility | Annotation | Return Type | Method | Parameters |
|------------|------------|-------------|--------|------------|
| global static | @AuraEnabled | `List<Interaction_Definition__c>` | `getAllInteractionDefinitionsByType` | `String type, String relatedRecordId` |
| global static | @AuraEnabled | `Interaction_Definition__c` | `updateOrInsertInteractionDefinition` | `Interaction_Definition__c interactionDefinition` |
| global static | @AuraEnabled | `Boolean` | `deleteInteractionDefinition` | `String recordId, String relatedRecordId` |

#### UTIL_InteractiveMap

- **File:** `classes/UTIL_InteractiveMap.cls`
- **Sharing:** with sharing
- **Description:** Interactive map geocoding utility (Azure Maps batch geocode)

| Visibility | Annotation | Return Type | Method | Parameters |
|------------|------------|-------------|--------|------------|
| global static | @AuraEnabled | `String` | `getAddressesGeocodes` | `String body` |

#### UTIL_OCR

- **File:** `classes/UTIL_OCR.cls`
- **Sharing:** with sharing
- **Description:** Azure OCR callout utility

| Visibility | Annotation | Return Type | Method | Parameters |
|------------|------------|-------------|--------|------------|
| global static | @AuraEnabled | `String` | `callAzureOCR` | `String url, Map<String, String> headers, String body` |
| public static | @AuraEnabled | `List<RenderDraw_OCR_Setting__mdt>` | `getRenderDrawOCRSettings` | -- |

#### ContentVersionCADConversionHelper

- **File:** `classes/ContentVersionCADConversionHelper.cls`
- **Sharing:** with sharing
- **Description:** CAD file format conversion via external callout

| Visibility | Annotation | Return Type | Method | Parameters |
|------------|------------|-------------|--------|------------|
| global static | @Future(Callout=true) | `void` | `runCadConversion` | `Set<Id> contentVersionIds` |
| global static | @InvocableMethod | `void` | `runCadConversionFromFlow` | `List<Id> contentVersionIds` |

#### RenderDrawMeasureProWallAreaHelper

- **File:** `classes/RenderDrawMeasureProWallAreaHelper.cls`
- **Sharing:** with sharing
- **Description:** Calculates area enclosed by walls (for floor plan measurement)

| Visibility | Annotation | Return Type | Method | Parameters |
|------------|------------|-------------|--------|------------|
| global static | @InvocableMethod | `List<Decimal>` | `calculateAreaFromWalls` | `List<List<RDraw.LayoutWall>> wallLists` |

---

### Additional Global Classes -- Data Models

#### BaseCanvasItem

- **File:** `classes/BaseCanvasItem.cls`
- **Sharing:** with sharing
- **Modifiers:** global virtual
- **Description:** Base class for all canvas items (shapes, notes, draggable items, layout areas)

**Properties (all global, @AuraEnabled + @InvocableVariable):**
`id`, `name`, `recordId`, `value`, `x`, `y`, `length`, `width`, `height`, `rotation`, `points` (List\<double\>), `templateId`, `metadata` (List\<MetadataEntry\>)

#### Canvas

- **File:** `classes/Canvas.cls`
- **Sharing:** with sharing
- **Description:** Legacy canvas wrapper with nested inner classes (DroppableArea, DropZone, DraggableItem, LayoutArea, BaseCanvasItem, etc.)

**Properties (all global, @AuraEnabled + @InvocableVariable):**
`id`, `name`, `backgroundImageURL`, `placedSelectableShapes`, `placedDroppableAreas`, `placedDraggableItems`, `placedLayoutAreas`, `placedLayoutWalls`, `droppableAreas`, `draggableItems`, `layoutAreas`

#### RenderContext

- **File:** `classes/RenderContext.cls`
- **Sharing:** with sharing
- **Description:** Rendering context -- holds settings, URLs, file paths, relationship metadata

**Properties (all global, @AuraEnabled):**
`UnderlyingObjectId`, `UnderlyingObjectName`, `Relationship`, `Light`, `RenderDraw`, `Control`, `RenderBaseURL`, `RenderRelativePath`, `HasOverrideRelativePath`, `RenderFile`, `RenderFileWithoutPath`, `FullRenderPathWithoutFile`, `RenderResourcePath`, `HasParentSettings`, `HasSceneSettings`, `Messages`, etc.

**Inner classes:** `SceneSettings` (public), `RenderContextMessage` (public)

#### DroppableArea

- **File:** `classes/DroppableArea.cls`
- **Sharing:** with sharing
- **Extends:** BaseCanvasItem

**Properties:** `imageURL`, `sortingEnabled`, `sortingDirection`, `dropZones` (List\<DropZone\>), `draggableItems` (List\<BaseCanvasItem\>)

#### DropZone

- **File:** `classes/DropZone.cls`
- **Sharing:** with sharing
- **Extends:** BaseCanvasItem

**Properties:** `placedDraggableItem` (BaseCanvasItem)

#### SnapShot

- **File:** `classes/SnapShot.cls`
- **Sharing:** with sharing

**Properties:** `rawData`, `type`, `formattedImage`

#### LayoutWall

- **File:** `classes/LayoutWall.cls`
- **Sharing:** with sharing
- **Modifiers:** global virtual

**Properties:** `id`, `x1`, `y1`, `x2`, `y2`, `height`, `windows` (List\<LayoutWindow\>), `doors` (List\<LayoutDoor\>), `points` (List\<double\>)

#### LayoutDoor

- **File:** `classes/LayoutDoor.cls`
- **Sharing:** with sharing
- **Modifiers:** global virtual

**Properties:** `doorId`, `x`, `y`, `d`, `height`, `width`, `rot`, `name`, `wallId`

#### LayoutWindow

- **File:** `classes/LayoutWindow.cls`
- **Sharing:** with sharing
- **Modifiers:** global virtual

**Properties:** `windowId`, `x`, `y`, `width`, `height`, `rot`, `top`, `name`, `wallId`

#### SObjectMap

- **File:** `classes/SObjectMap.cls`
- **Sharing:** with sharing

**Properties:** `mappedObjects` (List\<SObjectMapping\>)

#### SObjectMapping

- **File:** `classes/SObjectMapping.cls`
- **Sharing:** with sharing

**Properties:** `baseObjectId`, `relatedObjectId`

#### FileInputWrapper

- **File:** `classes/FileInputWrapper.cls`
- **Sharing:** with sharing
- **Description:** Invocable input for file save operations

**Properties (all global, @InvocableVariable):** `fileData`, `filename`, `fileExtension`, `title`, `recordId`

---

### Additional Global Classes -- VisualEditor Picklists

#### CustomExplosion_RecordPicklist

- **File:** `classes/CustomExplosion_RecordPicklist.cls`
- **Sharing:** with sharing
- **Extends:** `VisualEditor.DynamicPickList`
- **Methods:** `getDefaultValue()`, `getValues()`

#### Standalone_DataTable_RecordPicklist

- **File:** `classes/Standalone_DataTable_RecordPicklist.cls`
- **Sharing:** with sharing
- **Extends:** `VisualEditor.DynamicPickList`
- **Methods:** `getDefaultValue()`, `getValues()`

---

## Public Classes with @AuraEnabled/@InvocableMethod

### CTRL_AITakeoffSymbolDefs

- **File:** `classes/CTRL_AITakeoffSymbolDefs.cls`
- **Sharing:** public with sharing
- **Description:** CRUD for AI symbol definition prompts (custom metadata)

| Visibility | Annotation | Return Type | Method | Parameters |
|------------|------------|-------------|--------|------------|
| public static | @AuraEnabled(cacheable=true) | `String` | `getSymbolDefinitions` | `String promptName` |
| public static | @AuraEnabled(cacheable=true) | `List<Map<String, String>>` | `getPromptSummaries` | -- |
| public static | @AuraEnabled | `String` | `saveSymbolDefinitions` | `String promptName, String symbolDefinitionsJson` |

### CTRL_CsvFileUpload

- **File:** `classes/CTRL_CsvFileUpload.cls`
- **Sharing:** public with sharing
- **Description:** CSV file upload and import controller

| Visibility | Annotation | Return Type | Method | Parameters |
|------------|------------|-------------|--------|------------|
| public static | @AuraEnabled(Cacheable=true) | `String` | `getFieldList` | `ListSelection obj` |
| public static | @AuraEnabled | `List<SObject>` | `getDuplicateRecords` | `String objName, String uniqueColFieldName, List<String> uniqueFieldValues` |
| public static | @AuraEnabled | `String` | `upsertDataInSF` | `List<SObject> sObjects, Boolean isUpdate` |
| public static | @AuraEnabled(Cacheable=true) | `List<SObject>` | `getParentRecordsNotInData` | `String parentFieldMap, String objName, List<String> parentIdentifierNotInData` |

### UTIL_Permissions

- **File:** `classes/UTIL_Permissions.cls`
- **Sharing:** public with sharing
- **Description:** Feature permission checks for RenderDraw license enforcement

| Visibility | Annotation | Return Type | Method | Parameters |
|------------|------------|-------------|--------|------------|
| public static | @AuraEnabled(cacheable=false) | `RDPermissions` | `getRenderDrawRelatedPermissions` | -- |
| public static | @AuraEnabled | `Map<String, String>` | `checkFeaturesAvailable` | -- |
| public static | @AuraEnabled | `String` | `getCurrentSessionId` | -- |
| public static | @AuraEnabled(cacheable=true) | `String` | `getOrgEdition` | -- |
| public static | @AuraEnabled | `String` | `getCurrentConversionKey` | -- |

### UTIL_Record

- **File:** `classes/UTIL_Record.cls`
- **Sharing:** public with sharing
- **Description:** Generic record search, lookup, and SOQL utilities

| Visibility | Annotation | Return Type | Method | Parameters |
|------------|------------|-------------|--------|------------|
| public static | @AuraEnabled | `RecordLookupSearchResult` | `searchWithUniqueField` | `String uniqueField, String uniqueFieldValue, String objectApiName` |
| public static | @AuraEnabled(Cacheable=true) | `List<RecordLookupSearchResult>` | `search` | `String searchTerm, List<String> selectedIds, String objectApiName, String customNameField` |
| public static | @AuraEnabled(Cacheable=true) | `List<RecordLookupSearchResult>` | `searchByTerms` | `List<String> searchTerms, String searchField, String objectApiName` |
| public static | @AuraEnabled(Cacheable=true) | `List<RecordLookupSearchResult>` | `getRecentlyViewed` | `String objectApiName` |
| public static | @AuraEnabled | `String` | `getTechnicalObjectNameFromId` | `String recordId` |
| public static | @AuraEnabled(Cacheable=true) | `List<RecordLookupSearchResult>` | `getObjectOptions` | `String searchTerm` |
| public static | @AuraEnabled(cacheable=true) | `List<sObject>` | `lookUp` | `String searchTerm, String objectName, String filters, String recordId, String fields` |
| public static | @AuraEnabled(cacheable=true) | `List<ListSelection>` | `getListOfLightningFlows` | -- |
| public static | @AuraEnabled | `String` | `getSessionId` | -- |
| public static | @AuraEnabled(Cacheable=true) | `List<RecordLookupSearchResult>` | `searchWithSearchTermAndUniqueField` | `(multiple params)` |

### UTIL_Metadata

- **File:** `classes/UTIL_Metadata.cls`
- **Sharing:** public with sharing
- **Description:** Static resource URL resolution, metadata deployment, digital experience URL

| Visibility | Annotation | Return Type | Method | Parameters |
|------------|------------|-------------|--------|------------|
| public static | @AuraEnabled | `String` | `getStaticResourceURLByName` | `String resourceName` |
| public static | @AuraEnabled | `List<String>` | `getListOfStaticResourceURLByName` | `List<String> resourceNames` |
| public static | @AuraEnabled(Cacheable=true) | `String` | `getDigitalExperienceURL` | -- |
| public static | @AuraEnabled(cacheable=true) | `List<FontStaticResource>` | `getCustomFontStaticResources` | -- |

### PageAnnotateController

- **File:** `classes/PageAnnotateController.cls`
- **Sharing:** public with sharing
- **Description:** Page/document annotation controller -- file retrieval and Chatter posting

| Visibility | Annotation | Return Type | Method | Parameters |
|------------|------------|-------------|--------|------------|
| public static | @AuraEnabled | `ContentVersion` | `getContentVersionFromContentDocumentId` | `String cdId` |
| public static | @AuraEnabled | `ContentVersion` | `getCurrentContentVersion` | `String cvId` |
| public static | @AuraEnabled | `ContentVersion` | `getCurrentContentVersionByDocId` | `String docId` |
| public static | @AuraEnabled(Cacheable=false) | `List<FileWrapper>` | `getRelatedFiles` | `String parentRecordId` |
| public static | @AuraEnabled | `void` | `createChatterPost` | `String recordId, String body` |

### DynamicRecordQueryController

- **File:** `classes/DynamicRecordQueryController.cls`
- **Sharing:** public with sharing
- **Description:** Dynamic SOQL query execution from JSON model

| Visibility | Annotation | Return Type | Method | Parameters |
|------------|------------|-------------|--------|------------|
| public static | @AuraEnabled | `List<SObject>` | `getRecords` | `String model` |
| public static | @AuraEnabled | `Map<String, List<SObject>>` | `getGroupedRecords` | `String model` |

### SpreadsheetImportController

- **File:** `classes/SpreadsheetImportController.cls`
- **Sharing:** public with sharing
- **Description:** Spreadsheet import/export -- bulk record CRUD operations

| Visibility | Annotation | Return Type | Method | Parameters |
|------------|------------|-------------|--------|------------|
| public static | @AuraEnabled | `ImportResult` | `importRecords` | `String objectName, List<Map<String, Object>> records, Map<String, String> fieldMappings` |
| public static | @AuraEnabled | `ImportResult` | `updateRecords` | `String objectName, List<Map<String, Object>> records` |
| public static | @AuraEnabled | `ImportResult` | `deleteRecords` | `String objectName, List<String> recordIds` |
| public static | @AuraEnabled | `List<Map<String, Object>>` | `queryRecords` | `String objectName, List<String> fieldNames, Integer maxRecords` |
| public static | @AuraEnabled | `List<Map<String, Object>>` | `searchRecords` | `String objectName, String searchTerm, List<String> returnFields, Integer maxResults` |
| public static | @AuraEnabled(cacheable=true) | `List<RDraw.ListSelection>` | `getParentReferences` | `String objectName` |

### Flow_cadConversionController

- **File:** `classes/Flow_cadConversionController.cls`
- **Sharing:** public with sharing
- **Description:** CAD conversion controller for Flow screen components

| Visibility | Annotation | Return Type | Method | Parameters |
|------------|------------|-------------|--------|------------|
| public static | @AuraEnabled | `List<ContentVersion>` | `getFilesToConvert` | `String recordId` |
| public static | @AuraEnabled | `List<ContentVersion>` | `getContentVersionDetailsForContentIds` | `List<String> ids` |

### FlowJsonWrapper

- **File:** `classes/FlowJsonWrapper.cls`
- **Sharing:** public with sharing
- **Description:** Converts CanvasScene to JSON string for use in Flows

| Visibility | Annotation | Return Type | Method | Parameters |
|------------|------------|-------------|--------|------------|
| public static | @InvocableMethod | `List<String>` | `convertCanvasSceneToJson` | `List<Request> requests` |

### ObjectGraphBuilder

- **File:** `classes/ObjectGraphBuilder.cls`
- **Sharing:** public with sharing
- **Description:** Builds dependency graph of SObjects for ordered operations

| Visibility | Annotation | Return Type | Method | Parameters |
|------------|------------|-------------|--------|------------|
| public static | @AuraEnabled | `ObjectGraphResult` | `buildObjectGraph` | `List<String> objectNames` |

### FilePicker

- **File:** `classes/FilePicker.cls`
- **Sharing:** public with sharing
- **Description:** Content document picker with security checks

| Visibility | Annotation | Return Type | Method | Parameters |
|------------|------------|-------------|--------|------------|
| public static | @AuraEnabled(cacheable=true) | `ContentDocument` | `getContentDocument` | `Id contentDocumentId` |
| public static | @AuraEnabled(cacheable=false) | `List<ContentDocument>` | `getDocuments` | `Id relatedToId, List<String> formats, String filter, Boolean globalFileAccessOnSearch` |

### UserProfileService

- **File:** `classes/UserProfileService.cls`
- **Sharing:** public with sharing
- **Description:** Fetches user profile data

| Visibility | Annotation | Return Type | Method | Parameters |
|------------|------------|-------------|--------|------------|
| public static | @AuraEnabled(cacheable=true) | `User` | `fetchUserProfile` | `String id` |

### CTRL_InteractiveMap

- **File:** `classes/CTRL_InteractiveMap.cls`
- **Sharing:** public with sharing
- **Description:** Interactive map controller (all @AuraEnabled methods currently commented out)
- **Note:** No active annotated methods

---

## Public Classes (no annotated methods -- list only)

CustomMetadataCallback, DynamicHierarchyDataWrapper, DynamicQueryCondition, DynamicQueryDataSource, DynamicQueryHierarchicalDataSource, DynamicQuerySubQueryDataSource, FileGlobalSearch, HttpFormBuilder, ListSelection, LookupSearchResult, ObjectGraphBuilder (inner classes), Query, QuerySearch, RecordLookupSearchResult, UTIL_SwiperRelationship, UTIL_VirtualTourRelationship

### Interfaces

- **ISettingsController** -- `getAllSerializedSettings()`, `getSerializedSettingsById(String)`, `getSerializedCreateViewModel()`

### Test Classes (46 -- skipped)

FilePickerTest, LookupSearchResultTest, MetadataEntryListTest, MetadataEntryTest, QuerySearchTest, QueryTest, Test_CTRL_AITakeoff, Test_CTRL_AITakeoffSymbolDefs, Test_CTRL_AIVision, Test_CTRL_ControlSettings, Test_CTRL_CsvFileUpload, Test_CTRL_CustomFurniture, Test_CTRL_File, Test_CTRL_InteractionDefinition, Test_CTRL_LightSettings, Test_CTRL_Mapping, Test_CTRL_PolyHaven, Test_CTRL_RelationshipSettings, Test_CTRL_Renderer, Test_CTRL_Settings, Test_CanvasScene, Test_CanvasTransform, Test_ContentVersionCADConversionHelper, Test_CoverageFoundations, Test_DynamicQueryObjects, Test_DynamicRecordQueryController, Test_Flow_cadConversionController, Test_ListSelection, Test_ObjectGraphBuilder, Test_PageAnnotateController, Test_RecordLookupSearchResult, Test_RenderDrawMeasureProWallAreaHelper, Test_SpreadsheetImportController, Test_SwiperController, Test_UTIL_InteractionDefinition, Test_UTIL_Metadata, Test_UTIL_Permissions, Test_UTIL_Record, Test_UTIL_VirtualTourRelationship, Test_UserProfileService, Test_Util_OCR, Test_VirtualTourViewController
