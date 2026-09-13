# Runtime State Validator

## Tujuan
Memastikan state dan persistent memory merupakan hasil transisi sah, termasuk dynamic NPC/Event/Quest dan Monster/Beast/Loot, tanpa retcon, entity leakage, atau reward tanpa provenance.

## Pre-Resolution Validation
- [ ] World Time valid dan tidak mundur.
- [ ] Active Character ID, lokasi, target, jarak, resource, Realm/Stage, teknik, equipment, inventory, dan kondisi valid.
- [ ] Informasi yang digunakan memang diketahui Character.
- [ ] Relevant event/faction/NPC/quest/thread/source telah dimuat.
- [ ] Durasi aksi memenuhi Time System.
- [ ] Character History cocok dengan Active Character ID.
- [ ] Dynamic generation, bila dipakai, memenuhi Module 25/26 input dan formula gate.

### Dynamic NPC
- [ ] NPC fixed/Canon berasal dari source Canon yang benar.
- [ ] NPC generated memiliki konteks lokasi/role/agenda/knowledge boundary yang valid.
- [ ] Generated NPC tidak diam-diam menjadi tokoh Canon besar, pemimpin faction, grandmaster, bloodline/teknik rahasia, atau lore unik tingkat tinggi.
- [ ] NPC_ID unik/stabil bila persistence diperlukan.
- [ ] NPC State/History memiliki before → after dan Origin bila material.
- [ ] Realm/Stage NPC tidak ditebak.

### Dynamic Event
- [ ] Local Event memiliki pressure source dan modifier yang sah.
- [ ] Local Event tidak dinaikkan menjadi Regional/Global tanpa Canon/Admin trigger.
- [ ] World Event memakai registry dan trigger Canon resmi.
- [ ] Scheduled Event memakai jadwal/access yang benar.
- [ ] EVT_ID unik/stabil bila local event persisten.
- [ ] Event state/log sesuai scope dan Origin bila material.

### Dynamic Quest
- [ ] Quest memiliki source/need yang valid.
- [ ] Objective, target, method, risk/cost, success/failure condition valid.
- [ ] Quest tidak dianggap tersedia hanya karena Player meminta.
- [ ] QST_ID unik/stabil bila lintas-turn.
- [ ] Quest State dan Active Threads sesuai scope.
- [ ] Deadline hanya ada jika memiliki dasar waktu yang sah.
- [ ] Reward memiliki provenance: fixed Canon/Event/Mission → valid Item/Economy/Technique/Contract source → Dynamic Loot → `???`.
- [ ] Tidak ada item/uang/teknik/breakthrough gratis atau scaling reward berdasarkan Realm Character.

### Dynamic Creature / Loot
- [ ] Encounter Pressure dan Threat Score berasal dari Module 25.
- [ ] Tier ceiling dipatuhi; Tier ≠ Realm.
- [ ] Spirit Beast mengikuti Module 24, termasuk BEAST_ID/relationship/taming/ownership/contract.
- [ ] Loot hanya muncul setelah valid acquisition/resolution.
- [ ] Quantity/quality mengikuti formula Module 25/18 atau fixed table yang memang berlaku.
- [ ] Item ownership/provenance memiliki Origin.

## Post-Resolution Validation
- [ ] Waktu, cost, HP/Qi/Stamina/Satiety, lokasi, inventory, equipment, currency, Karma/Reputation dan status berubah tepat.
- [ ] NPC reaction sesuai knowledge, agenda, condition, dan autonomy.
- [ ] Event berubah hanya melalui trigger/resolution yang sah.
- [ ] Quest status/progress/reward sesuai resolusi; failure tidak memberi reward otomatis.
- [ ] Semua generated material memiliki entity ID, Origin, dan persistence sesuai scope.
- [ ] Character History hanya fakta Character; NPC/Quest/Event/Beast history hanya fakta entity masing-masing.
- [ ] Shared World State/Timeline/Active Threads hanya memuat fakta shared yang terkonfirmasi.
- [ ] No hidden time-skip, no retcon, no cross-entity overwrite.
- [ ] Write-back status diketahui dan tidak dipalsukan.

## Invalid State
Jika pemeriksaan material gagal, jangan menerapkan state. Kembali ke nilai terakhir yang terverifikasi atau tahan resolusi/minta klarifikasi. Jangan menulis memory yang bergantung pada state gagal.
