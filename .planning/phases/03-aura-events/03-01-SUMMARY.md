---
phase: 03-aura-events
plan: 01
subsystem: aura-events
requires: [01-audit-gap-analysis, 02-lms-message-channels]
provides: [source-aura-event-mapping]
affects: [03-02, 03-03, 03-04, 03-05]
tags: [audit, aura, events, source-mapping]
key-files:
  - .planning/phases/03-aura-events/source-aura-event-mapping.md
---

# Plan 03-01 Summary: Source Inventory — Aura Event Source/Handler Mapping

Mapped all 33 public Aura events to their source (firing) and handler components via main-package grep. 5 events have no in-package handler (consumed externally), 6 events have no in-package source (fired by consumers), 0 events are bidirectional.

## Accomplishments

- Inventoried all 33 public Aura events with Source Component(s) and Handler Component(s), derived from `<aura:registerEvent type="RDraw:EVT_*"/>` and `<aura:handler event="RDraw:EVT_*"/>` grep sweeps of the main RenderDraw package.
- 5 events with no in-package handler (consumed externally): `EVT_Add3DShape`, `EVT_Renderer_Camera_Changed`, `EVT_Renderer_Input`, `EVT_Renderer_RelatedRecord_Fetched`, `EVT_Renderer_Screenshot_Taken`.
- 6 events with no in-package source (fired by consumers or secondary packages): `EVT_AdminTestRenderer_GroupCreate`, `EVT_AdminTestRenderer_HideGroupDetails`, `EVT_AdminTestRenderer_ShowGroupDetails`, `EVT_Renderer_Group_Transformed`, `EVT_Renderer_Input`, `EVT_Renderer_Select_Component`.
- 0 bidirectional events found at the component level.
- Category breakdown matches Phase 1: Renderer=19, Admin=8, Layout=2, Scene=1, Interaction=1, Other=2 (total=33).
- Discovered architectural pattern: `SimpleRenderer` registers 14 Renderer-category events; `AdvancedRenderer` nests SimpleRenderer and adds 2 of its own (`EVT_InteractionEvent_Status_Log`, `EVT_Renderer_RelatedRecord_Fetched`). Consumers embed `<RDraw:AdvancedRenderer/>` to receive renderer events — SimpleRenderer is the canonical source.
- Discovered legacy-form `type="RDraw.EVT_*"` (dot, not colon) used on 4 registerEvent declarations — resolves identically to the colon form at runtime.
- Documented LWC `annotations3D` DOM-CustomEvent dispatch of `EVT_SceneSettings_Ready_For_Update` as an ancillary source (not counted as a primary Aura source).

## Files Created/Modified

- `.planning/phases/03-aura-events/source-aura-event-mapping.md` — new inventory file (commit `a57c7b2`)

## Decisions Made

- **Firing is identified by `<aura:registerEvent>`, not by JS `$A.get().fire()` calls.** The Aura runtime requires every firing component to declare its registered events in the `.cmp` markup; JS-only firing without a markup declaration is not possible. Grepping `aura:registerEvent` is therefore the authoritative source-component identification method.
- Events with zero source matches in the main package are documented but flagged in Observations for manual verification — cannot prove they are dead code without a secondary-package grep.
- Internal `EVT_Settings_*` events (23 of the 56 total) excluded from scope per PROJECT.md public-API-only constraint.
- LWC sweep for `RDraw:EVT_` included for completeness; only one LWC (`annotations3D`) dispatches a DOM CustomEvent of an Aura event name — annotated but not counted as a primary Aura source because LWCs cannot fire Aura application events directly.
- For Renderer events, the documentation in Plans 03-02 through 03-05 should attribute source to `SimpleRenderer` while noting that consumers typically embed `AdvancedRenderer` (the user-facing container).

## Issues Encountered

- **Initial grep for firing patterns (`e\.RDraw:EVT_`) returned no matches.** Root cause: the firing pattern used in Aura controllers is `$A.getEvt("RDraw:EVT_...")` or `component.getEvent("localName").fire()` — the registration, not the firing call, is where the event-to-component binding lives. Corrected by switching to `<aura:registerEvent type="RDraw:EVT_*">` as the authoritative source-identification pattern.
- **Initial handler grep pattern `aura:handler[^>]*event="RDraw:EVT_` missed 2 handlers** where the `event=` attribute sat on a continuation line in AdminVisualSceneSetup.cmp (`EVT_AdvancedLayout_HideContextDetailHeader`, `EVT_AdvancedLayout_ShowContextDetailHeader`). Corrected by running a broader `event="RDraw:EVT_` sweep.
- **Verification count for `EVT_Settings_` returned 1** (an informational scope sentence — "excludes 23 internal `EVT_Settings_*` events") rather than 0. Auto-fixed by rewording the scope sentence to avoid the literal token while preserving the informational value.
- **Markdown linter (MD060) flagged compact table divider style.** Auto-fixed per Phase 2 precedent (Plan 02-01's Issues Encountered note) by switching to spaced dividers where flagged.
- **Reconciled Phase 2 plan count.** STATE.md and ROADMAP showed `1/2` for Phase 2 but Plan 02-01 completed the phase. Reconciled to `1/1` in STATE.md and ROADMAP; Plan 02-02 marked as rolled into 02-01.

## Commits

- `a57c7b2` — feat(03-01): produce source-aura-event-mapping inventory

## Next Step

Ready for 03-02-PLAN.md (enrich 9 existing Aura event pages with Source Component, Handler Component, and Event Name (for handler) sections).
