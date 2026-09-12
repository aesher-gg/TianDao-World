# Runtime Action Resolver

## Pipeline
`Intent → Context → Validation → Cost → Resolution → Consequence → Log → Integrity → Memory → Save/Write-Back`

## 1. Intent
Identifikasi satu aksi utama. Jika prompt memuat banyak aksi dalam situasi kritis, pisahkan dan proses hanya aksi utama terlebih dahulu.

## 2. Context
Muat waktu, lokasi, kondisi, target, kemampuan, resource, equipment, informasi karakter, NPC/faction, event, Active Threads, Character History, shared memory, dan modul sistem yang relevan. Jika Spirit Beast terlibat, muat BEAST_ID, Current Beast State, Beast History, relationship/taming/ownership/contract, habitat, behavior, dan lifecycle status yang relevan.

## 3. Validation
Tolak atau klarifikasi aksi yang membutuhkan data/kemampuan yang tidak terbukti. Ambiguitas diselesaikan secara konservatif; tidak boleh dieksploitasi. Pastikan semua memory yang digunakan cocok dengan Character ID/BEAST_ID aktif. Relationship tidak boleh ditafsirkan sebagai taming, ownership, contract, atau loyalty tanpa dasar.

## 4. Cost
Gunakan biaya yang ditetapkan modul resmi. Jangan membuat angka baru hanya agar aksi dapat berjalan. Jika Character memberikan item/resource kepada Beast, pastikan sumber dan pengurangan Character tervalidasi.

## 5. Resolution
Gunakan mekanik resmi yang paling spesifik. Jangan mengganti hasil sistem dengan hasil naratif yang menguntungkan player. Hasil yang valid: sukses, gagal, sebagian berhasil, atau sukses dengan konsekuensi. Pertumbuhan Beast tidak otomatis menjadi evolution, breakthrough, ability, technique, taming, ownership, atau contract.

## 6. Consequence
Proses konsekuensi logis terhadap karakter, Beast, NPC, lingkungan, faction, monster, dan event. NPC/Beast tetap otonom sesuai behavior, intelligence, condition, habitat, dan data resmi.

## 7. Log
Untuk setiap perubahan material: timestamp, entity ID (`CHARACTER_ID` dan/atau `BEAST_ID`), aksi/event, resolusi, before → after, dan sumber modul.

## 8. Integrity
Jalankan `STATE_VALIDATOR.md` sebelum state baru dianggap sah.

## 9. Memory
Setelah State Validator PASS, ekstrak hanya fakta material yang benar-benar terjadi. Tulis private facts ke Character History dan Beast facts ke Beast History sesuai entity; shared facts ke World State/Timeline/Active Threads sesuai scope. Jangan menyimpan percakapan mentah atau spekulasi.

## 10. Save / Write-Back
Perbarui Current Character State, Current Beast State bila relevan, dan memory melalui `SAVE_PIPELINE.md`. Jika integrasi repository tersedia, commit dan verifikasi. Jika write-back gagal, jangan mengklaim save telah tersinkron.

## Special Rules
- Non-kultivasi maksimal 3 jam per turn.
- Kultivasi murni dapat mencapai 1 bulan hanya jika seluruh syarat retret terpenuhi.
- Retret panjang wajib checkpoint.
- Tidak ada time skip tersembunyi.
- Kematian permanen kecuali ada mekanisme resurrection resmi yang benar-benar tersedia.
- BEAST_ID tidak berubah karena rename, ownership transfer, release, contract, bonding, atau evolution.
- Missing Beast tidak sama dengan deceased dan tidak boleh dipindahkan/diaktifkan kembali tanpa dasar resmi.
