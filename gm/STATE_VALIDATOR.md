# Runtime State Validator

## Tujuan
Memastikan state dan persistent memory merupakan hasil transisi sah, termasuk dynamic NPC/Event/Quest, Monster/Beast/Loot, Cultivation Law, Technique provenance, organization state, shared-world scope, dan seluruh production process Crafting/Alchemy/Formation/Refinement.

## Validation Order
1. Repository/INDEX freshness.
2. Module Router REQUIRED modules tersedia.
3. Current State/History/World Time sesuai entity ID.
4. Pre-resolution checks.
5. Resolution-specific checks.
6. Post-resolution before → after.
7. Persistence/Origin/ID checks.
8. Write-back status.

## Pre-Resolution Validation
- [ ] World Time valid dan tidak mundur.
- [ ] Active Character ID, lokasi, target, jarak, resource, Realm/Stage, teknik, equipment, inventory, dan kondisi valid.
- [ ] Informasi yang digunakan memang diketahui Character.
- [ ] Relevant event/faction/NPC/quest/thread/source telah dimuat melalui Module Router.
- [ ] Durasi aksi memenuhi Time System.
- [ ] Character History cocok dengan Active Character ID.
- [ ] Dynamic generation memenuhi Module 25/26 input dan formula gate bila dipakai.
- [ ] Jika production process relevan, Module 31/32/33/34 yang REQUIRED telah dimuat.

## Entity Isolation
- [ ] Setiap perubahan memiliki Entity ID yang tepat.
- [ ] Character State tidak menerima fakta milik NPC/Beast/Quest/Event/Production Entity secara keliru.
- [ ] NPC/Beast/Quest/Event tidak menerima perubahan hanya karena Character menginginkannya.
- [ ] Shared World State hanya menerima fakta yang benar-benar berscope shared.
- [ ] Generated entity tidak menjadi Global Canon tanpa dasar Admin/Canon.
- [ ] Production result tidak menjadi Global Canon hanya karena berhasil runtime.

## Cultivation Law / Technique
- [ ] Law aktif memiliki Law Origin tervalidasi.
- [ ] Source type, source, acquisition method, requirements, training/insight, resolution tidak ditebak.
- [ ] Law Origin berstatus `VALIDATED & ACTIVE` sebelum Law dipasang aktif.
- [ ] Setiap teknik memiliki Technique Origin valid.
- [ ] Law tidak otomatis memberikan teknik.
- [ ] Technique requirements/mastery/effect/cost tidak diimprovisasi.
- [ ] Before/After + Origin tercatat untuk perubahan material.

## Dynamic NPC
- [ ] Context lokasi/role/agenda/knowledge valid.
- [ ] NPC tidak diberi lore/teknik/bloodline/realm tinggi tanpa dasar.
- [ ] NPC_ID unik/stabil bila persistent.
- [ ] State/History memiliki before → after dan Origin bila material.
- [ ] Knowledge sesuai pengalaman dan akses NPC.

## Dynamic Event
- [ ] Pressure source dan modifier sah.
- [ ] Scope Personal/Local/Regional/Global valid.
- [ ] Local tidak naik Regional/Global tanpa trigger Canon/Admin.
- [ ] World/Scheduled Event memakai registry dan trigger resmi.
- [ ] EVT_ID unik/stabil bila persistent.
- [ ] Event state sesuai scope dan Origin.

## Dynamic Quest
- [ ] Source/need valid.
- [ ] Objective, target, method, risk/cost, success/failure condition valid.
- [ ] QST_ID unik/stabil bila lintas-turn.
- [ ] Lifecycle sesuai Module 26.
- [ ] Deadline memiliki dasar waktu.
- [ ] Reward provenance valid: Fixed Canon/Event/Mission → valid source → Dynamic Loot → `RESOLUTION-BLOCKED`.
- [ ] Tidak ada reward, breakthrough, item, uang, teknik gratis atau automatic Realm scaling.

## Dynamic Creature / Loot
- [ ] Encounter Pressure dan Threat Score berasal dari Module 25.
- [ ] Tier ceiling dipatuhi; Tier ≠ Realm.
- [ ] Spirit Beast mengikuti Module 24.
- [ ] Loot hanya setelah valid acquisition/resolution.
- [ ] Quantity/quality mengikuti formula/fixed table yang berlaku.
- [ ] Ownership/provenance memiliki Origin.

## Organization / Faction
- [ ] Gunakan database Canon dan individual organization file bila tersedia.
- [ ] Individual file tidak boleh bertentangan dengan registry.
- [ ] Struktur/jabatan/relasi hanya dianggap Canon bila tersimpan sebagai Admin Canon.
- [ ] Faction membership, rank, contract, promotion, expulsion, dan akses tidak berubah tanpa sebab/resolusi sah.
- [ ] Data yang belum tersedia menggunakan status kelengkapan resmi dari `core/07_DATA_COMPLETENESS.md`.

## Crafting / Forging — Module 31
- [ ] Material yang digunakan benar-benar tersedia dan memiliki valid Origin.
- [ ] Recipe/blueprint/procedure memiliki source yang sah.
- [ ] Crafter memiliki qualification/knowledge yang valid bila diwajibkan.
- [ ] Tool/workspace tersedia dan sesuai proses bila diwajibkan.
- [ ] Resource cost dan waktu memiliki source mekanis yang valid.
- [ ] Process mengikuti recipe/source dan tidak memakai hidden modifier.
- [ ] Resolution dapat success, partial, failure, atau defective result; tidak ada automatic success.
- [ ] Quality/result tidak melebihi source/Canon ceiling.
- [ ] Item baru mendapat Item State dan Item Origin sesuai Module 14.
- [ ] Material yang dikonsumsi tercermin pada before → after dan Origin.

## Alchemy / Pills — Module 32
- [ ] Herb/material tersedia dan memiliki valid Origin.
- [ ] Formula/procedure memiliki source yang sah.
- [ ] Alchemist qualification/knowledge valid.
- [ ] Furnace/tool dan proses sesuai requirement.
- [ ] Cost dan waktu valid.
- [ ] Failure/deviation mungkin terjadi bila proses mendukungnya; tidak ada automatic success.
- [ ] Pill quality/quantity mengikuti formula/fixed source; tidak ditebak untuk memberi reward.
- [ ] Effect/potency/side effect/defect hanya berasal dari source yang valid; status belum tersedia mengikuti Data Completeness.
- [ ] Hasil Pill/Product mendapat Item State dan Item Origin sesuai Module 14.

## Formation / Array — Module 33
- [ ] Blueprint/procedure memiliki source sah.
- [ ] Builder/operator memiliki knowledge/qualification yang valid.
- [ ] Array materials dan Array Core tersedia serta memiliki Origin bila diwajibkan.
- [ ] Location/environment sesuai requirement.
- [ ] Construction dan activation dipisahkan dari blueprint ownership/knowledge.
- [ ] State formation mencerminkan resolusi aktual.
- [ ] Range/effect/cost/stability hanya berasal dari source/Admin Canon.
- [ ] Combat interaction mengikuti Module 12 dan tidak memberi automatic hit/kill/dodge/counter.
- [ ] Disruption, repair, collapse, atau destruction memiliki sebab/resolusi sah.
- [ ] Formation dan Array Core yang persisten memiliki identity/state/history yang dapat ditelusuri.

## Artifact / Weapon Refinement — Module 34
- [ ] Existing Item benar-benar ada dan state-nya terbaru.
- [ ] Refinement method memiliki source yang sah.
- [ ] Refiner qualification valid bila diwajibkan.
- [ ] Material/tool/workspace/cost tersedia dan valid.
- [ ] Refinement tidak diperlakukan sebagai pembuatan item baru tanpa dasar.
- [ ] Quality/property/condition hanya berubah jika method mendukungnya.
- [ ] Category/grade/tier tidak naik otomatis.
- [ ] Failure dapat mempertahankan, merusak, atau menghancurkan item hanya jika mekanisme mengizinkannya.
- [ ] Ownership tidak berubah otomatis karena refinement.
- [ ] Existing Item Origin dipertahankan dan refinement menambahkan Origin/History baru.

## Production Cross-Module Integrity
- [ ] Batas Module 31 → item baru, Module 32 → alchemical product, Module 33 → formation/array, Module 34 → existing item modification dipatuhi.
- [ ] Jika satu aksi melintasi beberapa production module, seluruh REQUIRED module diproses.
- [ ] Tidak ada double-consumption material.
- [ ] Tidak ada duplicate item/result akibat multi-step resolution.
- [ ] Before → after konsisten pada Character, Item, Material, Formation, Array Core, dan entity lain yang terdampak.
- [ ] Provenance chain dapat ditelusuri dari input → process → result.
- [ ] Production result tidak memberikan ability/effect/quality/tier yang tidak memiliki source.

## Post-Resolution
- [ ] Time, cost, HP/Qi/Stamina/Satiety, lokasi, inventory, equipment, currency, Karma/Reputation tepat.
- [ ] NPC reaction sesuai knowledge/agenda/autonomy.
- [ ] Event berubah hanya melalui trigger/resolution sah.
- [ ] Quest progress/reward sesuai resolusi.
- [ ] Generated material memiliki ID/Origin/persistence sesuai scope.
- [ ] History tiap entity hanya mencatat fakta entity tersebut.
- [ ] Shared State/Timeline/Active Threads hanya fakta shared terkonfirmasi.
- [ ] No hidden time-skip, retcon, cross-entity overwrite.
- [ ] Write-back status tidak dipalsukan.

## Invalid State
Jika pemeriksaan material gagal, jangan menerapkan state. Kembali ke nilai terakhir terverifikasi atau tahan resolusi. Jangan menulis memory yang bergantung pada state gagal.


## Data Completeness Enforcement
- [ ] Setiap field material yang belum tersedia memiliki status dari `core/07_DATA_COMPLETENESS.md`.
- [ ] `CANON-ESTABLISHED` memiliki sumber Canon/Admin yang dapat diverifikasi.
- [ ] `STATE-ESTABLISHED` berasal dari Current State yang terverifikasi.
- [ ] `RUNTIME-GENERATED` memiliki module/formula/trigger/input yang sah dan tidak dibuat hanya untuk mengisi field.
- [ ] `NOT-INSTANTIATED` tidak diperlakukan sebagai entity/record aktif.
- [ ] `UNRESOLVED` tidak diperlakukan sebagai fakta dan tidak diubah menjadi nilai konkret tanpa source sah.
- [ ] `RESOLUTION-BLOCKED` digunakan bila required input hilang tanpa fallback resmi.
- [ ] Tidak ada nilai yang berasal dari tebakan, plausibility, cache lama, real-world fallback, atau player demand.
- [ ] Narrative/dialogue tidak dipakai sebagai bukti Canon/State tanpa source dan resolusi yang sah.


## Dynamic Refinement Validation Gate
- [ ] Existing Item State is current and valid.
- [ ] Material ID, quantity, Origin, and refinement-relevant properties have a valid source.
- [ ] Refinement Method defines or references the allowed property dimensions, compatibility, bounds, and outcome mechanism.
- [ ] Module 25 is used only for concrete runtime selection inside those bounds.
- [ ] No property, grade, tier, category, ability, affinity, or effect is inferred from rarity/name/market value/Realm/plausibility.
- [ ] Missing required refinement source/input results in `RESOLUTION-BLOCKED`.
- [ ] Before → After covers Item, consumed Material, and every changed resource/entity.
- [ ] Existing Item Origin is preserved and refinement adds new Origin/History.
- [ ] Dynamic result remains `RUNTIME-GENERATED`, not Global Canon.


## Bounded Resolution Validation Gate
- [ ] Resolver context contains Item State, Material Property Records, Method Record, Compatibility, Qualification, and Process Conditions.
- [ ] All required inputs are sourced and pass the relevant module gates before result selection.
- [ ] Only Method-allowed property dimensions are changed.
- [ ] Every selected result lies inside the intersection of applicable Item, Material, and Method constraints/bounds.
- [ ] An absent/unsourced bound is not replaced by a guessed number, default, or narrative modifier.
- [ ] Outcome selection follows the Method Record outcome mechanism exactly; no hidden roll/probability/multiplier is introduced.
- [ ] `SUCCESS`, `PARTIAL`, and failure states are used only when the source mechanism permits them.
- [ ] `RESOLUTION-BLOCKED` is preserved when a required mechanism or bound cannot be established; it is not silently converted to success/failure.
- [ ] Before/After contains every changed Item, Material, resource, and relevant entity in one transaction.
- [ ] No numeric bonus, quality/grade/tier increment, durability change, ability/effect, or Realm scaling is inferred without Canon/source.


## AERIAL-DISTANCE STATE VALIDATION GATE
For flight-travel resolutions, validate:
- [ ] `systems/20_TRAVEL_ROUTES.md` was fetched from current repository state.
- [ ] Flight eligibility is validated independently from aerial distance.
- [ ] Flight speed has a valid Canon/State source.
- [ ] Origin and Destination are valid location nodes for the requested travel.
- [ ] The consumed aerial-distance record exists in the AERIAL-DISTANCE Canon Registry.
- [ ] `AERIAL_DISTANCE_BASELINE` is used exactly as the registered Canon Li value; no conversion from surface route distance occurs.
- [ ] No straight-line geometry, coordinate estimate, narrative plausibility, or unregistered route chain was used.
- [ ] If no exact record exists, aerial distance remains `UNRESOLVED` and numeric duration is not applied.
- [ ] Any detour/barrier/weather/airspace/encounter modifier has an independent valid source; otherwise no numeric modifier is introduced.
- [ ] The resolution records `AERIAL_DISTANCE_ID` + source ID when a registry entry is consumed.
- [ ] Before → After includes any actual time/location/resource changes only after the flight resolution passes this gate.


## ITEM_GRADE / GRADE_LEVEL VALIDATION GATE
- [ ] Every Item Canon/Instance has a resolvable ITEM_GRADE and GRADE_LEVEL, or each missing field is explicitly UNRESOLVED.
- [ ] ITEM_GRADE and GRADE_LEVEL come from Module 14 or an explicit authoritative variant/output source.
- [ ] ITEM_GRADE and GRADE_LEVEL are not inferred from Character Realm, name, price, rarity, quantity, quality, condition, or narrative description.
- [ ] Quality, condition, durability, rarity, and grade remain separate fields.
- [ ] No grade or level increase occurs without an explicit method/source and bounded transition.
- [ ] Loot/crafting/alchemy/refinement outputs do not invent or silently upgrade grade or level.
- [ ] A missing required grade or level produces RESOLUTION-BLOCKED rather than a guessed value.
