# RenderDraw Documentation Update

## What This Is

A comprehensive documentation update for the RenderDraw GitBook site (renderdrawdocs), filling gaps in public API coverage by auditing source code across the main RenderDraw Salesforce package, PropelPLM integration, AssetDigitalTwin package, and Revenue Cloud demos. The docs serve Salesforce admins, developers, and partners who build on or configure RenderDraw.

## Core Value

Complete, accurate public API surface documentation — every LMS message, Aura event, public @api property, and Apex method that customers and partners can use, with where it fires, payload shape, and usage context.

## Requirements

### Validated

- ✓ Existing GitBook structure with ~220 pages covering 2D, 3D, Digital Twin, API docs, use cases — existing
- ✓ Canvas2D API documentation extracted — existing
- ✓ Canvas3D API documentation extracted — existing
- ✓ LMS message channel documentation (5 channels documented) — existing
- ✓ Aura event documentation (9 events documented) — existing
- ✓ Component API pages for 2D and 3D interaction canvas, scene directors, advanced renderer — existing

### Active

- [ ] Audit all LWC/Aura components across main RenderDraw package for undocumented public @api properties
- [ ] Audit all LMS message channels for undocumented channels or payload fields
- [ ] Audit all Aura application/component events for undocumented events
- [ ] Audit all public Apex classes/methods (controllers, services) for undocumented APIs
- [ ] Document where each event/message fires from (component origin + user action trigger)
- [ ] Document event payload shapes with field descriptions
- [ ] Fill gaps for PropelPLM integration package public surface
- [ ] Fill gaps for AssetDigitalTwin package public surface
- [ ] Document Revenue Cloud demo integration patterns and APIs
- [ ] Cross-reference extracted Canvas2D/Canvas3D docs against existing GitBook pages to identify deltas

### Out of Scope

- Internal implementation details — only public API surface (private methods, internal helpers, internal wiring excluded)
- Restructuring existing documentation pages — only add new content and fill gaps
- Non-Salesforce documentation (external hosting, iOS MeasurePro app internals)
- Security review documentation or AppExchange-specific content

## Context

- **Source packages:**
  - Main: `/Users/erikpilgrim/Documents/Dev/Personal/RenderDraw SFDC/RenderDraw/force-app/`
  - PropelPLM: `/Users/erikpilgrim/Documents/Dev/Personal/RenderDraw for PropelPLM/`
  - AssetDigitalTwin: `/Users/erikpilgrim/Documents/Dev/Personal/AssetDigitalTwin/AssetDigitalTwin/force-app/`
- **Extracted API docs (reference):**
  - `/Users/erikpilgrim/Documents/Dev/Personal/RenderDraw SFDC/RenderDraw/Canvas2D_API_Documentation.md`
  - `/Users/erikpilgrim/Documents/Dev/Personal/RenderDraw SFDC/RenderDraw/Canvas3D_API_Documentation.md`
- **Tech stack:** Salesforce Aura + LWC components, Apex controllers, LMS message channels, Custom Metadata
- **Documentation platform:** GitBook with Markdown files, SUMMARY.md as table of contents
- **Component types in source:** Aura components (AdminExplosionSetup, AdvancedRenderer, DynamicContentComponent, SceneSetup, Settings, etc.), LWC components, Apex classes
- **Existing doc coverage:** Strong on admin guides and use cases, weaker on developer API reference completeness

## Constraints

- **Format**: All documentation must follow existing GitBook/Markdown structure and SUMMARY.md conventions
- **Style**: New content must match existing voice, tone, and structural patterns — no style overhaul
- **Scope**: Public API surface only — LMS messages, Aura events, public @api properties, public Apex methods
- **Source of truth**: Source code is authoritative; existing docs may be stale or incomplete

## Key Decisions

| Decision | Rationale | Outcome |
|----------|-----------|---------|
| Fill gaps alongside existing docs (not replace) | Preserve validated existing content; only add what's missing | — Pending |
| Public API surface only | Customers need stable, documented interfaces; internal details change frequently | — Pending |
| Audit source code across all 3 packages + revenue cloud | End-to-end coverage requires checking all packages, not just main | — Pending |

---
*Last updated: 2026-04-09 after initialization*
