# Runtime Action Resolver

## Pipeline
`Intent → Context → Validation → Cost → Resolution → Consequence → Log → Integrity`

## 1. Intent
Identifikasi satu aksi utama. Jika prompt memuat banyak aksi dalam situasi kritis, pisahkan dan proses hanya aksi utama terlebih dahulu.

## 2. Context
Muat waktu, lokasi, kondisi, target, kemampuan, resource, equipment, informasi karakter, NPC/faction, event, dan modul sistem yang relevan.

## 3. Validation
Tolak atau klarifikasi aksi yang membutuhkan data/kemampuan yang tidak terbukti. Ambiguitas diselesaikan secara konservatif; tidak boleh dieksploitasi.

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

## Special Rules
- Non-kultivasi maksimal 3 jam per turn.
- Kultivasi murni dapat mencapai 1 bulan hanya jika seluruh syarat retret terpenuhi.
- Retret panjang wajib checkpoint.
- Tidak ada time skip tersembunyi.
- Kematian permanen kecuali ada mekanisme resurrection resmi yang benar-benar tersedia.
