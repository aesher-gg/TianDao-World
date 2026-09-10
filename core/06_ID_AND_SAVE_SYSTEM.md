# 06 — PLAYER, CHARACTER ID & SAVE SYSTEM

## Tujuan
Memisahkan identitas Player, identitas Character, dan Current Character State agar banyak pemain dapat bermain tanpa bentrok data.

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

## 3. Registry
- `characters/players.md` = **Player Registry / starting-data registry**.
- `characters/character_registry.md` = **Character Registry** dan pemetaan Character ID → Player ID → Current State.
- Registry bukan save gameplay.

## 4. Current Character State
Setiap Character memiliki file state terisolasi:

`characters/players/<CHARACTER_ID>.md`

File tersebut adalah sumber Current Character State operasional untuk Character tersebut.

GM hanya boleh memuat state Character yang sedang dimainkan, kecuali ada alasan resmi untuk interaksi antar-character/world state.

## 5. ID Rules
Format standar:

- `PLAYER-0001`
- `CHAR-0001`

ID harus unik, stabil, dan tidak berubah sepanjang umur data.

Jika Character mati permanen, Character ID tidak boleh dipakai ulang untuk karakter baru.

## 6. Save Rules
Current State adalah snapshot terbaru yang sah.

Setiap perubahan material wajib dapat ditelusuri melalui Origin Log sesuai `core/05_SAVE_INTEGRITY.md`.

Minimal perubahan material mencatat:
- waktu dunia,
- penyebab/aksi/event,
- nilai sebelum → sesudah,
- sumber/modul yang relevan.

Save baru tidak boleh menghapus histori Origin Log.

## 7. Multi-Player Isolation
State Character A tidak boleh mengubah atau menggantikan state Character B hanya karena data berada dalam repository yang sama.

Tidak boleh:
- memakai nama sebagai satu-satunya ID;
- menyimpan semua current state dalam satu file karakter bersama;
- mengambil HP/inventory/lokasi Character lain sebagai state Character aktif;
- menimpa save Character lain;
- menggunakan data `players.md` sebagai current state setelah boot.

## 8. Shared World vs Private Character State
World Bible, sistem, event, lokasi, NPC, ekonomi, dan data dunia yang bersifat shared tetap menjadi sumber bersama.

Current Character State bersifat terisolasi per Character.

Jika dua Character berinteraksi, perubahan pada masing-masing state harus dicatat pada Character yang relevan dan tidak boleh menyebabkan overwrite terhadap state pihak lain.

## 9. New Character
Saat Character baru dibuat:
1. Admin menetapkan Player ID.
2. Admin menetapkan Character ID unik.
3. Starting data dicatat di Player Registry.
4. Character Registry dibuat.
5. Current Character State dibuat sebagai file terpisah.
6. Setelah boot, gameplay menggunakan Current Character State, bukan starting-data registry.
