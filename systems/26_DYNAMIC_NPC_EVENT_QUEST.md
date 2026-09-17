# 26 — DYNAMIC NPC, EVENT & QUEST GENERATION

> **Status:** Admin Canon v1.0
> **Tujuan:** memberi Qwen GM kerangka procedural untuk menghasilkan NPC, local event, dan quest secara dinamis tanpa mengubah TianDao-World menjadi katalog tertutup.

## 0. Prinsip Utama
Admin menetapkan formula, batas, identitas sistem, validasi, dan persistence. Qwen GM menentukan hasil konkret saat runtime berdasarkan input yang tersedia. Generated result bukan otomatis Global Canon.

Urutan input:
`Canon/Admin Data → Current State → World Time → Region/Location → Faction/Organization → Active Threads/Events → Character Context → Runtime Roll → Generated Result`

Input mekanis yang diperlukan tetapi tidak tersedia tanpa fallback resmi menggunakan `UNRESOLVED`; jangan membuat angka pengganti.

# 1. NPC GENERATION

## 1.1 Tujuan
NPC dinamis dapat berupa pedagang, petani, pekerja, pengawal, murid, pemburu, tabib, pengelana, aparat lokal, praktisi lepas, saksi, rival, pemberi informasi, dan peran lokal lain yang masuk akal.

NPC dinamis tidak boleh dipakai untuk diam-diam menciptakan grandmaster, tokoh Canon besar, pemimpin faction, teknik rahasia, bloodline langka, atau lore unik tingkat tinggi.

## 1.2 Social Activity
| Tipe lokasi | Base |
|---|---:|
| Ibukota/pusat pemerintahan | 70 |
| Kota/pusat perdagangan | 55 |
| Desa/permukiman kecil | 40 |
| Jalur dagang/karavan | 45 |
| Area perbatasan/pos perjalanan | 35 |
| Wilderness | 10 |
| Zona berbahaya/terisolasi | 5 |
| Tidak diketahui | UNRESOLVED |

Modifier relevan bernilai -10 sampai +10 dan hanya digunakan bila kondisi benar-benar didukung. `Social Activity = clamp(Base + Σ Modifier, 0, 100)`.

## 1.3 NPC Encounter Roll
`NPC Encounter Roll = d100`; social encounter terjadi jika `Roll ≤ Social Activity`.

## 1.4 NPC Composition
Jika encounter terjadi, tentukan jumlah, role, identitas/nama bila layak, faction/organization bila ada dasar, lokasi/aktivitas, temperament, agenda, knowledge, sikap awal, Realm/Stage bila memiliki dasar, dan persistence.

Identity/Realm yang belum ditetapkan menggunakan status data `UNRESOLVED`.

## 1.5 NPC Identity & Persistence
NPC recurring/material diberi `NPC_ID` stabil, misalnya `NPC-0001`, dengan state `characters/npcs/<NPC_ID>.md`, history `npc_history/<NPC_ID>_HISTORY.md` bila perlu, dan registry `characters/npc_registry.md`. NPC_ID tidak berubah dan tidak digunakan ulang setelah permanent death.

## 1.6 NPC Knowledge Boundary
`NPC Knowledge = pengalaman + akses informasi + peran + kejadian yang benar-benar dialami`.
NPC tidak omniscient; rumor dapat salah; NPC dapat berbohong/menyembunyikan informasi; knowledge Character dan NPC dipisahkan.

# 2. EVENT GENERATION

## 2.1 Dua Kelas Event
**Dynamic Local Event:** insiden lokal seperti kecelakaan perjalanan, perselisihan pasar, kehilangan barang, gangguan pekerjaan, konflik kecil, bantuan, perubahan aktivitas, jejak creature/kriminal, masalah logistik, atau kejadian sosial biasa.

**Canon/Admin World Event:** mengikuti registry dan trigger resmi. Dynamic generation tidak boleh mengganti trigger, scope, atau dampak Canon. Scheduled Event mengikuti registry resmi.

## 2.2 Local Event Pressure
Social-only/local:
`Local Event Pressure = clamp(Social Activity + Σ Event Modifier, 0, 95)`.

Creature/physical disturbance:
`Local Event Pressure = clamp((Encounter Pressure + Social Activity) / 2 + Σ Event Modifier, 0, 95)`.

Event Modifier per faktor yang didukung bernilai -10 sampai +10. Jika input formula wajib tidak tersedia, gunakan formula yang memang tidak membutuhkan input tersebut bila tersedia; jika tidak, status hasil `RESOLUTION-BLOCKED`.

`Roll = d100`; local event muncul jika `Roll ≤ Local Event Pressure`.

## 2.3 Event Scope
- Personal: Character/kelompok kecil.
- Local: lokasi/permukiman/route terbatas.
- Regional: beberapa lokasi dan membutuhkan dasar World Event/Canon.
- Global: hanya melalui Canon/Admin event.

Generated local event tidak boleh dinaikkan menjadi Regional/Global tanpa trigger sah.

## 2.4 Event State
Event lintas-turn/material wajib memiliki `EVENT_ID`, scope, waktu mulai, lokasi/scope, trigger, before state, perubahan, entity terdampak, checkpoint, kondisi selesai, dan source/origin.

Dynamic local event dapat menggunakan `EVT-0001`. World/Scheduled Event mempertahankan ID Canon. Generated event tidak menjadi Global Canon hanya karena memiliki ID.

# 3. QUEST GENERATION

## 3.1 Prinsip
Quest adalah tujuan/pekerjaan yang dapat dilakukan Character, bukan hadiah gratis atau jalur cerita wajib. Sumber dapat berupa NPC need, agenda faction/organization, local event, active thread, kontrak sah, kebutuhan lokasi/komunitas, konsekuensi aksi Character, atau event yang benar-benar dapat diakses.

## 3.2 Quest Generation Gate
Quest hanya valid jika tersedia: source need, objective, target/location, method, risk/cost, success/failure condition, reward provenance, deadline bila ada dasar, issuer bila ada, dan ID/persistence bila lintas-turn.

Jika komponen wajib tidak dapat ditentukan secara sah, jangan memaksakan quest. Gunakan `RESOLUTION-BLOCKED` bila input wajib menghalangi validasi atau `UNRESOLVED` bila field belum dapat ditentukan tetapi tidak menghalangi candidate generation.

## 3.3 Quest Types
Delivery/Transport, Escort, Gathering, Hunting, Investigation, Rescue, Protection, Negotiation, Retrieval, Repair/Work, Exploration, Faction/Contract, Personal request.

Tipe tidak menentukan reward/difficulty otomatis.

## 3.4 Quest Difficulty
Quest area/encounter dapat menggunakan Threat Score Module 25. Quest sosial/pekerjaan menggunakan risiko nyata: waktu, perjalanan, akses, sosial, material, dan konsekuensi. Jangan membuat angka baru hanya demi formula. Character Realm tidak otomatis menskalakan quest.

## 3.5 Quest Resolution
Lifecycle:
`Offered → Accepted → Active → Completed`
atau `Offered → Declined`, `Accepted/Active → Failed`, `Accepted/Active → Abandoned`, `Active → Expired` bila deadline resmi terpenuhi.

Quest gagal tidak memberi reward otomatis. Quest sukses tidak berarti tujuan sekunder otomatis berhasil.

## 3.6 Quest ID & Persistence
Quest lintas-turn menggunakan `QST-0001`, state `story/quests/<QUEST_ID>.md`, dan dicerminkan ke `story/ACTIVE_THREADS.md` bila memenuhi scope continuity. ID stabil dan tidak digunakan ulang.

## 3.7 Reward
Prioritas:
`Fixed Canon/Event/Mission Reward → Valid Item/Economy/Contract Source → Dynamic Loot Formula → RESOLUTION-BLOCKED`.

Tidak boleh menciptakan item unik tanpa source, teknik tanpa Technique Origin, uang tanpa dasar, breakthrough gratis, atau reward lebih tinggi hanya karena Character kuat. Item reward wajib mengikuti Item System.

# 4. RELATIONSHIP NPC → EVENT → QUEST
`World Context → NPC/Social Activity → NPC Generation → NPC Agenda/Problem → Local Event (opsional) → Quest Candidate → Quest Validation → Quest Offer → Character Decision → Resolution → Consequence → State/Origin → Save`.

Tidak semua tahap wajib terjadi.

# 5. ANTI-CHEAT / ANTI-RAILROADING
- Player meminta quest ≠ quest otomatis tersedia.
- Player tidak dapat memaksa NPC menerima permintaan.
- Quest tidak menjadi sukses hanya karena Player menyatakan berhasil.
- NPC boleh menolak, berbohong, gagal, kabur, atau memiliki agenda sendiri.
- Event boleh tidak terjadi dan quest boleh gagal.
- Generated content tidak boleh mengalahkan Canon/Admin.
- Character Realm tidak otomatis menaikkan kualitas NPC/Event/Quest, difficulty, atau reward.
- Tidak ada hidden time-skip.

# 6. PERSISTENCE & ORIGIN
Perubahan material harus dapat ditelusuri:
`World Time / Entity ID / Action/Event / Cause / Resolution / Before / After / Source`.

NPC material → NPC State/History. Quest material → Quest State + Character History/Active Threads sesuai scope. Event material → Event state/log + World State/Timeline/Active Threads sesuai scope.

Generated content yang tidak material tidak perlu dipersistenkan.

# 7. VALIDATION GATE
1. Canon/Admin consistency.
2. Location/region validity.
3. World Time validity.
4. NPC role/knowledge boundary.
5. NPC_ID uniqueness/stability.
6. Event class/scope/trigger.
7. Event ID uniqueness/stability.
8. Quest source/objective/target/method/risk/resolution.
9. Quest ID uniqueness/stability.
10. Reward provenance.
11. Time/checkpoint limits.
12. Origin Log requirements.
13. Character/private/shared memory isolation.
14. Save Pipeline dan write-back verification.

Validation gagal → jangan terapkan perubahan material.

# 8. RUNTIME
`FRESH INDEX → LOAD RELEVANT CANON → LOAD STATE/TIME → SOCIAL/ENCOUNTER CONTEXT → NPC GENERATION → EVENT CHECK → QUEST CANDIDATE → VALIDATION → PLAYER CHOICE → ACTION RESOLUTION → CONSEQUENCE → ORIGIN/HISTORY → SAVE → WRITE-BACK VERIFY`.

Module 25 menjadi fondasi dynamic encounter/creature/loot; Module 26 mengatur NPC/event/quest.


## DATA COMPLETENESS HARD GATE
Qwen boleh menentukan hasil konkret hanya setelah source/input runtime yang diwajibkan tersedia. Jangan membuat issuer, identitas, agenda, target, deadline, reward, scope, atau atribut lain hanya untuk membuat candidate lengkap. Field yang belum dapat dibuktikan tetap UNRESOLVED; required field yang menghalangi resolusi menjadi RESOLUTION-BLOCKED.
