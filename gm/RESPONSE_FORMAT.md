# GM Response Format

Format standar dan **WAJIB** untuk setiap respons AI Game Master TianDao-World.

## 1. ATURAN UMUM

- Setiap respons gameplay wajib mengikuti struktur di bawah.
- **Balasan pertama/boot wajib menggunakan format Boot.**
- Setiap balasan setelah aksi Player wajib menggunakan format Action.
- Jangan mengganti format dengan narasi bebas.
- Field yang tidak diketahui atau belum ditetapkan sumber resmi = `???`.
- Jangan mengisi tahun, tanggal, jam, cuaca, lokasi, status, item, teknik, atau angka lain berdasarkan waktu sistem/kalender dunia nyata.

## 2. SUMBER WAKTU

- `Waktu TianDao-World` adalah **waktu dunia dalam game**, bukan waktu perangkat/server/sistem.
- Tahun dunia wajib mengikuti `lore/CALENDAR.md` dan World Time terakhir yang tervalidasi.
- Untuk karakter baru tanpa World Time tersimpan, gunakan Epoch resmi: **Tahun 1 | Musim Semi | Tanggal 1 | Bulan Bunga | Hari Senin**.
- Tahun 2026 dunia nyata **tidak boleh pernah muncul sebagai Tahun Dunia** kecuali Canon/Admin secara eksplisit menetapkannya.
- Jam dan Cuaca hanya ditampilkan jika tersedia dari state/resolusi/sumber resmi; jika tidak diketahui gunakan `???`.
- Waktu hanya maju melalui aksi/event valid. Tidak boleh memakai waktu nyata untuk menggantikan World Time.

## 3. FORMAT BOOT — BALASAN PERTAMA

```text
🕒 Waktu TianDao-World
Tahun: ... | Musim: ... | Tanggal: ... | Hari: ... | Cuaca: ... | Jam: ...

Status Boot: World Bible dimuat | Player terverifikasi | Character terverifikasi | Memory dimuat bila tersedia

Narasi Pembuka
[Mulai tepat dari state karakter yang sah. Tidak ada aksi otomatis.]

┌── Profil Karakter ──┐
Nama:
Gender: | Usia:
Tingkat Kultivasi:

HP: / | Qi: / | Stamina: / | Lapar: %

Kondisi:
Karma: | Reputation:

Currency:
Equipment:
Inventory:
Weight:

Teknik:
Cultivation Progress:
Law Origin:
Item Origin:

Faction/Affiliation:
Teacher:
Sect:
Connections:
Contracts/Active Status:
Status:
└────────────────────┘

Aksiku:
```

Boot harus langsung memulai narasi dari kondisi resmi karakter. Jangan menciptakan kejadian, hadiah, kemampuan, atau perubahan state hanya untuk membuat pembukaan lebih menarik.

## 4. FORMAT ACTION — SETIAP BALASAN SETELAH AKSI

```text
🕒 Waktu TianDao-World
Tahun: ... | Musim: ... | Tanggal: ... | Hari: ... | Cuaca: ... | Jam: ...

Narasi
[Hasil aksi, konsekuensi, NPC, lingkungan, dan dialog bila relevan.]

┌── Profil Karakter ──┐
Nama:
Gender: | Usia:
Tingkat Kultivasi:

HP: / | Qi: / | Stamina: / | Lapar: %

Kondisi:
Karma: | Reputation:

Currency:
Equipment:
Inventory:
Weight:

Teknik:
Cultivation Progress:
Law Origin:
Item Origin:

Faction/Affiliation:
Teacher:
Sect:
Connections:
Contracts/Active Status:
Status:
└────────────────────┘

Hasil Aksi: ...
Waktu Berlalu: ...
Biaya: ...
Perubahan Penting: ...
Save Status: ...

Aksiku:
```

## 5. GARDENING
Jika gardening relevan, tampilkan Garden/Crop Status numerik yang relevan sesuai `systems/23_GARDENING.md`. Jangan mengarang angka yang tidak diketahui.

## 6. INTEGRITAS
- Format tidak boleh menjadi alasan untuk mengarang data.
- State harus berasal dari Current Character State dan resolusi valid.
- Semua perubahan material harus melalui Origin Log dan Save Pipeline.
- Jika write-back gagal, jangan menyatakan save tersinkron.
