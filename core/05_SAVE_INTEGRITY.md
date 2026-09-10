# 05 — SAVE INTEGRITY

## Tujuan
Menjaga agar state karakter dan dunia dapat ditelusuri, tidak berubah diam-diam, dan tidak dapat di-retcon untuk memperoleh keuntungan.

## Pemisahan Data
- `characters/players.md`: katalog/starting data karakter.
- `characters/players/<character>.md`: current character state operasional setelah karakter dimainkan.
- World Bible, System, Custom/Admin, dan Event resmi: sumber aturan/fakta dunia sesuai hierarki prioritas.

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

## Anti-Retcon
- Dilarang menambahkan item/teknik/status/uang setelah fakta tanpa asal.
- Dilarang menghapus cedera, utang, cooldown, kehilangan item, reputasi buruk, atau konsekuensi tanpa proses pemulihan yang sah.
- Dilarang mengubah waktu dunia ke belakang untuk membatalkan konsekuensi.
- Perubahan Canon/Admin yang sah adalah update dunia baru, bukan retcon diam-diam terhadap histori sesi.

## Integrity Check
Sebelum menerima state baru, GM harus memeriksa:
1. lokasi dan waktu konsisten;
2. resource tidak melebihi kapasitas;
3. inventory memiliki sumber;
4. teknik dan realm memiliki jalur perkembangan yang sah;
5. kondisi negatif memiliki penyebab dan belum dihapus tanpa penyembuhan;
6. faction rank/reputation memiliki event atau interaksi yang mendasari;
7. perubahan besar memiliki event/Canon yang mendukung.

## Restore / Recovery
Jika save rusak atau data hilang, GM tidak boleh mengisi kekosongan dengan tebakan. Gunakan snapshot/Origin Log terakhir yang dapat dibuktikan. Jika tidak ada bukti yang cukup, state dikembalikan ke nilai terakhir yang terverifikasi, bukan nilai yang diminta player.
