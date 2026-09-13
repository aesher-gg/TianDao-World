# Runtime State Validator

## Tujuan
Memastikan state dan persistent memory merupakan hasil transisi sah, termasuk dynamic NPC/Event/Quest, Monster/Beast/Loot, serta Cultivation Law dan Technique provenance, tanpa retcon, entity leakage, atau reward/ability tanpa provenance.

## Pre-Resolution Validation
- [ ] World Time valid dan tidak mundur.
- [ ] Active Character ID, lokasi, target, jarak, resource, Realm/Stage, teknik, equipment, inventory, dan kondisi valid.
- [ ] Informasi yang digunakan memang diketahui Character.
- [ ] Relevant event/faction/NPC/quest/thread/source telah dimuat.
- [ ] Durasi aksi memenuhi Time System.
- [ ] Character History cocok dengan Active Character ID.
- [ ] Dynamic generation, bila dipakai, memenuhi Module 25/26 input dan formula gate.

### Cultivation Law / Law Origin
- [ ] Cultivation Law aktif memiliki Law Origin yang tervalidasi, kecuali memang `???` karena source data belum tersedia.
- [ ] Law Origin memiliki source yang nyata dan sesuai Canon/Admin: source type, source, acquisition method, dan resolution tidak boleh ditebak.
- [ ] Requirements/training/insight yang diwajibkan telah dipenuhi atau resolusi sah telah membuktikan pengecualian.
- [ ] World Time dan Origin Reference tersedia untuk perubahan material bila data tersebut diwajibkan.
- [ ] Law Origin berstatus `VALIDATED & ACTIVE` sebelum Law baru dipasang sebagai aktif.
- [ ] Law Origin tidak diperlakukan sebagai stat bonus.
- [ ] Perubahan Law memiliki before/after, cause, resolution, source, dan Origin Log.
- [ ] Law baru tidak muncul hanya karena Player meminta, Realm cukup tinggi, atau karakter memiliki teknik terkait.
- [ ] `???` tidak boleh dipertahankan jika source Canon/Admin/History yang valid sudah menentukan asal Law.

### Technique / Technique Origin
- [ ] Setiap teknik baru memiliki Technique Origin yang valid.
- [ ] Source Type dan Source sesuai sumber nyata.
- [ ] Jika teknik berbasis Law, Cultivation Law aktif dan Law Origin tervalidasi.
- [ ] Memiliki Law tidak dianggap otomatis memberikan semua teknik terkait.
- [ ] Requirements, training/insight, mastery, effect, dan cost tidak dilewati atau diimprovisasi tanpa definisi sumber.
- [ ] Technique Origin memiliki resolution/timestamp dan Origin Reference bila material.
- [ ] Klaim teknik tanpa asal ditolak.

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
