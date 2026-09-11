# GM Checklist

Checklist validasi wajib sebelum dan sesudah resolusi aksi.

## A. Boot
- [ ] INDEX dimuat dan Load Order diikuti.
- [ ] Core Rules dimuat.
- [ ] `39_CUSTOM_EVENTS.md` dimuat pada awal sesi.
- [ ] Custom/Admin yang berlaku dimuat.
- [ ] Modul realm/system/faction/lore relevan dimuat.
- [ ] Jika gardening relevan, `systems/23_GARDENING.md` dimuat.
- [ ] Current character state dimuat berdasarkan Character ID.
- [ ] Character History aktif dimuat berdasarkan Character ID.
- [ ] Shared story memory relevan dimuat.

## B. Pre-Action
- [ ] Intent utama teridentifikasi.
- [ ] Waktu/lokasi/target valid.
- [ ] Realm, teknik, equipment, inventory, dan resource valid.
- [ ] Informasi yang digunakan diketahui karakter.
- [ ] Durasi sesuai Time System.
- [ ] Tidak ada konflik Canon/Admin.
- [ ] Active Threads yang relevan diperhitungkan.
- [ ] Jika gardening: Garden/Crop ID, lokasi, benih, jumlah, waktu tanam, dan kondisi awal tersedia atau `???`.
- [ ] Jika gardening: status 0–100 konsisten dan tidak dibuat tanpa dasar.

## C. Resolution
- [ ] Cost ditentukan dari modul resmi.
- [ ] Sistem resolusi yang tepat digunakan.
- [ ] Hasil tidak dipaksakan oleh player intent.
- [ ] NPC/monster/lingkungan/faction/event diproses bila relevan.
- [ ] Konsekuensi logis diterapkan.
- [ ] Jika gardening: pertumbuhan mengikuti waktu yang benar-benar berlalu.
- [ ] Jika gardening: tanaman biasa ≤10 hari dan tanaman spiritual ≤60 hari standar.
- [ ] Jika gardening: panen hanya terjadi setelah waktu/Maturity sesuai.

## D. Post-Action
- [ ] Waktu berubah tepat.
- [ ] HP/Qi/Stamina/Satiety/status diperbarui.
- [ ] Inventory/equipment/currency/technique/reputation/Karma diperbarui bila sah.
- [ ] Jika gardening: status kebun/tanaman, jumlah, pertumbuhan, kesehatan, air, nutrisi, penyakit, hama, kualitas, dan maturity konsisten.
- [ ] Jika gardening: Disease/Pest semakin tinggi berarti semakin buruk.
- [ ] Jika gardening: perubahan angka dapat ditelusuri ke waktu/aksi/kondisi.
- [ ] Event state diperbarui hanya jika trigger terpenuhi.
- [ ] Origin Log dibuat untuk perubahan material.
- [ ] State Validator PASS.
- [ ] Fakta cerita material diekstrak tanpa menambah spekulasi.
- [ ] Character History diperbarui hanya untuk Character aktif.
- [ ] Active Threads/World State/Timeline diperbarui hanya bila scope relevan.
- [ ] Write-back/commit diverifikasi jika integrasi repository tersedia.
- [ ] Jika write-back gagal, GM tidak mengklaim save tersinkron.

## E. Response
- [ ] Format `RESPONSE_FORMAT.md` dipatuhi.
- [ ] Tidak ada fakta unsupported.
- [ ] `???` dipertahankan untuk unknown.
- [ ] Current state siap menjadi input turn berikutnya.
- [ ] Save status mencerminkan status sinkronisasi sebenarnya.
