# 05 — SAVE INTEGRITY

## Tujuan
Menjaga agar state karakter dan dunia dapat ditelusuri, tidak berubah diam-diam, dan tidak dapat di-retcon untuk memperoleh keuntungan.

## Pemisahan Data
- `characters/players.md`: Player Registry dan pemetaan Player → Character; bukan current state.
- `characters/character_registry.md`: Character Registry dan pemetaan Character ID → Player ID → Current State; bukan current state.
- `characters/players/<CHARACTER_ID>.md`: current character state operasional untuk satu Character.
- `core/06_ID_AND_SAVE_SYSTEM.md`: aturan ID, isolasi, dan lifecycle save.
- World Bible, System, Custom/Admin, dan Event resmi: sumber aturan/fakta dunia sesuai hierarki prioritas.

## Identity Integrity
- Player ID dan Character ID harus unik dan stabil.
- Character ID tidak boleh dipakai ulang setelah Character mati permanen/diarsipkan.
- Nama Character bukan primary identifier.
- State satu Character tidak boleh menimpa state Character lain.

## Origin Log Wajib
Setiap perubahan material pada state harus memiliki asal yang dapat ditelusuri, minimal:
- timestamp/waktu dunia,
- aksi atau event penyebab,
- resolusi sistem bila ada,
- nilai sebelum → sesudah,
- sumber/modul yang relevan.

Perubahan item, equipment, currency, teknik, realm, HP, Qi, Stamina, Satiety, kondisi, Karma, Reputation, faction rank, kontrak, dan lokasi harus dapat ditelusuri ke sumber tersebut.

## Aturan Snapshot
- Current State adalah snapshot operasional terbaru, bukan izin untuk menghapus sejarah.
- Snapshot baru tidak membatalkan Origin Log sebelumnya.
- Bila state terbaru bertentangan dengan perubahan sebelumnya, GM wajib mencari sumber transisi; tidak boleh memilih nilai yang paling menguntungkan player.

## Konflik Data
Prioritas sumber mengikuti aturan Core/GM: Canon/Admin dan Custom/Admin yang berlaku mengungguli interpretasi GM; System mengatur resolusi mekanis; Current State mencerminkan hasil yang telah sah; klaim player tanpa bukti tidak mengubah state.

Untuk konflik antar-character, gunakan Character ID sebagai identitas utama dan jangan pernah menggabungkan state dua Character.

## Anti-Retcon
- Dilarang menambahkan item/teknik/status/uang setelah fakta tanpa asal.
- Dilarang menghapus cedera, utang, cooldown, kehilangan item, reputasi buruk, atau konsekuensi tanpa proses pemulihan yang sah.
- Dilarang mengubah waktu dunia ke belakang untuk membatalkan konsekuensi.
- Perubahan Canon/Admin yang sah adalah update dunia baru, bukan retcon diam-diam terhadap histori sesi.

## Integrity Check
Sebelum menerima state baru, GM harus memeriksa:
1. Player ID dan Character ID valid serta cocok dengan Registry;
2. lokasi dan waktu konsisten;
3. resource tidak melebihi kapasitas;
4. inventory memiliki sumber;
5. teknik dan realm memiliki jalur perkembangan yang sah;
6. kondisi negatif memiliki penyebab dan belum dihapus tanpa penyembuhan;
7. faction rank/reputation memiliki event atau interaksi yang mendasari;
8. perubahan besar memiliki event/Canon yang mendukung.

## Restore / Recovery
Jika save rusak atau data hilang, GM tidak boleh mengisi kekosongan dengan tebakan. Gunakan snapshot/Origin Log terakhir yang dapat dibuktikan. Jika tidak ada bukti yang cukup, state dikembalikan ke nilai terakhir yang terverifikasi, bukan nilai yang diminta player.
