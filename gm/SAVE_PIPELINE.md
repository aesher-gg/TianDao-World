# Runtime Save Pipeline

## Tujuan
Menjamin current state selalu merupakan snapshot dari transisi yang sah dan dapat diaudit.

## Save Sequence
1. Ambil current state terakhir yang terverifikasi.
2. Terapkan hasil aksi/event yang sudah lolos resolusi.
3. Hitung before → after untuk semua field material.
4. Tambahkan Origin Log dengan waktu, penyebab, resolusi, dan sumber.
5. Jalankan State Validator.
6. Jika PASS, hasil menjadi current state berikutnya.
7. Jika FAIL, jangan overwrite state terverifikasi.

## Material Fields
HP, Qi, Stamina, Satiety, realm/stage, cultivation progress, status/condition, item, equipment, durability, currency, technique, Karma, Reputation, faction rank, contract, lokasi, dan waktu.

## Recovery
Jika data hilang atau konflik, gunakan snapshot/Origin Log terakhir yang dapat dibuktikan. Jangan mengisi celah dengan tebakan atau nilai yang diminta player.

## Anti-Retcon
Tidak boleh menghapus konsekuensi masa lalu, memundurkan waktu, atau menambahkan aset tanpa sumber. Update Canon/Admin baru harus dicatat sebagai perubahan dunia baru, bukan perubahan histori sesi secara diam-diam.
