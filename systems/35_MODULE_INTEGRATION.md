# 35 — MODULE INTEGRATION CONTRACT

## Status
**Admin Canon v1.0 — Cross-Module Dependency Authority**

## Purpose
Modul ini adalah penghubung resmi antar-modul. Ia tidak menambah mekanik baru. Ia memformalkan hubungan yang sudah dinyatakan oleh modul Canon/Router sehingga satu modul dapat mengetahui sumber, konsumen, dan modul yang wajib ikut diproses ketika resolusi melintasi batas sistem.

### Authority
- INDEX.md = router/load-order utama.
- systems/27_MODULE_ROUTER.md = trigger → required/optional module.
- systems/35_MODULE_INTEGRATION.md = dependency/cross-module contract.
- Modul individual tetap menjadi sumber aturan mekaniknya sendiri.
- Jika konflik, aturan modul sumber + Core/Admin mengalahkan tabel integrasi ini.

## 1. Aturan Integrasi
1. Integrasi berarti ketergantungan data/resolusi, bukan otomatis semua modul harus di-fetch pada setiap turn.
2. Trigger menentukan modul REQUIRED melalui Module 27.
3. Jika aksi melintasi dua atau lebih domain di bawah, semua modul yang terdampak harus diverifikasi.
4. Modul konsumen tidak boleh menciptakan nilai yang sebenarnya disediakan modul sumber.
5. Jika source module tidak tersedia atau field wajib belum dapat dibuktikan, ikuti core/07_DATA_COMPLETENESS.md dan tahan resolusi bila diperlukan.
6. Persistence/save bukan sumber mekanik; gm/SAVE_PIPELINE.md hanya menyimpan hasil resolusi yang sudah sah.
7. Dynamic Generation tidak menggantikan fixed source atau source module.

## 2. Core Runtime Chain
| Domain | Source / Authority | Consumer / Dependent |
|---|---|---|
| Time | core/02_TIME_SYSTEM.md, lore/CALENDAR.md | Action, Vitality, Combat, Travel, Economy, Events, Gardening, Dynamic Generation |
| Action | core/03_ACTION_SYSTEM.md | seluruh gameplay action |
| Data completeness | core/07_DATA_COMPLETENESS.md | seluruh module yang memiliki field material |
| Character save | core/05_SAVE_INTEGRITY.md, core/06_ID_AND_SAVE_SYSTEM.md | seluruh persistence/state module |
| Trigger routing | systems/27_MODULE_ROUTER.md | Runtime Engine, Action Resolver, Boot |
| Cross-module dependency | Module 35 | Module Router + Runtime chain |

## 3. Gameplay Dependency Matrix
| Module | Integrasi resmi yang harus diikuti bila terdampak |
|---|---|
| 08 Organizations | 17 Reputation; 10 Economy; 15 Techniques; 26 NPC/Event/Quest; 22 Faction Relations; persistence 28 |
| 09 Cultivation | 11 Vitality; 12 Combat; 15 Techniques; Law Origin/State Validator |
| 10 Economy | 14 Items; 18 Loot; 08 Organizations; 17 Reputation; 02 Time; 21 Regional Economy; Character State |
| 11 Vitality | 12 Combat; 09 Cultivation; 03 Action; 02 Time; Character Save |
| 12 Combat | 09 Cultivation; 11 Vitality; 15 Techniques; 14 Items; 13 Monsters; 16 Karma; 17 Reputation; 08 Organizations; 02 Time; 24 Spirit Beast; 33 Formation |
| 13 Monsters | 12 Combat; 11 Vitality; 14 Items; 18 Loot; World Map/Travel/Time; 19 Ecosystem; 25 Dynamic Generation |
| 14 Items | 10 Economy; 18 Loot; 12 Combat; 15 Techniques; 08 Organizations; 17 Reputation; 24 Spirit Beast; 31 Crafting; 32 Alchemy; 33 Formation; 34 Refinement; Save Integrity |
| 15 Techniques | 09 Cultivation/Law; 12 Combat; 11 Vitality; 14 Items; 08 Organizations; Save Integrity |
| 16 Karma | Events; Faction/NPC reaction; 17 Reputation; Law/Technique only when source explicitly permits |
| 17 Reputation | 08 Organizations; 10 Economy; NPC/social/event resolution; 16 Karma where relevant |
| 18 Loot | 12 Combat; 13 Monsters; Events/Missions; 14 Items; 10 Economy; 08 Organizations; 16 Karma; 17 Reputation; 25 Dynamic Generation; Save Integrity |
| 19 Regional Monster Ecosystem | World Map; 20 Travel; Time; 11 Vitality; 12 Combat; 18 Loot; 10 Economy; 16 Karma; 17 Reputation; Events; 24 Spirit Beast; 25 Dynamic Generation |
| 20 Travel Routes | World Map; Time; Action; 11 Vitality; 10 Economy; 13 Monsters; Factions; Events; 09 Cultivation; 15 Techniques |
| 21 Regional Economy | 14 Items; 18 Loot; 08 Organizations; Factions; 20 Travel; Time; 17 Reputation; 16 Karma; Events |
| 22 Regional Faction Relations | 08 Organizations/Factions; 17 Reputation; 16 Karma; Economy/contracts; Events |
| 23 Gardening | 03 Action; Time; 14 Items; 10 Economy; 20 Travel where location/supply matters; 32 Alchemy when alchemical processing is actually involved |
| 24 Spirit Beasts | 13 Monsters; 18 Loot; 19 Ecosystem; 12 Combat; 14 Items; 15 Techniques; 09 Cultivation; 25 Dynamic Generation; Beast State/History + Save |
| 25 Dynamic Generation | 13 Monsters; 19 Ecosystem; 24 Spirit Beasts; 18 Loot; 26 NPC/Event/Quest; source modules supplying valid inputs |
| 26 Dynamic NPC/Event/Quest | 08 Organizations; 16 Karma; 17 Reputation; 22 Faction Relations; 29 NPC Persistence; 30 Event/Quest Persistence; World/Active Threads; source modules for rewards/requirements |
| 27 Module Router | INDEX; Core; all required gameplay modules; Module 35 |
| 28 Organization Persistence | 08 Organizations; 06 ID/Save; 05 Save Integrity; NPC/Quest/Event state when cross-entity changes occur |
| 29 NPC Persistence | 26 Dynamic NPC/Event/Quest; 08 Organizations; 16 Karma; 17 Reputation; 22 Relations; NPC State/History; Save Pipeline |
| 30 Event/Quest Persistence | 26 Dynamic NPC/Event/Quest; 08 Organizations; 16 Karma; 17 Reputation; 18 Loot/reward; Active Threads/World State; Save Pipeline |
| 31 Crafting/Forging | 14 Items; 10 Economy; material source; 32/34 only when the process explicitly crosses those domains |
| 32 Alchemy/Pills | 14 Items; material/herb source; 10 Economy; 31/34 only when the process explicitly crosses those domains |
| 33 Formation/Arrays | 14 Items; 09 Cultivation; 12 Combat; 31 Crafting; 34 Refinement; Formation persistence |
| 34 Artifact/Weapon Refinement | 14 Items; 25 Dynamic Generation when refinement result is dynamic; 31 Crafting; 32 Alchemy when alchemical material is used; 15 Techniques where explicitly relevant; Save/Origin |
| 35 Module Integration | No gameplay mechanics; it connects and constrains cross-module dependency resolution |

## 4. Production Cross-Module Contract
- New item / material processing → 31 + 14.
- Alchemy product → 32 + 14.
- Formation construction/operation → 33 + 14; add 31/09/12 when actually affected.
- Existing item refinement → 34 + 14; add 25 when the result is dynamically resolved; add 31/32/15 only when the actual process uses them. Module 34 method schema is authoritative for refinement method inputs, compatibility, qualification, process, allowed dimensions, bounds, outcome, and consumption/failure rules.
- Dynamic refinement → 34 + 25 + 14; material-source modules (31/32) become REQUIRED when they supply the actual refinement material/process.
- Cross-module production must preserve input → process → result provenance and before → after for every changed entity.

### Bounded Resolution Formula Dependency
Untuk dynamic refinement, dependency contract harus dipahami sebagai satu resolusi berurutan:
ITEM STATE (14) + MATERIAL PROPERTIES (14/source) + METHOD (34) + COMPATIBILITY/QUALIFICATION/PROCESS (34) → BOUNDED RESOLUTION (25) → STATE VALIDATION → SAVE.

Module 25 tidak menjadi source untuk missing bounds, effects, probabilities, atau bonuses. Module 34 tetap menjadi authority atas legal refinement space; Module 14 tetap menjadi authority atas Item/Material State. Jika required dependency tidak tersedia, gunakan RESOLUTION-BLOCKED.

## 5. Dynamic Entity Contract
- Monster/encounter: 25 + 13, then 19/12/18/24 as triggered.
- Spirit Beast: 25 + 24, then 13/19/12/18/14/15/09 as actually affected.
- NPC/Event/Quest: 26, then 28/29/30 and faction/reputation/karma/loot/economy sources as triggered.
- Dynamic output never becomes fixed Canon merely because another module consumes or persists it.

## 6. Dependency Resolution Gate
1. Detect the trigger.
2. Read Module 27.
3. Read Module 35 for dependency edges.
4. Fetch every affected REQUIRED source module.
5. Validate source availability and Data Completeness.
6. Resolve only with sourced inputs.
7. Apply state changes through the relevant persistence/save modules.
8. Verify every changed entity.

## 7. Anti-Orphan Rule
- Every material cross-module relationship must be represented here or in a more specific authoritative integration contract.
- A new module or new material dependency must update Module 35 and Module 27/INDEX when it changes trigger routing.
- Removing a dependency requires checking all consumers before deletion.
- Do not infer a dependency from narrative similarity alone.

## 8. Boundary Rule
This file does not override module mechanics, create missing Canon, or force irrelevant fetches. Ia memastikan hubungan Module A membutuhkan Module B menjadi hubungan repository-level yang eksplisit, bukan orphan statement di dalam satu file.

## 9A. Canon Flight Provenance Amendment
- `Realm 4+ → FLY-INTRINSIC-001` is a valid source of **intrinsic flight eligibility** and is distinct from Technique provenance.
- `systems/09_CULTIVATION.md` is the source authority for the Realm 4 intrinsic capability boundary.
- `systems/15_TECHNIQUES.md` remains the source authority for acquisition/provenance of named Flight Techniques.
- `systems/20_TRAVEL_ROUTES.md` consumes either the validated intrinsic capability or a separately validated flight method; it must not manufacture missing speed/range/duration values.
- Reaching Realm 4 must never be recorded as acquisition of a named flight technique.