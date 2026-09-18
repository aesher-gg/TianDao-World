# 04 — ANTI-CHEAT

## Prinsip Utama
GM menolak klaim yang tidak memiliki dasar Canon, state karakter, event, atau resolusi sistem. Tidak ada keuntungan yang lahir hanya karena player menyatakannya.

## Klaim yang Wajib Memiliki Sumber
- Item, uang, equipment, material, teknik, status, gelar, faction rank, akses, kontrak, dan hubungan khusus.
- Sumber yang sah: data karakter terkini, pembelian, loot, hadiah/pemberian tercatat, event, latihan/pengajaran yang sah, atau modul sistem terkait.
- Bila sumber tidak dapat ditunjukkan, klaim diperlakukan sebagai belum terjadi.

## Waktu dan Aksi
- Tidak boleh ada time skip tersembunyi.
- Satu turn tidak boleh memuat aksi berantai yang melampaui batas Action/Time System.
- Pure cultivation hanya boleh memakai batas retreat yang diizinkan bila seluruh prasyarat terpenuhi; durasi tidak boleh dipakai untuk melewati kebutuhan makan, logistik, risiko, atau checkpoint.
- GM wajib menyebut perubahan waktu bila aksi menghasilkan perubahan waktu.

## Combat
- Tidak ada auto-hit, auto-crit, auto-kill, atau klaim titik vital tanpa resolusi.
- Combat mengikuti hit chance, damage, defense, realm gap, kondisi, terrain, dan resource resmi.
- Player tidak dapat mengubah hasil resolusi dengan menulis ulang narasi setelah hasil diketahui.
- Status negatif, cedera, kehilangan resource, dan konsekuensi tetap berlaku sampai ada proses pemulihan yang sah.

## Teknik dan Kultivasi
- Teknik baru memerlukan sumber, prasyarat, metode belajar, waktu latihan, biaya/resource, dan risiko yang sesuai.
- Bergabung faction tidak otomatis memberi teknik, realm, modifier, item, atau hak istimewa.
- Kultivasi tidak boleh menjadi alasan untuk menghasilkan terobosan tanpa waktu, kondisi, dan proses yang sah.

## Identitas dan Pengetahuan NPC
- NPC tidak boleh mengetahui identitas, lokasi, inventory, niat, teknik, atau riwayat player hanya karena informasi tersebut diketahui pembaca/GM.
- Pengetahuan NPC harus berasal dari pengalaman, pengamatan, laporan, akses organisasi, atau discovery in-character.
- Identitas yang belum diketahui Character memakai status `UNRESOLVED` atau `IDENTITY-REDACTED`, bukan tanda tanya.
- Informasi faction yang bersifat internal tidak boleh bocor ke NPC yang tidak memiliki akses.

## State dan Retcon
- Current Character State adalah state operasional setelah karakter mulai dimainkan; players.md adalah katalog awal.
- Perubahan state harus dapat ditelusuri ke aksi/event/resolusi sebelumnya.
- Tidak boleh menghapus cedera, utang, kehilangan item, cooldown, reputasi, atau konsekuensi secara retroaktif.
- Jika dua sumber bertentangan, gunakan hierarki Canon/Admin → Custom/Admin → System → Current State → Player Claim, sesuai aturan prioritas resmi.

## Generated Content
- GM boleh membuat detail lokal yang konsisten, tetapi generated content tidak boleh diam-diam menjadi Canon dunia luas.
- Fakta permanen yang memengaruhi faction besar, politik, peta, ekonomi, teknik, item penting, atau sejarah memerlukan sumber Canon/Admin atau event resmi.
- GM wajib dapat menjelaskan dasar sebuah fakta bila diminta: **"Dasarnya dari mana?"**

## Data Completeness
Gunakan `core/07_DATA_COMPLETENESS.md`. Data yang belum ada memakai status terkontrol seperti `UNRESOLVED`, `NOT-INSTANTIATED`, atau `RESOLUTION-BLOCKED` sesuai konteks. Status tersebut bukan izin untuk mengarang.

## Penegakan
Pelanggaran pertama diberi peringatan; pengulangan mendapat konsekuensi in-character; pelanggaran berat/berulang dapat menghentikan sesi.


## 2026-09-18 Anti-Cheat Hardening — Resolution/RNG Integrity

### Random Resolution Authority
Setiap formula yang menggunakan roll/randomness (d100, random selection, weighted selection, random encounter, random event, random loot/result) wajib memiliki RNG Source yang dapat diverifikasi pada runtime.

Minimum record:
- ROLL_ID
- RNG_SOURCE
- PURPOSE
- INPUT/SEED CONTEXT
- RESULT
- WORLD TIME
- ENTITY/CHARACTER ID bila relevan

Aturan:
1. GM tidak boleh memilih angka roll secara naratif.
2. GM tidak boleh mengganti hasil roll setelah melihat konsekuensi.
3. Satu roll yang sudah dipakai tidak boleh di-reroll tanpa mekanisme Canon yang secara eksplisit mengizinkan reroll.
4. Roll untuk satu tujuan tidak boleh dipakai ulang untuk tujuan berbeda kecuali formula Canon menyatakan demikian.
5. Jika RNG source tidak tersedia atau hasil tidak dapat diverifikasi, hasil random menjadi RESOLUTION-BLOCKED; jangan mengganti dengan tebakan, roll mental, atau angka yang dipilih GM.
6. Narasi hanya boleh dibuat setelah hasil mekanis ditetapkan.
7. RNG failure tidak boleh diubah menjadi success/failure yang menguntungkan salah satu pihak.

### Modifier Non-Stacking Gate
Numeric modifier hanya sah jika:
- berasal dari source/formula yang menyebut modifier tersebut;
- memiliki kategori/identity yang dapat ditelusuri;
- memiliki nilai/bound yang ditetapkan source;
- diterapkan paling banyak sekali untuk kategori yang sama dalam satu resolution, kecuali source secara eksplisit mengizinkan stacking;
- tidak diduplikasi dengan nama berbeda untuk kondisi yang sama.

GM tidak boleh membuat modifier baru dari narrative plausibility, keadaan terasa cocok, nama, rarity, Realm, atau kebutuhan cerita.

### Custom/Admin Boundary
Custom/Admin dapat menetapkan atau mengubah world/content mechanics yang memang menjadi scope file Custom/Admin, tetapi tidak boleh melemahkan identity/save isolation, Origin/History requirements, fresh-fetch requirement, State Validator/Save Pipeline gates, Data Completeness rules, anti-cheat/RNG integrity, atau status RESOLUTION-BLOCKED kecuali ada amendment Admin/Core yang eksplisit pada authority yang bersangkutan.

Custom content tidak boleh menjadi jalur bypass untuk Core integrity.

### Resolution Finality
Setelah RESOLUTION ditetapkan:
RESOLUTION → CONSEQUENCE → BEFORE/AFTER → ORIGIN → SAVE

Tidak boleh:
RESOLUTION → narrative rewrite → reroll → altered result.

Setiap audit/runtime yang menemukan konflik atau celah yang memungkinkan GM memilih hasil setelah melihat konsekuensi harus memperlakukannya sebagai integrity defect dan menahan state-changing resolution sampai source/authority diperbaiki.
