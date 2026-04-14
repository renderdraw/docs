# Plan 01-02 Summary: Scan LMS Channels & Aura Events from Source

**Completed:** 2026-04-14
**Duration:** ~15 minutes

## What Was Done

### Task 1: Extract all LMS message channel definitions with fields
Scanned all 5 `.messageChannel-meta.xml` files and searched the entire force-app for publisher/subscriber references.

**Results:**
- 5 channels confirmed (all `isExposed: true`)
- 4 LWC components interact with channels: canvas3D, canvas2D, standalone_DataTable, groupSelection
- No Aura component references found — all LMS usage is LWC-only
- `canvas3D` is bidirectional on Canvas_Interaction (both publishes and subscribes)

**Notable findings:**
- 2 channel descriptions are truncated in source XML (Canvas_Interaction, Record_Selected)
- Record_Selected has a commented-out `sender` field

### Task 2: Extract all Aura event definitions with attributes
Scanned all 56 `.evt` files, extracting type, attributes, access level, and categorizing by prefix.

**Results:**
| Category | Count | access=global | Likely Scope |
|----------|-------|---------------|-------------|
| Renderer | 19 | 14 | Public |
| Settings | 23 | 0 | Likely Internal |
| Admin | 8 | 0 | Public |
| Layout | 2 | 0 | Public |
| Scene | 1 | 0 | Public |
| Interaction | 1 | 0 | Public |
| Other | 2 | 0 | Public |

**Key findings:**
- ALL 56 events are APPLICATION type (zero COMPONENT events)
- 14 events have `access="global"` — all in Renderer category — confirming public API surface
- 23 Settings events follow consistent CRUD pattern across 5 custom metadata types — strong evidence of internal admin UI wiring
- EVT_Renderer_Input uniquely uses `access="public"` (not "global")
- Most event descriptions are generic "Event template"

**Commit:** `7d786c9` — `feat(01-02): scan LMS channels and Aura events from source`

## Output

`source-lms-events.md` — complete source inventory with:
1. LMS channel definitions with fields, publisher/subscriber mapping
2. Aura event inventory with attributes, types, categories, and scope classification
3. Detailed per-event attribute tables for all 56 events

## Deviations

None — counts match research (5 LMS, 56 events).

## Issues Discovered

None.
