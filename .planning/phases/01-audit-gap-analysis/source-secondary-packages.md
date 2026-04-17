# Source Inventory: Secondary Packages

> Generated: 2026-04-17 | Task: 01-04-T2

## PropelPLM Integration

### Summary
| LWC Components | Apex Classes | LMS Channels | Aura Events |
|---------------|-------------|-------------|-------------|
| 1 | 1 (+1 test) | 0 | 0 |

**Package path:** `renderdraw-for-propelplm/force-app/main/default/`

No Aura components, no LMS channels, no Aura events in this package. The `aura/` directory exists but is empty.

### LWC: itemRevisionAttachmentAnnotation

- **@api Properties:**

| Property | Type | Notes |
|----------|------|-------|
| `contentId` | implicit (String) | Set from URL param `c__contentId` |

- **RenderDraw child components used in template:**

| Component | Role |
|-----------|------|
| `RDraw-pdf-editor` | PDF annotation/editing with save-as |
| `RDraw-annotate-it` | Image annotation with save-as |
| `RDraw-canvas3-d` | 3D model viewer (playground mode) |
| `RDraw-standalone-_cad-conversion` | CAD-to-GLB conversion |
| `RDraw-local-notifications` | Toast-style user notifications |

- **Key event handlers:**
  - `handlePDFSaved` -- receives `{contentVersionId, contentDocumentId}` from PDF editor
  - `handleImageSaved` -- receives `{contentVersionId, contentDocumentId}` from image annotator
  - `handleCADConversionSuccess` -- receives `{savedFileIds}` from CAD converter
  - `handleComponentSelected` / `handleSelectionCleared` -- 3D component selection

- **URL parameters consumed:**
  - `c__contentId`, `c__type`, `c__attachmentId`, `c__itemRevision`, `c__revisionName`, `c__itemName`, `c__attachmentName`

### Apex: ItemRevisionAttachmentController

- **Visibility:** `public with sharing`
- **Methods:**

| Annotation | Return Type | Method | Parameters |
|------------|-----------|--------|------------|
| `@AuraEnabled` | `DocumentCreationResult` | `createDocumentFromContent` | `String contentId, String itemRevisionId` |

- **Inner classes:**

| Class | Fields |
|-------|--------|
| `DocumentCreationResult` | `@AuraEnabled Boolean success`, `@AuraEnabled String documentId`, `@AuraEnabled String message` |

- **Key behavior:** Detects ContentVersion (068) vs ContentDocument (069) by ID prefix, queries the content, creates a `PDLM__Document__c` record linking the content to an Item Revision.

---

## AssetDigitalTwin Package

**Package path:** `AssetDigitalTwin/force-app/main/default/`

### Filtering Applied

| Category | Count | Pattern |
|----------|-------|---------|
| Total .cls files in directory | 361 | -- |
| Excluded: SDO_ demo classes | 203 | `SDO_*` |
| Excluded: sustain_app__ classes | 39 | `sustain_app__*` |
| Excluded: Wave analytics classes | 29 | `Wave*` |
| Excluded: auth/portal templates | 26 | `ChangePassword*`, `Communities*`, `ForgotPassword*`, `Lightning*`, `MicrobatchSelfReg*`, `MyProfile*`, `SiteLogin*`, `SiteRegister*` |
| Excluded: generic utilities | 5 | `Zippex`, `HexUtil`, `MetadataService`, `MetadataServiceTest`, `SF_MetadataUtils` |
| **Remaining after first pass** | **59** | -- |
| Further excluded: demo/infra/mock | 33 | See below |
| **In-scope ADT classes** | **26** | See table below |

**Second-pass exclusions (demo infrastructure, data loading, test mocks):**
- Analytics demo: `AnalyticsDemoDataflowHelper`, `AnalyticsDemoFAQ`
- Time shifting infra: `CheckTimeShiftingQueue`, `ScheduledTimeShifting`, `TimeShiftingBatch`, `ScheduledChatterComment`
- Data loading: `CopyChatterFeeds`, `CreateObjectsAndFieldsQueueable`, `CreateRecordTypesQueueable`, `CsvDataImportBatch`, `CSVReader`, `CSV_RowIterator`, `LoadDashboardQueueable`, `LoadDatasetBatch`, `LoadDatasetQueueable`, `LoadEdgemartQueueable`, `UploadUserPhotoQueueable`, `Utility_RowIterator`
- Wave config: `GenericAppConfiguration`, `SalesWaveConfigurationModifierFlex`, `ServiceWaveConfigurationModifier`, `ReplaceSfdcDigestByEdgemarts`, `ReplaceSfdcDigestByEdgemartsDirect`, `ReplaceSfdcDigestByEdgemartsGeneric`
- Bulk/batch utilities: `MassDeleteExtension`, `MassDeleteExtensionTest`, `genericBatchExecutor`
- Test/mock helpers: `MockHttpResponseGenerator`, `MockarooHelperFactory`, `IMockarooHelper`, `MathRandomFunction`

### ADT Apex Classes

| Class Name | Visibility | @AuraEnabled | @RemoteAction | @InvocableMethod | Notes |
|------------|-----------|-------------|---------------|-----------------|-------|
| `AssetDigitalTwinController` | `public with sharing` | 7 methods | -- | -- | Core ADT controller |
| `AutoCompleteController` | `public` | 2 methods | -- | -- | Generic search/lookup |
| `AutoCompleteControllerTest` | `private` | -- | -- | -- | Test class |
| `ChecklistRemoter` | `global` | -- | 5 methods | -- | Sales Analytics wizard |
| `ServiceChecklistRemoter` | `global` | -- | 5 methods | -- | Service Analytics wizard |
| `CustomerInsightsConfigurationModifier` | `public with sharing` | -- | -- | -- | Wave template modifier |
| `CustomerInsightsRemoter` | `global with sharing` | -- | 5 methods | -- | Revenue Ops Analytics wizard |
| `RevInsightsConfigurationModifier` | `public with sharing` | -- | -- | -- | Wave template modifier |
| `RevInsightsRemoter` | `global with sharing` | -- | 5 methods | -- | Revenue Insights wizard |
| `FlowFindCollection` | `public with sharing` | -- | -- | 1 method | Flow-invocable SOQL/SOSL |
| `FlowFindCollectionTest` | -- | -- | -- | -- | Test class |
| `FlowFindCollection_WithoutSharing` | `without sharing` | -- | -- | -- | Sharing bypass helper |
| `CompositeSmartLookup` | `public` | -- | -- | -- | Data model (CSV import) |
| `SmartLookup` | `public` | -- | -- | -- | Data model (CSV import) |
| `CustomModalConfirmation` | `public` | -- | -- | -- | Data model (header/body) |
| `TimeShiftSettings` | `public` | -- | -- | -- | Data model (time shifting config) |
| `CPQB_QuickSelectCTRL` | `public` | ? | -- | -- | CPQ quick-select controller ? |
| `CPQB_QuickSelectCTRLTest` | -- | -- | -- | -- | Test class |
| `CPQB_QuickSelectCallback` | `public` | -- | -- | -- | CPQ deploy callback ? |
| `New_Wto_Ext` | `public` | -- | -- | -- | Extension ? |
| `PSBulkActionException` | `public` | -- | -- | -- | Custom exception |
| `PSResponse` | `public` | -- | -- | -- | Response wrapper |
| `Point` | `public` | -- | -- | -- | Geometry data model |
| `Puff` | `public` | -- | -- | -- | Zippex helper |
| `RestApiCompositeTreeResponse` | `public` | -- | -- | -- | REST API response model |
| `RestApiErrorResponse` | `public` | -- | -- | -- | REST API error model |
| `RestApiFolderErrorResponse` | `public` | -- | -- | -- | REST API folder error model |
| `RestApiResponseBody` | `public` | -- | -- | -- | REST API response model |

> Classes marked with `?` are ambiguous -- could be ADT-specific or reusable utility. Included for completeness.

### ADT Apex Method Details

#### AssetDigitalTwinController (7 @AuraEnabled methods)

| Return Type | Method | Parameters |
|-------------|--------|------------|
| `List<Asset>` | `getChildAssets` | `String parentId` |
| `Asset` | `getAssetByProductCode` | `String productCode, String rootAssetId` |
| `Asset` | `getAssetById` | `String assetId` |
| `List<HierarchyWrapper>` | `fetchAssetHierarchy` | `String assetId` (cacheable) |
| `List<RelatedProduct>` | `getReplacementProducts` | `String productId` |
| `String` | `addSelectedItemsToActiveCart` | `List<RelatedProduct> selectedItems` |
| `String` | `addConfiguredItemToActiveCart` | `String productId, String quantity, String configuration` |

Inner classes: `HierarchyWrapper` (13 @AuraEnabled fields), `RelatedProduct` (5 @AuraEnabled fields)

#### AutoCompleteController (2 @AuraEnabled methods)

| Return Type | Method | Parameters |
|-------------|--------|------------|
| `List<ResultssObject>` | `getRecords` (cacheable) | `String searchString, String objectApiName, String valueFieldApiName, String extendedWhereClause, Integer maxRecords, String extraObjects, String SearchScope, String QueryType, Boolean Bypasssharing` |
| `void` | `saveResult` | `Id recordId, String fieldAPiName, String value` |

#### FlowFindCollection (1 @InvocableMethod)

| Return Type | Method | Label |
|-------------|--------|-------|
| `List<Results>` | `execute` | "Get / Search with APEX" |

InvocableVariables: `FieldApiINames`, `WhereClause`, `sObjectName`, `IdsList`, `IdListFieldName`, `BypassSharing`, `queries`, `scope`, `SearchExtraObjects`, `WhereLimit`

#### ChecklistRemoter (5 @RemoteAction methods)

| Return Type | Method |
|-------------|--------|
| `Map<String, Object>` | `dataOk` |
| `Map<String, Object>` | `objectUsage` |
| `Map<String, Object>` | `fieldAccess` |
| `Map<String, Object>` | `configuration` |
| `Map<String, Object>` | `dataInconsistencies` |

#### ServiceChecklistRemoter (5 @RemoteAction methods)

| Return Type | Method | Parameters |
|-------------|--------|------------|
| `Map<String, Object>` | `dataOk` | `Boolean isCustomReset` |
| `Map<String, Object>` | `objectUsage` | `Boolean isCustomReset` |
| `Map<String, Object>` | `fieldAccess` | `Boolean isCustomReset` |
| `Map<String, Object>` | `configuration` | `Boolean isCustomReset` |
| `Map<String, Object>` | `caseHistoryCheck` | `Boolean isCustomReset` |

#### CustomerInsightsRemoter (5 @RemoteAction methods)

| Return Type | Method |
|-------------|--------|
| `Map<String, Object>` | `dataOk` |
| `Map<String, Object>` | `objectUsage` |
| `Map<String, Object>` | `fieldAccess` |
| `Map<String, Object>` | `configuration` |
| `Map<String, Object>` | `dataInconsistencies` |

#### RevInsightsRemoter (5 @RemoteAction methods)

| Return Type | Method |
|-------------|--------|
| `Map<String, Object>` | `dataOk` |
| `Map<String, Object>` | `objectUsage` |
| `Map<String, Object>` | `fieldAccess` |
| `Map<String, Object>` | `configuration` |
| `Map<String, Object>` | `dataInconsistencies` |

### ADT Aura Events (filtered, excluding SDO_ prefix)

| Event Name | Type | Attributes |
|------------|------|------------|
| `CPQB_QuickRemove` | APPLICATION | `removeRow` (Integer) |
| `setExpId` | APPLICATION | `expid` (String) |
| `setStartUrl` | APPLICATION | `startURL` (Map) |

> 3 non-SDO events out of ~170+ total aura items. The vast majority are SDO demo components.

### ADT Aura Components (filtered, excluding SDO_ prefix)

| Component | Type | Notes |
|-----------|------|-------|
| `AssetDigitalTwin` | Aura CMP | Core ADT component |
| `CPQB_QuickSelect` | Aura CMP | CPQ quick-select UI ? |
| `CPQB_QuickSelectRow` | Aura CMP | CPQ quick-select row ? |
| `annualCrabonInventoryExtrapolationWrapper` | Aura CMP | Sustainability wrapper |
| `forgotPassword` | Aura CMP | Auth template |
| `loginForm` | Aura CMP | Auth template |
| `selfRegister` | Aura CMP | Auth template |

> 7 non-SDO Aura components. Auth templates (`forgotPassword`, `loginForm`, `selfRegister`) are boilerplate.

### ADT LWC Components (filtered, excluding b2b*/sdo*/sustain* prefix)

| Component | @api Properties | Notes |
|-----------|----------------|-------|
| `annualCarbonInventoryExtrapolation` | (none) | Sustainability |
| `createReport` | `folderName`, `diagramImageSource` | Report creation utility |
| `fireCartChangedEvent` | `availableActions` | B2B cart event helper |
| `globalLookup` | `label`, `objectApiNameInput`, `valueFieldApiName`, `idFieldApiName`, `extendedWhereClause`, `maxRecords`, `extraObjects`, `searchScope`, `selectedOption`, `queryType`, `inputFieldAPIName`, `StartingValue`, `FlowAction`, `Bypasssharing`, `LoadPreloadedRecordId`, `inputValue`, `recordId`, `availableActions` + 5 @api methods | Core lookup component -- uses AutoCompleteController |
| `modal` | (none) | Generic modal |
| `parallaxcmp` | `backgroundImage`, `mainTitle`, `fontColor`, `overlayColor`, `imageHeight`, `fontSize` | Parallax visual effect |
| `sdp_customer_summary` | `recordId` | Customer summary ? |
| `spotterCmsResourceResolver` | (none) | Spotter CMS helper |
| `spotterConfig` | `recordId` | Spotter configuration |
| `spotterEmbed` | `recordId`, `spotterMode`, `configId`, `showSpotterTitle`, `showHotspotsDesktop`, `showHotspotsMobile`, `showProductCarousel`, `productCarouselTitle`, `effectiveAccountId` | Spotter embed ? |
| `spotterIllustration` | (none) | Spotter illustration |

> 11 non-b2b/sdo/sustain LWC components. The `globalLookup` is the most significant -- it is the UI counterpart to `AutoCompleteController` and `FlowFindCollection`.
> Spotter components (`spotterConfig`, `spotterEmbed`, `spotterCmsResourceResolver`, `spotterIllustration`) appear to be a 3D/visual product configurator unrelated to RenderDraw.
