# Phase 1: Audit & Gap Analysis - Research

**Researched:** 2026-04-09
**Domain:** Salesforce component/API documentation auditing across GitBook + source packages
**Confidence:** HIGH

<research_summary>
## Summary

Researched the existing GitBook documentation coverage against the actual source code across all three RenderDraw packages (main, PropelPLM, AssetDigitalTwin). The audit reveals significant documentation gaps — the GitBook covers approximately 18% of Aura events, 5% of components, and has minimal Apex API documentation.

The main RenderDraw package contains 5 LMS channels, 56 Aura events, 163 LWC components, 35 Aura components, and 105 Apex classes. The AssetDigitalTwin package is unexpectedly large (361 Apex classes, 161 Aura components). Extracted Canvas2D/Canvas3D documentation covers hundreds of methods and events that haven't been reconciled with GitBook pages.

**Primary recommendation:** Build a structured gap inventory organized by API surface type, mapping each source artifact to its documentation status (documented/undocumented/partial). Use file system patterns (grep for @api, .evt, .messageChannel-meta.xml, public/global class) for systematic discovery.
</research_summary>

<existing_documentation>
## Existing GitBook Documentation Inventory

### Overall Structure
- **~216 total markdown files** across the GitBook
- **~40 API-focused pages** covering components, events, data objects, LMS, and CAD API
- Organized into: About, Introduction, Usage Scenarios, API Documentation, Digital Twin

### API Documentation Pages by Category

**3D Component APIs (5 components documented):**
- 3D Interaction Canvas (LWC)
- 3D Advanced Renderer (Aura)
- 3D Simple Renderer (Aura)
- 3D Scene Director (Aura)
- 3D File Attachment Viewer (Aura)

**2D Component APIs (2 components documented):**
- 2D Interaction Canvas
- 2D Scene Director

**Universal Components (3 documented):**
- DynamicContentComponent TreeGrid
- RDraw Layout
- README index

**Data Objects (5 documented):**
- Canvas, BaseCanvasItem, LayoutWall, DropZone, DroppableArea

**Aura Events (9 events documented + README):**
- EVT_Renderer_Loaded
- EVT_Renderer_Context_Details_Closed
- EVT_Renderer_Element_Added
- EVT_Renderer_Get_CameraPositionandTarget
- EVT_Renderer_Get_Hierarchy
- EVT_Renderer_Mesh_Selected
- EVT_Renderer_Mesh_Selection_Cleared
- EVT_Renderer_Screenshot_Taken
- EVT_Renderer_Select_Component

**LMS Channels (5 documented):**
- Canvas Initialized
- Canvas Element Selected
- Canvas Element Hovered
- Canvas Interaction
- Record Selected
- Plus: Code example of listening to LMS events

**CAD Conversion API (5 pages):**
- Version 1 direct use + example input
- Version 2 proposal + purpose + sample input

**Other Developer Pages:**
- Modifying Canvas with Apex
- Custom 2D/3D App Development guides
- Custom Component Interaction with Renderer
- Development Resources
- Utilizing Interactions within Lightning Flow

### Naming Conventions
- Component files: `[component-name]-[framework].md`
- Event files: `evt_[event_name].md` (lowercase, underscores)
- LMS files: human-readable names (e.g., `canvas-initialized.md`)
- Directories: kebab-case
- README.md files as section indexes
</existing_documentation>

<source_inventory>
## Source Code Inventory

### Main RenderDraw Package
**Path:** `/Users/erikpilgrim/Documents/Dev/Personal/RenderDraw SFDC/RenderDraw/force-app/main/default/`

| Category | Count | Location |
|----------|-------|----------|
| LMS Message Channels | 5 | messageChannels/ |
| Aura Events (.evt) | 56 | aura/ |
| LWC Components | 163 | lwc/ |
| Aura Components (.cmp) | 35 | aura/ |
| Apex Classes (Global) | 8 | classes/ |
| Apex Classes (Public) | 47 | classes/ |
| Apex Classes (Private/Test) | 50 | classes/ |

### PropelPLM Integration
**Path:** `/Users/erikpilgrim/Documents/Dev/Personal/RenderDraw for PropelPLM/renderdraw-for-propelplm/`

| Category | Count | Details |
|----------|-------|---------|
| LMS Message Channels | 0 | — |
| Aura Events | 0 | — |
| Aura Components | 0 | — |
| LWC Components | 1 | itemRevisionAttachmentAnnotation |
| Apex Classes | 2 | ItemRevisionAttachmentController + test |

### AssetDigitalTwin Package
**Path:** `/Users/erikpilgrim/Documents/Dev/Personal/AssetDigitalTwin/AssetDigitalTwin/force-app/main/default/`

| Category | Count | Notes |
|----------|-------|-------|
| LMS Message Channels | 0 | — |
| Aura Events | 32 | Mostly SDO_ prefixed (demo/Solution Demo Org) |
| Aura Components | 161 | Large — includes B2B Commerce, Service Cloud, CPQ |
| LWC Components | 24 | B2B checkout, analytics, sustainability |
| Apex Classes | 361 | Very large — multi-cloud demo ecosystem |

### Extracted API Documentation (Reference)
**Canvas2D_API_Documentation.md:**
- 24 @api properties
- 11 method categories (~70+ methods)
- 40+ custom events across 4 categories
- Full sendMessage contract

**Canvas3D_API_Documentation.md:**
- 25 @api properties
- 7 method categories (~100+ methods)
- 24 custom events
- 4 LMS channels (publish) + 2 (subscribe)
- 88 outbound postMessage commands + 21 inbound callbacks
- 4 named slots
</source_inventory>

<gap_analysis>
## Gap Analysis Summary

### LMS Message Channels
| Channel | Documented? | Gap |
|---------|------------|-----|
| Canvas_Interaction | ✅ Yes | Check payload completeness |
| Canvas_Initialized | ✅ Yes | Check payload completeness |
| Record_Selected | ✅ Yes | Check payload completeness |
| Canvas_ElementSelected | ✅ Yes | Check payload completeness |
| Canvas_ElementHovered | ✅ Yes | Check payload completeness |

**Gap: LOW** — All 5 channels documented. Need to verify payload field completeness against source.

### Aura Events
| Status | Count | Percentage |
|--------|-------|------------|
| Documented | 9 | 16% |
| Undocumented | 47 | 84% |

**Gap: CRITICAL** — 47 of 56 events lack documentation. Undocumented categories:
- Admin/Setup events (9): EVT_AdminTestRenderer_*, EVT_AdminExplosion*
- Settings events (22): EVT_Settings_Controls_*, EVT_Settings_Light_*, EVT_Settings_Relationship_*, EVT_Settings_RenderDraw_*
- Layout events (2): EVT_AdvancedLayout_*
- Renderer events (8): EVT_Renderer_Camera_Changed, EVT_Renderer_Component_Transformed, EVT_Renderer_Group_Transformed, EVT_Renderer_Input, EVT_Renderer_LabelStyling_*, EVT_Renderer_Mesh_Hovered, EVT_Renderer_RelatedRecord_Fetched, EVT_Renderer_Settings_Fetched
- Scene events (2): EVT_SceneSettings_Ready_For_Update, EVT_Add3DShape
- Other (4): EVT_InteractionEvent_Status_Log, EVT_Renderer_Element_Verify, EVT_Switch_Tab

**Note:** Many Settings_* events may be internal admin UI. Phase 3 should classify which are truly public API vs internal.

### LWC Components
| Status | Estimated Count |
|--------|----------------|
| Documented (with @api details) | ~5 (canvas2D, canvas3D via extracted docs) |
| Partially documented | ~5 (mentioned in GitBook but @api not detailed) |
| Undocumented | ~153 |

**Gap: CRITICAL** — 163 LWC components exist; most have no documentation of their @api properties. The extracted Canvas2D/3D docs cover the two primary canvas components thoroughly, but these aren't yet in GitBook.

**Priority components likely to have public @api surfaces:**
- canvas2D, canvas3D (extracted docs exist)
- layout, droppableArea, draggableItem
- interactiveMap, virtualTour
- cadConversion, pdfEditor
- annotateIt, annotations3D
- dynamicContentComponent_* family

### Aura Components
| Status | Estimated Count |
|--------|----------------|
| Documented | ~5 (AdvancedRenderer, SimpleRenderer, SceneSetup, DynamicContentComponent, Settings) |
| Undocumented | ~30 |

**Gap: HIGH** — Most Aura components not documented for their public attributes.

### Apex Public APIs
| Status | Estimated Count |
|--------|----------------|
| Documented | ~2 (CAD conversion, basic Apex mentions) |
| Undocumented (Global) | ~6 (CTRL_AITakeoff, CTRL_AIVision, CanvasScene, DraggableItemTemplate, DroppableAreaTemplate, MetadataEntry/List, VirtualTourViewController) |
| Undocumented (Public controllers) | ~20+ (CTRL_*, UTIL_*, SpreadsheetImportController, etc.) |

**Gap: CRITICAL** — Almost no Apex API documentation. 8 global classes (customer-facing) and 47 public classes with undocumented methods.

### Canvas2D/Canvas3D Reconciliation
**Gap: HIGH** — Comprehensive extracted docs exist but haven't been compared to GitBook pages. The extracted docs contain:
- Canvas2D: 24 properties, ~70 methods, 40+ events (GitBook has 1 page)
- Canvas3D: 25 properties, ~100 methods, 24 events, 88 postMessage commands (GitBook has 1 page)

### Secondary Packages
**PropelPLM:** Minimal (1 LWC + 1 Apex controller). Small gap.
**AssetDigitalTwin:** Very large (361 Apex, 161 Aura components). BUT many are SDO_ prefixed (Solution Demo Org) — these may be demo scaffolding, not customer-facing APIs. Phase 9 needs to separate public APIs from demo infrastructure.
</gap_analysis>

<audit_patterns>
## Audit Patterns — How to Systematically Find Gaps

### LMS Channel Audit
```bash
# Find all channel definitions
find [package-path] -name "*.messageChannel-meta.xml" | sort

# Extract channel fields from XML
grep -A2 "<lightningMessageFields>" [channel-file]
```

### Aura Event Audit
```bash
# Find all .evt files
find [package-path] -name "*.evt" | sort

# Extract event attributes
grep "aura:attribute" [evt-file]

# Find where events are fired
grep -r "fireEvent\|fire(" --include="*.js" --include="*.cmp" [package-path]
```

### LWC @api Property Audit
```bash
# Find all @api declarations
grep -rn "@api" --include="*.js" [package-path]/lwc/

# Find @api in specific component
grep -n "@api" [component-path]/*.js
```

### Aura Component Attribute Audit
```bash
# Find all public attributes
grep -rn "aura:attribute" --include="*.cmp" [package-path]/aura/

# Extract attribute details
grep "aura:attribute" [component].cmp | sed 's/.*name="\([^"]*\)".*/\1/'
```

### Apex Public API Audit
```bash
# Find global/public classes
grep -rln "global class\|public class\|global with sharing\|public with sharing" --include="*.cls" [package-path]

# Find public/global methods
grep -n "public\|global\|@AuraEnabled\|@InvocableMethod\|@RemoteAction" [class-file]
```
</audit_patterns>

<dont_hand_roll>
## Don't Hand-Roll

| Problem | Don't Build | Use Instead | Why |
|---------|-------------|-------------|-----|
| Source file discovery | Manual file-by-file reading | grep/glob patterns above | 163 LWC + 35 Aura + 105 Apex = too many to read manually |
| Gap tracking | Mental model of what's documented | Structured gap report (markdown table) | Need to hand off between sessions |
| Event origin tracing | Reading every component controller | `grep -r "fireEvent"` + `grep -r "fire("` | Events are fired from specific handlers, grep finds them |
| Payload shape extraction | Reading event definitions one at a time | Batch `grep "aura:attribute"` across all .evt files | Pattern is consistent across all events |
| @api extraction | Reading each JS file individually | `grep -rn "@api"` across lwc/ directory | All follow same decorator pattern |
| Doc page inventory | Manually browsing GitBook | Parse SUMMARY.md programmatically | SUMMARY.md is the authoritative TOC |

**Key insight:** This is a documentation audit, not a coding task. The bottleneck is systematic discovery and comparison, not implementation complexity. Shell tools (grep, find) do 80% of the work.
</dont_hand_roll>

<common_pitfalls>
## Common Pitfalls

### Pitfall 1: Confusing Internal vs Public APIs
**What goes wrong:** Documenting internal-only events/components as if they're public API
**Why it happens:** Settings_* events and admin components may be purely internal wiring
**How to avoid:** Check if the component/event is used only within the managed package or if it's accessible to customers. Look for `access="global"` in Aura, and `@api` in LWC.
**Warning signs:** Events that are both fired and handled within the same component family

### Pitfall 2: AssetDigitalTwin Scope Explosion
**What goes wrong:** Attempting to document all 361 Apex classes in AssetDigitalTwin
**Why it happens:** Package contains SDO (Solution Demo Org) demo scaffolding alongside actual product code
**How to avoid:** Filter by prefix — SDO_ prefixed classes/components are demo infrastructure, not product API. Focus on AssetDigitalTwin-specific classes.
**Warning signs:** Classes with SDO_, Community_, B2B_ prefixes that don't relate to digital twin functionality

### Pitfall 3: Stale Existing Documentation
**What goes wrong:** Trusting existing GitBook pages are accurate and only filling gaps
**Why it happens:** Source code evolves; docs may document old property names or missing new ones
**How to avoid:** For each documented component, also verify current docs match current source
**Warning signs:** Property names in docs that don't appear in source `grep`

### Pitfall 4: Missing the Extracted Docs
**What goes wrong:** Redoing work already captured in Canvas2D/Canvas3D extracted docs
**Why it happens:** Not reconciling extracted docs before starting component audits
**How to avoid:** Phase 7 exists specifically for this — but Phase 1 gap report should note that extracted docs cover canvas2D and canvas3D thoroughly
**Warning signs:** Spending time auditing canvas2D/canvas3D @api properties when the extracted docs already have them

### Pitfall 5: Incomplete Event Origin Tracking
**What goes wrong:** Documenting event payload but not where/when it fires
**Why it happens:** Finding the .evt definition is easy; finding every `fireEvent` call is harder
**How to avoid:** For each event, grep all component JS/controllers for the event name to find fire points
**Warning signs:** Event docs that say "fires when..." without specifying the source component
</common_pitfalls>

<scoping_decisions>
## Scoping Decisions for Phase 1

### What's IN Scope for the Gap Report
1. **Main RenderDraw package** — full audit of all API surface types
2. **PropelPLM package** — minimal, quick audit
3. **AssetDigitalTwin package** — scoped to actual digital twin APIs (filter out SDO_ demo code)
4. **Extracted Canvas2D/Canvas3D docs** — note their existence and coverage for Phase 7

### What's OUT of Scope for the Gap Report
1. Revenue Cloud demos — separate phase (Phase 10)
2. Internal-only APIs — identified but explicitly excluded
3. Test classes — not public API
4. Custom Metadata types — configuration, not API
5. Static resources — assets, not API
6. Flows — declarative, not documented as API

### Classification Schema for Gap Report
Each source artifact should be classified as:
- **Documented**: Has a GitBook page with accurate content
- **Partially documented**: Mentioned in GitBook but missing details (properties, payload, etc.)
- **Undocumented**: No GitBook page exists
- **Internal only**: Not public API — exclude from documentation scope
- **Covered by extracted docs**: Canvas2D/3D items covered in extracted docs but not yet in GitBook
</scoping_decisions>

<open_questions>
## Open Questions

1. **AssetDigitalTwin public vs demo scope**
   - What we know: 361 Apex classes, 161 Aura components — many SDO_ prefixed
   - What's unclear: Which classes are actual AssetDigitalTwin product APIs vs demo scaffolding
   - Recommendation: During Phase 9, filter by prefix and cross-reference with AssetDigitalTwin-specific functionality

2. **Settings_* events — public or internal?**
   - What we know: 22 Settings_* Aura events for Controls, Light, Relationship, RenderDraw
   - What's unclear: Whether customers interact with these or they're purely internal admin UI wiring
   - Recommendation: During Phase 3, check if these events cross component boundaries or are self-contained within Settings

3. **Existing docs accuracy**
   - What we know: 9 events and ~10 components are documented
   - What's unclear: Whether existing documentation is current (properties may have been added/removed)
   - Recommendation: Phase 1 gap report should flag "needs verification" for existing pages, not assume correctness
</open_questions>

<sources>
## Sources

### Primary (HIGH confidence)
- GitBook SUMMARY.md — full table of contents parsed, all 216 pages inventoried
- Main package source tree — all directories enumerated via glob/ls
- PropelPLM package source tree — all artifacts inventoried
- AssetDigitalTwin package source tree — all artifacts inventoried
- Canvas2D_API_Documentation.md — full structure analyzed
- Canvas3D_API_Documentation.md — full structure analyzed

### Secondary (MEDIUM confidence)
- @api property counts based on grep patterns (exact count per component requires per-file reading)
- Apex class visibility based on class declaration grep (some may have mixed public/private methods)

### Tertiary (LOW confidence - needs validation)
- AssetDigitalTwin scope classification (SDO_ prefix assumption needs verification during Phase 9)
- Settings_* event public/internal classification (needs Phase 3 investigation)
</sources>

<metadata>
## Metadata

**Research scope:**
- Core technology: Salesforce Aura + LWC + Apex + LMS
- Ecosystem: GitBook documentation platform
- Patterns: Documentation auditing via shell tools
- Pitfalls: Scope explosion, stale docs, internal vs public classification

**Confidence breakdown:**
- Existing docs inventory: HIGH - parsed directly from SUMMARY.md and file system
- Source code inventory: HIGH - enumerated all files via glob patterns
- Gap analysis: HIGH - direct comparison of inventories
- Scoping recommendations: MEDIUM - AssetDigitalTwin scope needs validation

**Research date:** 2026-04-09
**Valid until:** 2026-05-09 (30 days - source packages unlikely to change during doc project)
</metadata>

---

*Phase: 01-audit-gap-analysis*
*Research completed: 2026-04-09*
*Ready for planning: yes*
