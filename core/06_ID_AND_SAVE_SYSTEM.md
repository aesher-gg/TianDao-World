# 06 — PLAYER, CHARACTER ID & SAVE SYSTEM

## Tujuan
Memisahkan identitas Player, identitas Character, Current Character State, Beast State, Persistent Story Memory, dan Beast History agar banyak pemain dapat bermain tanpa bentrok data serta dapat melanjutkan cerita tanpa bergantung pada memory chat AI.

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

## 4. Registry
- `characters/players.md` = **Player Registry / starting-data registry**.
- `characters/character_registry.md` = **Character Registry** dan pemetaan Character ID → Player ID → Current State.
- `characters/beast_registry.md` = **Spirit Beast Registry** dan pemetaan BEAST_ID → Current Beast State → Beast History serta owner/lifecycle.
- Registry bukan save gameplay.

## 5. Current Character State
Setiap Character memiliki file state terisolasi:

`characters/players/<CHARACTER_ID>.md`

File tersebut adalah sumber Current Character State operasional untuk Character tersebut.

GM hanya boleh memuat state Character yang sedang dimainkan, kecuali ada alasan resmi untuk interaksi antar-character/world state.

## 6. Current Beast State
Setiap Spirit Beast memiliki file state terisolasi:

`characters/beasts/<BEAST_ID>.md`

Current Beast State adalah sumber operasional untuk identitas, relationship, taming, ownership, contract, tier/realm, vitality, kondisi, lokasi, abilities/techniques, dan status lifecycle Beast tersebut sesuai `systems/24_SPIRIT_BEASTS.md`.

GM tidak boleh membuat Beast State dari nama Beast saja. BEAST_ID dan sumber Beast harus dapat diverifikasi.

## 7. Persistent Story Memory
Setiap Character aktif dapat memiliki history privat:

`character_history/CHAR-<CHARACTER_ID>_HISTORY.md`

Setiap Spirit Beast dapat memiliki history tersendiri:

`beast_history/<BEAST_ID>_HISTORY.md`

Character History menyimpan pengalaman dan konsekuensi Character. Beast History menyimpan kejadian dan transisi yang terjadi pada Beast. Keduanya tidak boleh saling menggantikan atau menjadi salinan penuh satu sama lain.

Memory persisten bukan pengganti Current State. Fungsinya menyimpan fakta cerita jangka panjang yang penting untuk kontinuitas, seperti peristiwa besar, hubungan, kewajiban, konflik, dan konsekuensi permanen.

Shared memory berada di:
- `story/WORLD_STATE.md`
- `story/ACTIVE_THREADS.md`
- `story/STORY_TIMELINE.md`

Aturan isolasi:
- Character History hanya boleh memuat memori Character tersebut.
- Beast History hanya boleh memuat fakta Beast tersebut.
- Shared World State hanya memuat fakta yang benar-benar bersifat shared/world-level.
- Jangan membocorkan private Character History atau Beast History ke entitas lain tanpa dasar resmi.
- Memory tidak boleh menciptakan fakta baru atau mengalahkan Canon/Admin.

## 8. ID Rules
Format standar:

- `PLAYER-0001`
- `CHAR-0001`
- `BEAST-0001`

ID harus unik, stabil, dan tidak berubah sepanjang umur data.

Jika Character atau Beast mati permanen, ID tidak boleh dipakai ulang.

## 9. Save Rules
Current State adalah snapshot terbaru yang sah.

Setiap perubahan material wajib dapat ditelusuri melalui Origin Log sesuai `core/05_SAVE_INTEGRITY.md` dan modul sistem terkait.

Minimal perubahan material mencatat:
- waktu dunia,
- penyebab/aksi/event,
- nilai sebelum → sesudah,
- sumber/modul yang relevan.

Untuk perubahan Beast, Origin Log wajib mengidentifikasi BEAST_ID. Jika aksi mengubah Character dan Beast sekaligus, kedua state harus memiliki before → after yang dapat ditelusuri.

Save baru tidak boleh menghapus histori Origin Log.

## 10. Multi-Entity Isolation
State Character A tidak boleh mengubah atau menggantikan state Character B atau Beast C hanya karena data berada dalam repository yang sama.

Tidak boleh:
- memakai nama sebagai satu-satunya ID;
- menyimpan semua current state dalam satu file bersama;
- mengambil HP/inventory/lokasi Character atau Beast lain sebagai state aktif tanpa dasar interaksi resmi;
- menimpa save Character/Beast lain;
- menggunakan `players.md` sebagai current state setelah boot;
- mengubah owner Beast tanpa transfer/release mechanism dan Origin Log yang sah.

## 11. Shared World vs Private State
World Bible, sistem, event, lokasi, NPC, ekonomi, dan data dunia yang bersifat shared tetap menjadi sumber bersama.

Current Character State, Character History, Current Beast State, dan Beast History bersifat terisolasi.

Jika Character dan Beast berinteraksi, perubahan pada masing-masing state harus dicatat pada entity yang relevan. Relationship tidak otomatis berarti ownership, taming, contract, atau loyalty.

## 12. New Character
Saat Character baru dibuat:
1. Admin menetapkan Player ID.
2. Admin menetapkan Character ID unik.
3. Starting data dicatat di Player Registry.
4. Character Registry dibuat.
5. Current Character State dibuat sebagai file terpisah.
6. Character History dibuat bila diperlukan.
7. Setelah boot, gameplay menggunakan Current Character State, bukan starting-data registry.

## 13. Spirit Beast Lifecycle
Saat Spirit Beast pertama kali menjadi entitas resmi:
1. Admin/system menetapkan BEAST_ID unik.
2. Beast Registry mencatat BEAST_ID dan lifecycle mapping.
3. Current Beast State dibuat bila Beast sudah memiliki state yang dapat disimpan.
4. Beast History dibuat bila diperlukan untuk kontinuitas.
5. Taming, ownership, relationship, contract, growth, evolution, missing, dan death mengikuti `systems/24_SPIRIT_BEASTS.md`.

Tidak boleh membuat Beast hanya karena Player menyatakan memilikinya.

## 14. Automatic Memory Update
Setelah aksi/event berhasil dan State Validator PASS, AI GM harus:
1. memperbarui Current Character State bila berubah;
2. memperbarui Current Beast State bila berubah;
3. menambahkan Origin Log untuk perubahan material;
4. menambahkan fakta terkonfirmasi ke Character History dan/atau Beast History sesuai entity;
5. memperbarui Active Threads/World State/Timeline bila dampaknya memang shared;
6. menjaga Character ID dan BEAST_ID isolation;
7. tidak menulis memory untuk aksi rutin yang tidak memiliki nilai kontinuitas.

Jika repository write-back tidak tersedia, GM wajib menyatakan bahwa save/memory belum tersinkron dan tidak boleh mengklaim commit telah terjadi.

## 15. Memory Integrity
- Jangan menyimpan seluruh percakapan mentah.
- Simpan fakta ringkas, bukan narasi yang tidak diperlukan.
- Jangan mengubah memory lama untuk membuat kejadian baru tampak pernah terjadi.
- Koreksi Admin harus dapat dibedakan dari event gameplay.
- Jika fakta tidak dapat dibuktikan, gunakan `???` atau jangan simpan.
