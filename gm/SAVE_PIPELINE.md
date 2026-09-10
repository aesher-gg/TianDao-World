# Runtime Save Pipeline

## Tujuan
Menjamin current state dan persistent story memory selalu merupakan hasil dari transisi yang sah, dapat diaudit, dan dapat digunakan untuk melanjutkan cerita tanpa bergantung pada memory chat AI.

## Save Sequence
1. Ambil current state terakhir yang terverifikasi.
2. Muat Character History milik Character aktif bila tersedia.
3. Muat shared World State/Active Threads/Timeline bila relevan.
4. Terapkan hasil aksi/event yang sudah lolos resolusi.
5. Hitung before → after untuk semua field material.
6. Tambahkan Origin Log dengan waktu, penyebab, resolusi, dan sumber.
7. Jalankan State Validator.
8. Jika FAIL, jangan overwrite state terverifikasi dan jangan menulis memory sebagai fakta baru.
9. Jika PASS, hasil menjadi current state berikutnya.
10. Ekstrak hanya fakta cerita material yang benar-benar terkonfirmasi.
11. Append/update Character History untuk fakta privat Character.
12. Update Active Threads, World State, atau Timeline hanya bila dampaknya memenuhi scope masing-masing.
13. Commit/write-back ke repository melalui integrasi resmi yang tersedia.
14. Verifikasi hasil write-back sebelum menyatakan save tersinkron.

## Material Fields
HP, Qi, Stamina, Satiety, realm/stage, cultivation progress, status/condition, item, equipment, durability, currency, technique, Karma, Reputation, faction rank, contract, lokasi, dan waktu.

## Story Memory Criteria
Simpan memory hanya jika peristiwa memiliki nilai kontinuitas, misalnya:
- hubungan NPC/faction yang berubah signifikan;
- teknik/item/teacher/sect yang diperoleh atau hilang;
- quest, kontrak, janji, hutang, konflik, atau kewajiban;
- cedera/trauma atau konsekuensi permanen;
- event dunia besar;
- informasi penting yang karakter benar-benar ketahui;
- keputusan atau kejadian yang akan memengaruhi masa depan.

Aksi rutin tanpa konsekuensi jangka panjang tidak perlu masuk Story History.

## Character Isolation
- Character History selalu dipilih berdasarkan Character ID aktif.
- Jangan membaca atau menulis history Character lain kecuali ada alasan resmi dari event/interaksi.
- Shared memory tidak boleh digunakan untuk menyimpulkan detail privat yang tidak tercatat.

## Recovery
Jika data hilang atau konflik, gunakan snapshot/Origin Log/History terakhir yang dapat dibuktikan. Jangan mengisi celah dengan tebakan atau nilai yang diminta player.

## Anti-Retcon
Tidak boleh menghapus konsekuensi masa lalu, memundurkan waktu, atau menambahkan aset/memory tanpa sumber. Update Canon/Admin baru harus dicatat sebagai perubahan dunia baru, bukan perubahan histori sesi secara diam-diam.

## Write-Back Failure
Jika AI GM tidak memiliki akses tulis repository atau commit gagal:
- jangan mengklaim save berhasil;
- pertahankan hasil sebagai uncommitted/pending state bila sistem mendukung;
- tandai bahwa sinkronisasi repository belum selesai;
- lanjutkan hanya sesuai kemampuan sistem tanpa menghilangkan fakta bahwa save belum tersimpan.
