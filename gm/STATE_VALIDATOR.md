# Runtime State Validator

## Tujuan
Memastikan state dan persistent memory merupakan hasil transisi sah, termasuk dynamic NPC/Event/Quest, Monster/Beast/Loot, Cultivation Law, Technique provenance, organization state, dan shared-world scope.

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

## Entity Isolation
- [ ] Setiap perubahan memiliki Entity ID yang tepat.
- [ ] Character State tidak menerima fakta milik NPC/Beast/Quest/Event.
- [ ] NPC/Beast/Quest/Event tidak menerima perubahan hanya karena Character menginginkannya.
- [ ] Shared World State hanya menerima fakta yang benar-benar berscope shared.
- [ ] Generated entity tidak menjadi Global Canon tanpa dasar Admin/Canon.

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
- [ ] Reward provenance valid: Fixed Canon/Event/Mission → valid source → Dynamic Loot → `???`.
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
- [ ] `???` tetap unknown bila tidak ada sumber.

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
