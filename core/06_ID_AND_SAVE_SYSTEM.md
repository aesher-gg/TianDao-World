# 06 — PLAYER, CHARACTER ID & SAVE SYSTEM

## Tujuan
Memisahkan identitas Player, identitas Character, Current Character State, Beast State, NPC State, Quest State, Persistent Story Memory, dan Beast/NPC History agar banyak pemain dapat bermain tanpa bentrok data serta dapat melanjutkan cerita tanpa bergantung pada memory chat AI.

## 1. Player

Player adalah pengguna/manusia yang memainkan game.

- Setiap Player memiliki **Player ID** unik.
- Player ID bukan identitas karakter.
- Satu Player dapat memiliki satu atau lebih Character jika Admin mengizinkan.
- Data akun/pribadi Player tidak menjadi bagian dari gameplay state kecuali diperlukan oleh sistem komunitas.

## 2. Character

Character adalah tokoh yang dimainkan Player.

- Setiap Character memiliki **Character ID** unik dan permanen.
- Character wajib terhubung ke satu Player ID.
- Nama Character tidak boleh menjadi primary identifier karena nama dapat sama.
- Status gameplay, lokasi, resource, inventory, teknik, hubungan, dan perkembangan berada pada Character State.

## 3. Spirit Beast Identity

Spirit Beast adalah entitas gameplay tersendiri dan bukan Item, Equipment, atau Inventory.

- Setiap Spirit Beast memiliki **BEAST_ID** unik, stabil, dan permanen.
- Format standar: `BEAST-0001`.
- Nama Beast bukan primary identifier.
- BEAST_ID tidak berubah karena rename, transfer ownership, release, contract, bonding, atau evolution.
- BEAST_ID tidak boleh dipakai ulang setelah Beast mati permanen atau diarsipkan.
- Relationship Character → Beast tidak menggantikan identitas BEAST_ID.

## 4. NPC Identity

NPC adalah entitas dunia yang dapat bersifat Canon/fixed atau generated.

- NPC Canon dapat berasal dari `lore/NPC_DATABASE.md`.
- NPC generated yang membutuhkan continuity material mendapat **NPC_ID** unik, stabil, dan permanen.
- Format standar: `NPC-0001`.
- Nama NPC bukan primary identifier.
- NPC_ID tidak berubah karena rename, perpindahan lokasi, perubahan faction, hubungan, atau status.
- NPC yang mati permanen mempertahankan NPC_ID untuk histori dan ID tidak boleh dipakai ulang.
- NPC sementara yang tidak mengalami perubahan material tidak wajib dipersistenkan.

Current NPC State:
`characters/npcs/<NPC_ID>.md`

NPC History bila continuity material memerlukannya:
`npc_history/<NPC_ID>_HISTORY.md`

Registry:
`characters/npc_registry.md`

Generated NPC tidak otomatis menjadi Global Canon hanya karena memiliki NPC_ID.

## 5. Quest Identity

Quest adalah gameplay objective/pekerjaan yang dapat muncul secara fixed atau dynamic.

- Quest lintas turn yang membutuhkan persistence memiliki **QUEST_ID** unik, stabil, dan permanen.
- Format standar: `QST-0001`.
- Quest ID tidak boleh dipakai ulang.
- Quest ID tidak bergantung pada nama quest, quest giver, atau reward.
- Quest State adalah sumber operasional quest lintas turn.

Current Quest State:
`story/quests/<QUEST_ID>.md`

Quest aktif yang relevan dicerminkan pada `story/ACTIVE_THREADS.md` sesuai scope.

Generated quest tidak otomatis menjadi Global Canon.

## 6. Event Identity

Event dapat berupa fixed Canon/Admin event, scheduled event, atau dynamic local event.

- World Event mempertahankan ID Canon `WE-###`.
- Scheduled Event mempertahankan ID Canon `SE-###`.
- Dynamic persistent local event menggunakan `EVENT_ID` stabil, format standar `EVT-0001`.
- EVENT_ID tidak boleh dipakai ulang.
- Dynamic local event tidak menjadi Global Canon hanya karena memiliki EVENT_ID.

## 7. Registry

- `characters/players.md` = **Player Registry / starting-data registry**.
- `characters/character_registry.md` = **Character Registry** dan pemetaan Character ID → Player ID → Current State.
- `characters/beast_registry.md` = **Spirit Beast Registry** dan pemetaan BEAST_ID → Current Beast State → Beast History serta owner/lifecycle.
- `characters/npc_registry.md` = **NPC Registry** untuk NPC yang membutuhkan persistence.
- Registry bukan save gameplay dan bukan katalog tertutup untuk generated entities.

## 8. Current Character State

Setiap Character memiliki file state terisolasi:

`characters/players/<CHARACTER_ID>.md`

File tersebut adalah sumber Current Character State operasional untuk Character tersebut.

GM hanya boleh memuat state Character yang sedang dimainkan, kecuali ada alasan resmi untuk interaksi antar-character/world state.

## 9. Current Beast State

Setiap Spirit Beast memiliki file state terisolasi:

`characters/beasts/<BEAST_ID>.md`

Current Beast State adalah sumber operasional untuk identitas, relationship, taming, ownership, contract, tier/realm, vitality, kondisi, lokasi, abilities/techniques, dan status lifecycle Beast tersebut sesuai `systems/24_SPIRIT_BEASTS.md`.

GM tidak boleh membuat Beast State dari nama Beast saja. BEAST_ID dan sumber Beast harus dapat diverifikasi.

## 10. Persistent Story Memory

Setiap Character aktif dapat memiliki history privat:

`character_history/CHAR-<CHARACTER_ID>_HISTORY.md`

Setiap Spirit Beast dapat memiliki history tersendiri:

`beast_history/<BEAST_ID>_HISTORY.md`

NPC persisten dapat memiliki history:

`npc_history/<NPC_ID>_HISTORY.md`

Character History menyimpan pengalaman dan konsekuensi Character. Beast History menyimpan kejadian dan transisi yang terjadi pada Beast. NPC History menyimpan perubahan dan kejadian material yang benar-benar terjadi pada NPC. Keduanya tidak boleh saling menggantikan atau menjadi salinan penuh satu sama lain.

Memory persisten bukan pengganti Current State. Fungsinya menyimpan fakta cerita jangka panjang yang penting untuk kontinuitas, seperti peristiwa besar, hubungan, kewajiban, konflik, dan konsekuensi permanen.

Shared memory berada di:
- `story/WORLD_STATE.md`
- `story/ACTIVE_THREADS.md`
- `story/STORY_TIMELINE.md`

Aturan isolasi:
- Character History hanya boleh memuat memori Character tersebut.
- Beast History hanya boleh memuat fakta Beast tersebut.
- NPC History hanya boleh memuat fakta NPC tersebut.
- Shared World State hanya memuat fakta yang benar-benar bersifat shared/world-level.
- Jangan membocorkan private Character History, Beast History, atau NPC History ke entitas lain tanpa dasar resmi.
- Memory tidak boleh menciptakan fakta baru atau mengalahkan Canon/Admin.

## 11. ID Rules

Format standar:

- `PLAYER-0001`
- `CHAR-0001`
- `BEAST-0001`
- `NPC-0001`
- `QST-0001`
- `EVT-0001`

Semua ID gameplay yang persisten harus unik, stabil, dan tidak berubah sepanjang umur data.

Jika Character, Beast, NPC, Quest, atau Event telah selesai/deceased/archived sesuai lifecycle, ID tidak boleh dipakai ulang.

## 12. Save Rules

Current State adalah snapshot terbaru yang sah.

Setiap perubahan material wajib dapat ditelusuri melalui Origin Log sesuai `core/05_SAVE_INTEGRITY.md` dan modul sistem terkait.

Minimal perubahan material mencatat:
- waktu dunia,
- penyebab/aksi/event,
- nilai sebelum → sesudah,
- sumber/modul yang relevan.

Untuk perubahan Beast, Origin Log wajib mengidentifikasi BEAST_ID. Untuk NPC/Quest/Event, Origin Log wajib mengidentifikasi entity ID yang relevan. Jika aksi mengubah beberapa entity sekaligus, semua state yang berubah harus memiliki before → after yang dapat ditelusuri.

Save baru tidak boleh menghapus histori Origin Log.

## 13. Multi-Entity Isolation

State Character A tidak boleh mengubah atau menggantikan state Character B, Beast C, NPC D, Quest E, atau Event F hanya karena data berada dalam repository yang sama.

Tidak boleh:
- memakai nama sebagai satu-satunya ID;
- menyimpan semua current state dalam satu file bersama;
- mengambil HP/inventory/lokasi Character atau Beast lain sebagai state aktif tanpa dasar interaksi resmi;
- menimpa save Character/Beast/NPC/Quest lain;
- menggunakan `players.md` sebagai current state setelah boot;
- mengubah owner Beast tanpa transfer/release mechanism dan Origin Log yang sah.

## 14. Shared World vs Private State

World Bible, sistem, event, lokasi, NPC, ekonomi, dan data dunia yang bersifat shared tetap menjadi sumber bersama.

Current Character State, Character History, Current Beast State, Beast History, Current NPC State, NPC History, dan private Quest State bersifat terisolasi sesuai ownership/scope.

Jika Character dan Beast/NPC/Quest berinteraksi, perubahan pada masing-masing state harus dicatat pada entity yang relevan. Relationship tidak otomatis berarti ownership, taming, contract, loyalty, atau quest completion.

## 15. New Character

Saat Character baru dibuat:
1. Admin menetapkan Player ID.
2. Admin menetapkan Character ID unik.
3. Starting data dicatat di Player Registry.
4. Character Registry dibuat.
5. Current Character State dibuat sebagai file terpisah.
6. Character History dibuat bila diperlukan.
7. Setelah boot, gameplay menggunakan Current Character State, bukan starting-data registry.

## 16. Spirit Beast Lifecycle

Saat Spirit Beast pertama kali menjadi entitas resmi:
1. Admin/system menetapkan BEAST_ID unik.
2. Beast Registry mencatat BEAST_ID dan lifecycle mapping.
3. Current Beast State dibuat bila Beast sudah memiliki state yang dapat disimpan.
4. Beast History dibuat bila diperlukan untuk kontinuitas.
5. Taming, ownership, relationship, contract, growth, evolution, missing, dan death mengikuti `systems/24_SPIRIT_BEASTS.md`.

Tidak boleh membuat Beast hanya karena Player menyatakan memilikinya.

## 17. NPC / Quest / Event Lifecycle

### NPC
Generated NPC menjadi persistent bila continuity material membutuhkan identity/state. Admin/GM harus membuat NPC_ID dan current state sebelum menyimpan perubahan material.

### Quest
Quest lintas turn harus memiliki QST_ID dan Current Quest State. Status, objective, progress, failure, completion, reward, dan expiry harus dapat ditelusuri.

### Event
Dynamic local event yang berlangsung lintas turn atau mengubah world/entity state harus memiliki EVT_ID dan event state/log. World Event/Scheduled Event memakai ID Canon yang sudah ada.

Generated content tetap berbeda dari Canon/Admin content.

## 18. Automatic Memory Update

Setelah aksi/event berhasil dan State Validator PASS, AI GM harus:
1. memperbarui Current Character State bila berubah;
2. memperbarui Current Beast State bila berubah;
3. memperbarui Current NPC State bila NPC persisten berubah;
4. memperbarui Current Quest State bila quest persisten berubah;
5. menambahkan Origin Log untuk perubahan material;
6. menambahkan fakta terkonfirmasi ke Character History, Beast History, NPC History, dan/atau quest memory sesuai entity/scope;
7. memperbarui Active Threads/World State/Timeline bila dampaknya memang shared;
8. menjaga semua ID dan entity isolation;
9. tidak menulis memory untuk aksi rutin yang tidak memiliki nilai kontinuitas.

Jika repository write-back tidak tersedia, GM wajib menyatakan bahwa save/memory belum tersinkron dan tidak boleh mengklaim commit telah terjadi.

## 19. Memory Integrity
- Jangan menyimpan seluruh percakapan mentah.
- Simpan fakta ringkas, bukan narasi yang tidak diperlukan.
- Jangan mengubah memory lama untuk membuat kejadian baru tampak pernah terjadi.
- Koreksi Admin harus dapat dibedakan dari event gameplay.
- Jika fakta tidak dapat dibuktikan, gunakan `???` atau jangan simpan.
