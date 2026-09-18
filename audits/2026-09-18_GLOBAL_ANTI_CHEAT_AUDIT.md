# 2026-09-18 GLOBAL ANTI-CHEAT / GM EXPLOIT AUDIT

## Scope
Repository-wide audit focused on:
- rule contradictions and cross-module precedence;
- GM-controlled randomness and reroll risk;
- numeric modifier stacking/invention;
- dynamic encounter/event/loot resolution;
- state/save/Origin enforcement;
- generated-content boundaries;
- structural/placeholder CI coverage.

## Verified Baseline
Fresh repository state audited from `main` after the latest maintenance commits.

GitHub Actions at the audited HEAD:
- `placeholder-lint`: PASS
- `structural-reference-lint`: PASS

## Findings

### 🔴 Critical — GM-controlled random outcomes
Dynamic systems used d100/random selection but did not previously require a verifiable RNG source, a roll identity, or a no-reroll rule. This left a path for post-hoc result selection by the GM.

**Fix:** `core/04_ANTI_CHEAT.md` now requires RNG Source, ROLL_ID, purpose, input/seed context, result, world time, and entity context where applicable. GM-selected rolls, post-outcome rerolls, and result substitution are prohibited. Missing verifiable RNG blocks the random-dependent resolution.

### 🔴 Critical — Unbounded numeric modifier stacking
Module 25 and Module 26 used Sigma Modifier formulas but did not define a repository-level rule preventing duplicate categories or renamed duplicate conditions from stacking.

**Fix:** Core Anti-Cheat now requires source-defined modifier identity, trigger, value/bound, and stacking rule. Same-category modifiers cannot stack unless the source explicitly permits it.

### 🟠 High — Loot score inputs not executable by themselves
Module 25 names Habitat Score, Harvest/Defeat Method, Condition, and Special Event as 0–20 loot components, but the repository did not contain a complete numeric scoring registry for those components.

**Fix:** these fields are now source-gated. GM may not choose 0–20 values by intuition. If a required score lacks a source, numeric Loot Potential is RESOLUTION-BLOCKED unless a fixed table or another valid source independently resolves the loot.

### 🟠 High — Dynamic NPC/Event modifier ambiguity
Module 26 used Social/Event modifier ranges without a complete source registry.

**Fix:** modifier source/trigger/value/bound/stacking rules are now mandatory; missing required numeric values cannot be guessed.

### 🟢 Confirmed protections
- Fresh INDEX requirement exists and is enforced in the runtime contract.
- Required-module fetch failure blocks dependent resolution.
- Player claim is not a state source.
- Current Character State is separated from players.md.
- Origin/History and Before→After are required for material state changes.
- Multi-entity save integrity is defined.
- Dynamic content does not automatically become Global Canon.
- Custom/Admin content cannot bypass Core integrity under the new boundary.
- Loot ownership/provenance and item identity gates are present.
- Monster and Spirit Beast persistence are separated from Character state.

## Remaining 🟡 Work

1. A dedicated executable RNG implementation/source is still an infrastructure dependency. The repository now forbids GM-selected random values; a runtime RNG source must be supplied by the execution environment before randomized resolutions are allowed.
2. Numeric modifier registries should be added only when Admin has real Canon values/conditions to establish.
3. Loot score registries should be added only from explicit Admin/source rules. Until then, fixed tables or non-numeric source-specific outcomes remain valid.
4. CI currently verifies concrete Markdown references, registry/state conventions, and legacy placeholder vocabulary, but does not prove semantic equivalence of every cross-module formula. Runtime semantic audits remain necessary.

## Anti-Cheat Runtime Contract

`FRESH INDEX → REQUIRED SOURCES → VALIDATE → RNG/MODIFIER SOURCE GATE → RESOLVE → BEFORE/AFTER → ORIGIN/HISTORY → SAVE → WRITE-BACK VERIFY → RESPONSE`

No state-changing resolution may bypass a failed integrity gate.

## Status

**🟡 GLOBAL ANTI-CHEAT / GM EXPLOIT AUDIT — HARDENING APPLIED / INFRASTRUCTURE DEPENDENCIES OPEN**

This audit is separate from the previously closed Global Structural Audit. The earlier closure remains historical; this is a new security/integrity scope focused on GM exploit resistance.
