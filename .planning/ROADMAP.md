# Roadmap: RenderDraw Documentation Update

## Overview

Systematically audit the public API surface across all RenderDraw Salesforce packages (main, PropelPLM, AssetDigitalTwin) and Revenue Cloud demos, then fill documentation gaps in the existing GitBook site. Work starts with a gap analysis against existing docs, proceeds through each API surface type (LMS, Aura events, LWC/Aura component APIs, Apex), reconciles extracted Canvas2D/Canvas3D docs, and finishes with the secondary packages and demo integrations.

## Domain Expertise

None

## Phases

**Phase Numbering:**
- Integer phases (1, 2, 3): Planned milestone work
- Decimal phases (2.1, 2.2): Urgent insertions (marked with INSERTED)

- [ ] **Phase 1: Audit & Gap Analysis** — Cross-reference existing docs against source to build gap inventory
- [ ] **Phase 2: LMS Message Channels** — Audit and document all LMS channels, payloads, and origins
- [ ] **Phase 3: Aura Events** — Audit and document all Aura application/component events
- [ ] **Phase 4: LWC Component APIs** — Audit all LWC public @api properties across main package
- [ ] **Phase 5: Aura Component APIs** — Audit all Aura public attributes across main package
- [ ] **Phase 6: Apex Public APIs** — Audit and document all public Apex classes/methods
- [ ] **Phase 7: Canvas2D/Canvas3D Delta** — Cross-reference extracted API docs with existing GitBook pages
- [ ] **Phase 8: PropelPLM Integration** — Document PropelPLM package public API surface
- [ ] **Phase 9: AssetDigitalTwin Package** — Document AssetDigitalTwin package public API surface
- [ ] **Phase 10: Revenue Cloud Demos** — Document Revenue Cloud demo integration patterns and APIs

## Phase Details

### Phase 1: Audit & Gap Analysis
**Goal**: Produce a complete inventory of what's documented vs. what exists in source code, across all API surface types and all packages
**Depends on**: Nothing (first phase)
**Research**: Unlikely (reading existing docs and source code)
**Plans**: TBD

Plans:
- [x] 01-01: Catalog existing GitBook documentation pages and their coverage
- [x] 01-02: Scan LMS message channels and Aura event definitions from source
- [x] 01-03: Scan LWC and Aura component @api surfaces from source
- [ ] 01-04: Scan Apex public classes + PropelPLM and AssetDigitalTwin packages
- [ ] 01-05: Cross-reference inventories and generate comprehensive gap report

### Phase 2: LMS Message Channels
**Goal**: Complete documentation for all Lightning Message Service channels — channels, payload fields, where they fire, and usage context
**Depends on**: Phase 1 (gap inventory identifies which channels are undocumented)
**Research**: Unlikely (reading .messageChannel-meta.xml files and component source)
**Plans**: TBD

Plans:
- [ ] 02-01: Audit all LMS channel definitions across packages
- [ ] 02-02: Document undocumented channels with payload shapes and origins

### Phase 3: Aura Events
**Goal**: Complete documentation for all Aura application and component events — event definitions, where they fire, payload shapes, and handler patterns
**Depends on**: Phase 1 (gap inventory identifies which events are undocumented)
**Research**: Unlikely (reading .evt files and component controllers)
**Plans**: TBD

Plans:
- [ ] 03-01: Audit all Aura event definitions across packages
- [ ] 03-02: Document undocumented events with payloads, origins, and usage

### Phase 4: LWC Component APIs
**Goal**: Complete documentation for all public @api properties and methods on LWC components in the main RenderDraw package
**Depends on**: Phase 1 (gap inventory identifies which components have undocumented APIs)
**Research**: Unlikely (reading LWC .js files for @api decorators)
**Plans**: TBD

Plans:
- [ ] 04-01: Audit all LWC components for public @api properties and methods
- [ ] 04-02: Document undocumented @api properties with types, defaults, and usage

### Phase 5: Aura Component APIs
**Goal**: Complete documentation for all public attributes on Aura components in the main RenderDraw package
**Depends on**: Phase 1 (gap inventory identifies which components have undocumented attributes)
**Research**: Unlikely (reading Aura .cmp/.app files for aura:attribute tags)
**Plans**: TBD

Plans:
- [ ] 05-01: Audit all Aura components for public attributes
- [ ] 05-02: Document undocumented attributes with types, defaults, and usage

### Phase 6: Apex Public APIs
**Goal**: Complete documentation for all public Apex classes, methods, and services (controllers, REST endpoints, invocable actions)
**Depends on**: Phase 1 (gap inventory identifies which Apex APIs are undocumented)
**Research**: Unlikely (reading .cls files for public/global methods)
**Plans**: TBD

Plans:
- [ ] 06-01: Audit all public Apex classes and methods across main package
- [ ] 06-02: Document undocumented Apex APIs with signatures, parameters, and return types

### Phase 7: Canvas2D/Canvas3D Delta
**Goal**: Reconcile the extracted Canvas2D and Canvas3D API documentation against existing GitBook pages, filling any gaps
**Depends on**: Phase 1 (understanding of existing doc coverage)
**Research**: Unlikely (comparing two existing documents)
**Plans**: TBD

Plans:
- [ ] 07-01: Diff extracted Canvas2D docs against GitBook pages
- [ ] 07-02: Diff extracted Canvas3D docs against GitBook pages
- [ ] 07-03: Write missing content into GitBook structure

### Phase 8: PropelPLM Integration
**Goal**: Document all public API surface in the PropelPLM integration package — components, events, LMS channels, Apex
**Depends on**: Phases 2-6 (established documentation patterns from main package)
**Research**: Unlikely (reading PropelPLM package source)
**Plans**: TBD

Plans:
- [ ] 08-01: Audit PropelPLM package for all public API surface
- [ ] 08-02: Document PropelPLM public APIs in GitBook structure

### Phase 9: AssetDigitalTwin Package
**Goal**: Document all public API surface in the AssetDigitalTwin package — components, events, LMS channels, Apex
**Depends on**: Phases 2-6 (established documentation patterns from main package)
**Research**: Unlikely (reading AssetDigitalTwin package source)
**Plans**: TBD

Plans:
- [ ] 09-01: Audit AssetDigitalTwin package for all public API surface
- [ ] 09-02: Document AssetDigitalTwin public APIs in GitBook structure

### Phase 10: Revenue Cloud Demos
**Goal**: Document Revenue Cloud demo integration patterns, APIs, and configuration for partners/developers
**Depends on**: Phase 6 (Apex documentation patterns established)
**Research**: Likely (Revenue Cloud integration patterns may require understanding Salesforce Revenue Cloud APIs)
**Research topics**: Revenue Cloud CPQ/Billing API patterns, demo architecture conventions, integration touchpoints with RenderDraw
**Plans**: TBD

Plans:
- [ ] 10-01: Audit Revenue Cloud demo source for integration patterns
- [ ] 10-02: Document Revenue Cloud integration APIs and configuration

## Progress

**Execution Order:**
Phases execute in numeric order: 1 → 2 → 3 → 4 → 5 → 6 → 7 → 8 → 9 → 10

| Phase | Plans Complete | Status | Completed |
|-------|---------------|--------|-----------|
| 1. Audit & Gap Analysis | 3/5 | In Progress | - |
| 2. LMS Message Channels | 0/2 | Not started | - |
| 3. Aura Events | 0/2 | Not started | - |
| 4. LWC Component APIs | 0/2 | Not started | - |
| 5. Aura Component APIs | 0/2 | Not started | - |
| 6. Apex Public APIs | 0/2 | Not started | - |
| 7. Canvas2D/Canvas3D Delta | 0/3 | Not started | - |
| 8. PropelPLM Integration | 0/2 | Not started | - |
| 9. AssetDigitalTwin Package | 0/2 | Not started | - |
| 10. Revenue Cloud Demos | 0/2 | Not started | - |
