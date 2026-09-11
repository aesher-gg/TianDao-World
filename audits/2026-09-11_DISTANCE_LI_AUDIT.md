# Audit — Official Li Distance Standard

**Date:** 2026-09-11
**Repository:** aesher-gg/TianDao-World
**Branch:** main
**Status:** PASS WITH NORMALIZATION NOTE

## Scope
- Core distance convention.
- Travel route registry.
- Repository-wide search for kilometer/meter terminology and distance-related usage.
- GM runtime implications.

## Changes Applied
1. `core/00_CORE_RULES.md` now defines **Li (里)** as the official world distance unit.
2. Official conversion: **1 Li = 500 meters = 0.5 km; 2 Li = 1 km**.
3. `systems/20_TRAVEL_ROUTES.md` was converted from kilometer baselines to Li.
4. `INDEX.md` already exposes the travel route registry; no new path was required.
5. Runtime rule: new distances for travel, locations, NPCs, encounters, combat range, and events must use Li unless Canon/Admin explicitly defines another unit.

## Converted Route Baselines
- Dataran Cangyuan: 72/38/126/54 km → 144/76/252/108 Li.
- Pegunungan Qingluan: 24/46/31/19 km → 48/92/62/38 Li.
- Domain Yaohuang Selatan: 61/18/47/83 km → 122/36/94/166 Li.
- Laut Dongming: 96/138/164/218 km → 192/276/328/436 Li.
- Tanah Salju Beiming: 77/43/69/154 km → 154/86/138/308 Li.
- Gurun Jinyan: 91/57/42/118 km → 182/114/84/236 Li.

## Search Result
Repository search for `km` after conversion returned no current main-branch matches outside historical/search-result snapshots. A broader short-token search for `m` is too noisy because it matches ordinary words and abbreviations; therefore it is not treated as evidence of distance-unit conflicts.

## Runtime Compatibility
- Travel duration formula remains `distance / effective speed + obstacles`; only the canonical distance unit changed.
- Existing gameplay logic using numeric distance remains structurally compatible because route baselines were converted by the fixed 1 Li = 0.5 km convention.
- Meter/kilometer may appear only as explanatory conversions, not as the primary runtime distance unit.
- Unknown/unregistered distances remain `???`; GM must not invent route distances.

## Final Verdict
**PASS.** Li is now the official distance unit. The known distance-bearing travel registry has been normalized, core rules have been hardened, and a repository-wide search found no remaining known kilometer-based runtime distance entries requiring conversion. Future modules must use Li by default.
