# TianDao-World — P0/P1 Remediation & Cross-Module Numeric Audit

**Date:** 2026-09-25  
**Scope:** Gardening canon conflict, Custom/Event load-order conflict, and cross-module numeric integrity.  
**Repository:** `aesher-gg/TianDao-World`  
**Status:** **REMEDIATED / AUDIT CLOSED WITH NON-BLOCKING DATA GAPS**

## 1. P0 — Gardening Growth Limit Conflict

### Finding
`systems/23_GARDENING.md` contained contradictory limits:
- ordinary crops: 7 days vs 10 days;
- spiritual crops: 15 days vs 60 days.

### Remediation
The authoritative gameplay limits are now normalized to:

| Crop class | Standard maximum |
|---|---:|
| Ordinary crop | **10 in-game days** |
| Spiritual crop | **60 in-game days (2 months)** |

The same values are used in the runtime rule section. No 7-day or 15-day gameplay cap remains as an active rule.

### Boundary
These are maximum gameplay bounds, not automatic growth durations. Actual growth still requires a valid growth source/rate and valid time passage. Admin override remains possible only when explicitly documented.

## 2. P1 — Custom/Event Load-Order Conflict

### Finding
`core/00_CORE_RULES.md` stated that `39_CUSTOM_EVENTS` must always be loaded at session start, while `INDEX.md` and Module 27 establish a trigger-dependent **REQUIRED modules only** model.

### Remediation
The Core rule now establishes:
- `events/39_CUSTOM_EVENTS.md` and `custom/40–42` are Admin-managed sources;
- they are fetched when the current trigger/action requires them;
- they are not an always-load exception;
- relevant custom content can override official data only within its explicitly defined Admin scope;
- uncatalogued content remains non-canonical.

`INDEX.md` now explicitly states that custom content and official event sources are fetched only when the trigger/action requires them, and that `39_CUSTOM_EVENTS.md` is not an always-load exception.

### Runtime hierarchy
`INDEX → Core → Module Router → Required sources → Validation → Resolution`

This removes the load-order contradiction without weakening Admin Custom authority.

## 3. P1 — Cross-Module Numeric Audit

### 3.1 Time
**Result: PASS**

`core/02_TIME_SYSTEM.md` and `core/03_ACTION_SYSTEM.md` consistently enforce:
- normal non-cultivation action ≤ 3 hours/turn;
- sleep is the explicit exception;
- no hidden time skip;
- long travel uses checkpoints;
- cultivation has separate long-retreat rules.

No conflicting general action-duration cap was found in the audited source chain.

### 3.2 Satiety
**Result: PASS**

`systems/11_VITALITY.md` defines:
- Mortal FastingMultiplier ×4;
- 24 hours to zero;
- drain = 100 / 24 = 4.1667% per hour;
- state thresholds 51–100 Not Hungry, 1–50 Hungry, 0 Starving.

`core/02_TIME_SYSTEM.md` explicitly delegates sleep satiety processing to this canonical formula.

No competing hunger threshold or sleep-drain formula was found in the audited core/action/vitality chain.

### 3.3 Stamina
**Result: PASS WITH EXPLICIT BOUNDARY**

Stamina capacity is defined by Realm/Stage in Module 11, with only sourced modifiers permitted.

There is intentionally **no universal hidden stamina-cost formula**. Action/production modules consume stamina only when a specific source establishes a cost.

This is treated as a deliberate Data Completeness boundary, not a missing number to be invented.

### 3.4 Cultivation
**Result: PASS**

Module 09 establishes:
`Mortal → Dantian → Realm 1 → 10 Meridian → Breakthrough → Realm 2`

Realm/Stage scaling is sourced. Mortal is not treated as a cultivation Realm.

No audited cross-module rule permits a Realm jump, automatic breakthrough, or automatic stamina restoration.

### 3.5 Combat
**Result: PASS**

Module 12 defines the baseline:
- AttackPower = QiCap × 0.15 × LawAttackMultiplier;
- PassiveDefense = QiCap × 0.05;
- HitChance = clamp(70% + RealmIndex gap × 5%, 10%, 95%).

Technique/item/environment modifiers require their own source.

No audited rule permits an unsourced damage multiplier or automatic hit.

### 3.6 Travel
**Result: PASS**

Module 20 defines:
- official distance unit = Li;
- 1 Li = 500 m;
- baseline speeds for ordinary travel methods;
- duration = distance / effective speed + sourced obstacles;
- unsourced numeric obstacle modifiers are prohibited;
- flight requires separate eligibility, speed, and aerial-distance sources.

Module 35 confirms the same dependency chain.

No audited source permits deriving missing flight distance/speed from surface routes or narrative plausibility.

### 3.7 Economy
**Result: PASS / SOURCE-DEPENDENT BY DESIGN**

Module 10 does not create a universal arbitrary price formula. Prices come from item, region, faction, market state, supply/demand and other valid sources.

Module 21 provides regional commodity/economic structure but explicitly does not create a fixed price list.

Therefore the absence of a universal price number is intentional. GM must not invent a price when the required market source is missing.

### 3.8 Crafting / Forging
**Result: PASS**

Module 31 requires:
`Material → Recipe → Qualification → Tool/Workspace → Cost → Process → Validation → Resolution → Result → Origin → Save`

Cost and process time are source-dependent. No hidden stamina/time/currency cost is allowed.

### 3.9 Alchemy
**Result: PASS**

Module 32 requires:
`Material → Formula → Qualification → Furnace/Tool → Process → Validation → Resolution → Result`

Existing formulas have explicit process/cost where applicable. Missing required output identity is correctly treated as RESOLUTION-BLOCKED rather than being invented.

### 3.10 Refinement
**Result: PASS**

Module 34 defines the legal refinement boundary. The established baseline method does not introduce hidden:
- damage bonus;
- defense bonus;
- quality/tier escalation;
- probability;
- Realm scaling;
- extra time;
- extra stamina/Qi cost.

Character readiness remains separate from existence of the global method source.

## 4. Gardening Numeric Boundary

**Result: PASS WITH NON-BLOCKING SOURCE GAP**

Gardening status ranges are 0–100, but the range itself is not a growth-rate formula.

Therefore:
- passive growth requires a sourced rate;
- harvest quantity/quality requires a valid formula/source;
- unsupported `+10 Growth`, `+20 Growth`, etc. remain prohibited;
- if required numeric input is absent, runtime must use `UNRESOLVED` or `RESOLUTION-BLOCKED`.

This is intentional anti-cheat behavior, not a reason to invent a universal growth formula.

## 5. Final Audit Decision

### Blocking issues
- **P0 Gardening contradiction:** RESOLVED.
- **P1 Custom/Event load-order contradiction:** RESOLVED.

### Remaining non-blocking boundaries
1. Gardening growth-rate/yield formulas remain source-dependent.
2. Universal stamina-cost formula does not exist; action-specific sources control costs.
3. Economy prices remain market/source-dependent.
4. Dynamic systems require their RNG/modifier contracts rather than hidden fallback numbers.

### Final Status

**P0: CLOSED**  
**P1 Load-Order: CLOSED**  
**P1 Cross-Module Numeric Audit: PASS WITH EXPLICIT DATA-COMPLETENESS BOUNDARIES**

No audited cross-module conflict currently requires a new numeric formula merely to make gameplay continue.
