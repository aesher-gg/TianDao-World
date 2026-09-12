# Runtime Save Pipeline

## Tujuan
Menjamin current state dan persistent story memory selalu merupakan hasil dari transisi yang sah, dapat diaudit, dan dapat digunakan untuk melanjutkan cerita tanpa bergantung pada memory chat AI.

## Save Sequence
1. Ambil current state terakhir yang terverifikasi.
2. Muat Character History milik Character aktif bila tersedia.
3. Jika Spirit Beast terlibat, muat Current Beast State berdasarkan BEAST_ID dan Beast History yang sesuai.
4. Muat shared World State/Active Threads/Timeline bila relevan.
5. Terapkan hasil aksi/event yang sudah lolos resolusi pada entity yang relevan.
6. Hitung before → after untuk semua field material Character dan Beast yang berubah.
7. Tambahkan Origin Log dengan waktu, entity ID, penyebab, resolusi, dan sumber.
8. Jalankan State Validator.
9. Jika FAIL, jangan overwrite state terverifikasi dan jangan menulis memory sebagai fakta baru.
10. Jika PASS, hasil menjadi current state berikutnya untuk Character dan/atau Beast.
11. Ekstrak hanya fakta cerita material yang benar-benar terkonfirmasi.
12. Append/update Character History untuk fakta privat Character.
13. Append/update Beast History untuk fakta privat Beast.
14. Update Active Threads, World State, atau Timeline hanya bila dampaknya memenuhi scope masing-masing.
15. Commit/write-back ke repository melalui integrasi resmi yang tersedia.
16. Verifikasi hasil write-back sebelum menyatakan save tersinkron.

## Material Fields
Character: HP, Qi, Stamina, Satiety, realm/stage, cultivation progress, status/condition, item, equipment, durability, currency, technique, Karma, Reputation, faction rank, contract, lokasi, dan waktu.

Spirit Beast: relationship, trust, bond, loyalty, taming status, ownership status/owner, contract status/type, tier, realm/stage bila berlaku, growth/evolution, HP, Qi, Stamina, Satiety, condition, abilities, techniques, lokasi, habitat, lifecycle status, dan waktu.

## Story Memory Criteria
Simpan memory hanya jika peristiwa memiliki nilai kontinuitas, misalnya:
- hubungan NPC/faction/Beast yang berubah signifikan;
- teknik/item/teacher/sect/Beast yang diperoleh atau hilang;
- quest, kontrak, janji, hutang, konflik, atau kewajiban;
- cedera/trauma atau konsekuensi permanen;
- event dunia besar;
- informasi penting yang karakter benar-benar ketahui;
- keputusan atau kejadian yang akan memengaruhi masa depan;
- transisi Beast berupa taming, ownership, contract, growth/evolution, missing, atau death.

Aksi rutin tanpa konsekuensi jangka panjang tidak perlu masuk Story History.

## Character/Beast Isolation
- Character History selalu dipilih berdasarkan Character ID aktif.
- Beast History selalu dipilih berdasarkan BEAST_ID.
- Jangan membaca atau menulis history entity lain kecuali ada alasan resmi dari event/interaksi.
- Shared memory tidak boleh digunakan untuk menyimpulkan detail privat yang tidak tercatat.
- Ownership transfer mengubah owner mapping, bukan BEAST_ID.

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
