# Plan 01-03 Summary: Scan LWC & Aura Component @api Surfaces

**Completed:** 2026-04-17
**Duration:** ~15 minutes

## What Was Done

### Task 1: Scan all LWC components for @api properties
Scanned all LWC component directories in the main RenderDraw force-app, extracting @api properties and methods from each component's .js file.

**Results:**
| Has @api | No @api | Total |
|----------|---------|-------|
| 136 | 33 | 169 |

**Top components by @api surface:**
| Component | @api Props | @api Methods | Total |
|-----------|-----------|-------------|-------|
| canvas2D | 21 | 99 | 120 |
| canvas3D | 22 | 92 | 114 |
| interactiveMap | 6 | 19 | 25 |
| annotateIt | 17 | 0 | 17 |
| internalLookup | 12 | 4 | 16 |

**Notable findings:**
- Total LWC count is 169 (vs. 163 estimated in research) — 6 additional components found
- canvas2D and canvas3D have massive method surfaces (99 and 92 @api methods respectively)
- utilitiesRDSceneSettings has 0 properties but 23 methods — acts as a pure method library
- Both canvas2D and canvas3D flagged as having extracted API documentation available

**Commit:** `1efefe3` — `feat(01-03): scan LWC and Aura component @api surfaces from source`

### Task 2: Scan all Aura components for public attributes
Scanned all Aura component directories (excluding EVT_* event directories), extracting aura:attribute definitions and access levels.

**Results:**
| Has Attributes | No Attributes | Global Access | Total |
|---------------|---------------|---------------|-------|
| 34 | 1 | 7 | 35 |

**Global access components (public API surface):**
AdvancedRenderer (266 attrs), SimpleRenderer (234 attrs), SceneSetup (26), AdvancedLayout (18), FileSelector (6), Settings (6), FlowData_Canvas2D_ReplaceSceneSettingsElement (4)

**Notable findings:**
- AdvancedRenderer has 266 attributes — the largest component surface in the entire package
- SimpleRenderer has 234 attributes — likely a simplified version of AdvancedRenderer
- Only 1 component (Settings_About) has zero attributes
- 7 components have `access="global"` making them available outside the package
- FlowWrapper and RecordDetailsApp are `.app` files (not `.cmp`) — correctly excluded

## Output

`source-components.md` (3,207 lines) — complete component API inventory with:
1. LWC summary table + per-component @api detail for all 136 components with @api
2. Aura summary table + per-component attribute detail for all 34 components with attributes
3. Lists of components without public APIs

## Deviations

- **LWC count differs from research:** Found 169 vs. 163 estimated. The 6 additional components were likely added since the research scan or were in subdirectories not counted.

## Issues Discovered

None.
