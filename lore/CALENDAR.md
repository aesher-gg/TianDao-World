# KALENDER RESMI TIANDAO-WORLD

## Struktur
- 1 tahun = 4 musim.
- 1 tahun = 12 bulan.
- 1 minggu = 7 hari.
- 1 hari = 24 jam untuk pencatatan sistem.
- Format tanggal: `Tahun XXXX | Era | Musim | Tanggal DD | Bulan Nama | Hari`.
- **Tahun dunia saat ini tidak menggunakan Tahun 1 sebagai titik awal boot karakter.** Boot dan runtime mengikuti World Time aktif sesuai hierarki sumber resmi.

## Era Dunia
- Era adalah penanda sejarah besar dunia dan dapat berubah sesuai Canon/Admin.
- **Era Kebangkitan** adalah era aktif yang dapat digunakan ketika ditetapkan oleh Current World Time Repository.
- Tahun dalam Era Kebangkitan harus menggunakan tahun resmi yang tercatat di repository; GM dilarang menciptakan angka tahun sendiri.
- Jika tahun/era aktif tidak tersedia dari sumber resmi, gunakan `???`.

## Musim
1. Semi
2. Panas
3. Gugur
4. Dingin

## Bulan
1. Bulan Bunga — Semi
2. Bulan Hujan — Semi
3. Bulan Angin — Semi
4. Bulan Bara — Panas
5. Bulan Matahari — Panas
6. Bulan Teratai — Panas
7. Bulan Panen — Gugur
8. Bulan Embun — Gugur
9. Bulan Daun Merah — Gugur
10. Bulan Salju — Dingin
11. Bulan Es — Dingin
12. Bulan Malam Panjang — Dingin

## Siklus Hari
Hari ke-1 Senin, ke-2 Selasa, ke-3 Rabu, ke-4 Kamis, ke-5 Jumat, ke-6 Sabtu, ke-7 Minggu. Setelah Minggu kembali ke Senin.

## Epoch Historis
Tahun 1, Musim Semi, Tanggal 1, Bulan Bunga, Hari Senin tetap merupakan **titik awal historis kalender**, tetapi **bukan fallback untuk boot atau runtime karakter**.

## World Time Saat Ini
World Time aktif adalah state dunia bersama dan harus ditetapkan/tervalidasi melalui sumber repository yang sah. Hierarki runtime:

**Current World Time Repository → Character State World Time → ??? jika keduanya tidak tersedia**

Untuk setting dunia modern saat ini, Admin dapat menetapkan tahun di atas 1000 dalam **Era Kebangkitan** melalui Current World Time Repository. Setelah ditetapkan, nilai tersebut menjadi acuan utama seluruh Character dan runtime sampai diperbarui melalui event/perubahan dunia yang sah.

## Peristiwa Kalender
Festival, hari pasar, upacara faction, dan event terjadwal harus memiliki tanggal resmi. GM boleh membuat kegiatan harian lokal, tetapi kegiatan tersebut tidak boleh mengubah kalender global.

## Aturan Waktu
Waktu hanya maju melalui aksi/event valid. Durasi perjalanan, istirahat, kultivasi, combat, dan efek kondisi mengikuti `core/02_TIME_SYSTEM.md`. Tidak ada lompatan waktu tersembunyi.
