# GM Checklist

Checklist validasi wajib sebelum dan sesudah resolusi aksi.

## A. Boot
- [ ] INDEX dimuat dan Load Order diikuti.
- [ ] Core Rules dimuat.
- [ ] `39_CUSTOM_EVENTS.md` dimuat pada awal sesi.
- [ ] Custom/Admin yang berlaku dimuat.
- [ ] Modul realm/system/faction/lore relevan dimuat.
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

## C. Resolution
- [ ] Cost ditentukan dari modul resmi.
- [ ] Sistem resolusi yang tepat digunakan.
- [ ] Hasil tidak dipaksakan oleh player intent.
- [ ] NPC/monster/lingkungan/faction/event diproses bila relevan.
- [ ] Konsekuensi logis diterapkan.

## D. Post-Action
- [ ] Waktu berubah tepat.
- [ ] HP/Qi/Stamina/Satiety/status diperbarui.
- [ ] Inventory/equipment/currency/technique/reputation/Karma diperbarui bila sah.
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
