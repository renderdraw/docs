# Plan 01-04 Summary: Scan Apex Public Classes + Secondary Packages

**Completed:** 2026-04-17
**Duration:** ~15 minutes

## What Was Done

### Task 1: Scan main package Apex classes for public/global methods
Scanned all 110 .cls files in the main RenderDraw package, classifying each by visibility, sharing model, and type. Extracted method-level detail for all customer-facing classes.

**Results:**
| Global | Public (non-test) | Test/Private | Total |
|--------|-------------------|--------------|-------|
| 34 | 30 | 46 | 110 |

**Annotated methods (customer-facing surface):**
| Annotation | Count | Key Classes |
|------------|-------|-------------|
| @AuraEnabled | ~82 | CTRL_Renderer (15), CTRL_Mapping (14), CTRL_InteractionDefinition (11), UTIL_Record (10), CTRL_File (9), VirtualTourViewController (8) |
| @InvocableMethod | 7 | CTRL_AITakeoff, CTRL_AIVision, CTRL_File, FlowJsonWrapper, ContentVersionCADConversionHelper, RenderDrawMeasureProWallAreaHelper, Test_CanvasTransform |
| @RemoteAction | 0 | (none) |
| @Http* (REST) | 0 | (none) |

**Notable findings:**
- Global class count is 34 (vs. 8 identified in research) — research only flagged 8 key controllers/models; full scan revealed additional UTIL_* utility classes, VisualEditor picklists, and data model wrappers (BaseCanvasItem, DroppableArea, SnapShot, LayoutWall, etc.)
- @InvocableVariable used heavily in data model classes (CanvasScene, BaseCanvasItem, etc.) — these are the Flow/Agentforce integration surface
- No @RemoteAction or REST endpoints — all Apex APIs use @AuraEnabled or @InvocableMethod
- 1 @Future(Callout=true) in ContentVersionCADConversionHelper for async CAD conversion

**Commit:** `0a20f7e` — `feat(01-04): scan main package Apex classes for public/global methods`

### Task 2: Quick scan PropelPLM and AssetDigitalTwin packages
Scanned both secondary packages, applying filtering for the large AssetDigitalTwin directory.

**PropelPLM results:**
| LWC Components | Apex Classes | LMS Channels | Aura Events |
|---------------|-------------|-------------|-------------|
| 1 | 1 (+1 test) | 0 | 0 |

- LWC `itemRevisionAttachmentAnnotation`: 1 @api property (`contentId`), embeds 5 RenderDraw child components
- Apex `ItemRevisionAttachmentController`: 1 @AuraEnabled method (`createDocumentFromContent`) creating PDLM__Document__c records

**AssetDigitalTwin results:**
| Total .cls | Excluded | In-scope ADT | Aura Events | LWC Components |
|-----------|----------|-------------|-------------|----------------|
| 361 | 335 | 26 | 3 | 11 |

- Exclusions documented with exact counts: 203 SDO_, 39 sustain_app__, 29 Wave*, 26 auth/portal, 5 generic utilities, 33 demo/infra/mock
- Key ADT classes: AssetDigitalTwinController (7 @AuraEnabled), AutoCompleteController (2 @AuraEnabled), FlowFindCollection (1 @InvocableMethod)
- 4 Wave template remoters with 5 @RemoteAction methods each
- globalLookup LWC has 18+ @api properties — largest component in the package

**Commit:** `4f1d5d4` — `feat(01-04): scan PropelPLM and AssetDigitalTwin package API surfaces`

## Output

- `source-apex.md` — complete main package Apex inventory with method-level detail for all 34 global classes and all public classes with annotated methods
- `source-secondary-packages.md` — PropelPLM and AssetDigitalTwin inventories with filtering documentation

## Deviations

- **Global class count differs from research:** Found 34 vs. 8 estimated. Research identified only the 8 most prominent controllers/models; the deep scan captured all global-visibility classes including utilities, picklists, and data model wrappers. This is not an error — the additional classes are genuinely part of the public API surface.

## Issues Discovered

None.
