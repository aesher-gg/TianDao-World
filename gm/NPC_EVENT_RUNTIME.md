# NPC, EVENT & QUEST RUNTIME

## 1. Fresh Runtime Gate

Jika NPC, event, atau quest relevan, setelah fresh `INDEX.md` berhasil:

1. Muat `systems/26_DYNAMIC_NPC_EVENT_QUEST.md`.
2. Muat Canon/location/faction/lore yang relevan.
3. Muat current NPC State/History jika NPC persistent terlibat.
4. Muat relevant Event Registry/World State/Active Threads.
5. Muat Current Quest State jika quest lintas turn relevan.
6. Validasi sebelum membuat perubahan material.

## 2. NPC Resolution

- NPC Canon yang sudah terdaftar tetap bersumber dari `lore/NPC_DATABASE.md`.
- NPC yang belum dikenal Character memiliki identity status `UNRESOLVED` sampai identitas diketahui in-character, sesuai aturan Canon.
- Untuk social encounter baru, gunakan Social Activity dan NPC generation pada Module 26.
- Tentukan role, aktivitas, agenda, temperament, pengetahuan, faction/organization bila ada dasar, dan sikap terhadap Character.
- NPC tidak boleh mengetahui fakta di luar pengalaman/aksesnya.
- NPC boleh menolak, berbohong, salah memahami, meminta bayaran, takut, berubah sikap, membantu, gagal, pergi, atau bertindak sendiri bila konsisten.
- Realm/Stage NPC tidak boleh ditebak. Jika tidak memiliki dasar yang sah → `UNRESOLVED`.
- NPC persistent harus memiliki NPC_ID stabil (`NPC-####`) dan state/history sesuai Module 26.

## 3. Event Resolution

### Dynamic Local Event
- Gunakan Local Event Pressure dari Module 26.
- Event dapat muncul atau tidak berdasarkan roll dan konteks nyata.
- Local Event dapat bersifat personal/local; tidak boleh otomatis menjadi regional/global.
- Generated event tidak menjadi Canon global hanya karena memiliki EVENT_ID.

### Canon/Admin World Event
- Muat `events/world_events/00_WORLD_EVENT_REGISTRY.md`.
- Periksa trigger secara eksplisit.
- Jika trigger belum terpenuhi, event tidak aktif.
- Jika aktif, jalankan hanya impact/konsekuensi yang diizinkan.
- Jangan mengganti trigger, scope, atau dampak Canon melalui dynamic generation.

### Scheduled Event
- Muat `events/scheduled_events/00_SCHEDULED_EVENT_REGISTRY.md` bila kalender relevan.
- Event terjadwal tidak otomatis berarti Character hadir, mengetahui, atau memperoleh akses.
- Perjalanan, lokasi, akses, keamanan, dan waktu harus terpenuhi.

## 4. Quest Resolution

- Quest candidate hanya boleh dibuat melalui Generation Gate Module 26.
- Sumber dapat berupa NPC need, faction/organization agenda, local event, active thread, contract, lokasi, atau event yang benar-benar dapat diakses.
- Player meminta quest ≠ quest otomatis tersedia.
- Quest harus memiliki tujuan, target, metode, risiko/biaya, success/failure condition, dan reward provenance yang valid.
- Quest lintas turn menggunakan `QST-####` dan Current Quest State `story/quests/<QUEST_ID>.md`.
- Active quest yang relevan dicerminkan di `story/ACTIVE_THREADS.md`.
- Status harus mengikuti lifecycle Module 26: Offered, Accepted, Active, Completed, Declined, Failed, Abandoned, Expired.
- Quest failure tidak memberi reward otomatis.
- Reward item/uang/teknik mengikuti Item, Economy, Technique, Loot, Contract, dan Event rules; tidak boleh dibuat bebas.

## 5. Canon / Derived / Generated

- **CANON:** fakta resmi; wajib dipatuhi.
- **DERIVED:** konsekuensi logis dari Canon/state; boleh dihitung selama tidak bertentangan.
- **GENERATED:** NPC lokal, local incident, dialogue, quest candidate, atau detail runtime yang dibuat GM; tidak menjadi Canon permanen tanpa dasar.
- Persistence mempertahankan continuity, tetapi tidak otomatis mengubah generated content menjadi Global Canon.

## 6. Evidence Rule

Untuk setiap NPC reaction, event, quest, atau perubahan material, GM harus dapat menjawab: `Dasarnya dari mana?`

Jika tidak ada dasar yang cukup:
- jangan menerapkan perubahan material;
- gunakan `UNRESOLVED` atau status kelengkapan data yang sesuai;
- atau jangan generate content tersebut.

## 7. Save / Origin

Perubahan material harus melewati State Validator dan Save Pipeline.

Minimal:
`World Time / Entity ID / Action/Event / Cause / Resolution / Before / After / Source`

- NPC change → NPC State + NPC History bila relevan.
- Quest change → Quest State + Character History/Active Threads sesuai scope.
- Event change → Event state/log + World State/Timeline/Active Threads sesuai scope.
- Write-back harus diverifikasi.
- Jika write-back gagal, gunakan `PENDING SYNC`; jangan mengklaim sinkron.

## 8. Runtime Pipeline

`FRESH INDEX → RELEVANT CANON → STATE/TIME → SOCIAL/ENCOUNTER CONTEXT → NPC RESOLUTION → EVENT CHECK → QUEST CANDIDATE → PLAYER DECISION → ACTION RESOLUTION → CONSEQUENCE → VALIDATION → ORIGIN/HISTORY → SAVE → WRITE-BACK VERIFY`


## Data Completeness Gate
Sebelum NPC/Event/Quest generation atau perubahan state:
- Klasifikasikan field yang belum tersedia dengan `core/07_DATA_COMPLETENESS.md`.
- NPC identity/realm/knowledge/faction/role tidak boleh ditebak untuk membuat encounter lebih lengkap.
- Dynamic generation hanya boleh mengisi field yang memang dihasilkan oleh Module 26 dengan input dan formula sah; hasilnya `RUNTIME-GENERATED`, bukan Canon.
- Entity/record yang belum dibuat tetap `NOT-INSTANTIATED`; jangan menciptakan persistent NPC/Quest/Event hanya untuk mengisi schema.
- Bila required source/input tidak tersedia, gunakan `UNRESOLVED` atau `RESOLUTION-BLOCKED` sesuai konteks dan tahan perubahan material.
- Dialogue, NPC assertion, Player claim, dan narrative convenience bukan bukti Canon.
