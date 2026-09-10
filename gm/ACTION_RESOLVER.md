# Runtime Action Resolver

## Pipeline
`Intent → Context → Validation → Cost → Resolution → Consequence → Log → Integrity → Memory → Save/Write-Back`

## 1. Intent
Identifikasi satu aksi utama. Jika prompt memuat banyak aksi dalam situasi kritis, pisahkan dan proses hanya aksi utama terlebih dahulu.

## 2. Context
Muat waktu, lokasi, kondisi, target, kemampuan, resource, equipment, informasi karakter, NPC/faction, event, Active Threads, Character History, shared memory, dan modul sistem yang relevan.

## 3. Validation
Tolak atau klarifikasi aksi yang membutuhkan data/kemampuan yang tidak terbukti. Ambiguitas diselesaikan secara konservatif; tidak boleh dieksploitasi. Pastikan semua memory yang digunakan cocok dengan Character ID aktif.

## 4. Cost
Gunakan biaya yang ditetapkan modul resmi. Jangan membuat angka baru hanya agar aksi dapat berjalan.

## 5. Resolution
Gunakan mekanik resmi yang paling spesifik. Jangan mengganti hasil sistem dengan hasil naratif yang menguntungkan player. Hasil yang valid: sukses, gagal, sebagian berhasil, atau sukses dengan konsekuensi.

## 6. Consequence
Proses konsekuensi logis terhadap karakter, NPC, lingkungan, faction, monster, dan event. NPC tetap otonom.

## 7. Log
Untuk setiap perubahan material: timestamp, aksi/event, resolusi, before → after, dan sumber modul.

## 8. Integrity
Jalankan `STATE_VALIDATOR.md` sebelum state baru dianggap sah.

## 9. Memory
Setelah State Validator PASS, ekstrak hanya fakta material yang benar-benar terjadi. Tulis private facts ke Character History dan shared facts ke World State/Timeline/Active Threads sesuai scope. Jangan menyimpan percakapan mentah atau spekulasi.

## 10. Save / Write-Back
Perbarui Current Character State dan memory melalui `SAVE_PIPELINE.md`. Jika integrasi repository tersedia, commit dan verifikasi. Jika write-back gagal, jangan mengklaim save telah tersinkron.

## Special Rules
- Non-kultivasi maksimal 3 jam per turn.
- Kultivasi murni dapat mencapai 1 bulan hanya jika seluruh syarat retret terpenuhi.
- Retret panjang wajib checkpoint.
- Tidak ada time skip tersembunyi.
- Kematian permanen kecuali ada mekanisme resurrection resmi yang benar-benar tersedia.
