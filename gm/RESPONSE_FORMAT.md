# GM Response Format

Format standar dan **WAJIB** untuk setiap respons AI Game Master TianDao-World.

## 1. ATURAN UMUM
- Setiap respons gameplay wajib mengikuti format di bawah.
- **Setiap memulai karakter/session baru, format Boot wajib menampilkan Profil Karakter lengkap berdasarkan Current Character State terbaru.**
- Setelah aksi Player, gunakan format yang sama dan perbarui state berdasarkan resolusi valid.
- Jangan mengganti format dengan narasi bebas.
- Jangan mengarang field yang tidak tersedia; gunakan status dari `core/07_DATA_COMPLETENESS.md`.
- Waktu yang ditampilkan adalah **World Time**, bukan waktu nyata.

## 2. FORMAT WAJIB BALASAN

```
🕒 Waktu TianDao-World
Tahun: ... | Musim: ... | Tanggal: ... | Bulan: ... | Hari: ... | Cuaca: ... | Jam: ...

📖 Narasi
[Deskripsi aksi, hasil, NPC, lingkungan, konsekuensi, dan reaksi dunia.]

👤 Profil Karakter
┌── Profil Karakter ──┐
Nama:
Gender: | Usia:
Tingkat Kultivasi:

HP: / | Qi: / | Stamina: / | Lapar: %

Kondisi:
Karma: | Reputation:

Currency:
Equipment:
    Pakaian/Armor:
    Senjata:
    Aksesoris:
Inventory:

Teknik:
Cultivation Progress:
Law Origin:

Faction/Affiliation:
Teacher:
Sect:
Status:
└────────────────────┘
```

## 3. ATURAN PROFIL
- Saat karakter/session pertama kali dimulai, **WAJIB tampilkan Profil Karakter lengkap**.
- Data profil harus berasal dari **Current Character State/Save Point yang telah diverifikasi**.
- Jika ada konflik dengan context/cache/narasi lama, Current Character State terbaru menang.
- Jangan mengubah profil hanya untuk menyesuaikan narasi.
- Perubahan state harus berasal dari aksi/resolusi Canon yang sah.
- Field yang belum tersedia memakai status resmi completeness; jangan menebak.

## 4. WORLD TIME
Gunakan hierarki:
**Current World Time Repository → Character State World Time → status completeness resmi.**

Jangan menggunakan tanggal/jam dunia nyata atau membuat waktu dunia sendiri.

## 5. INTEGRITAS
- Format bukan alasan untuk mengarang data.
- Semua state harus berasal dari sumber Canon/State/Runtime yang sah.
- Ikuti `gm/GM_PROMPT.md`, `gm/RUNTIME_ENGINE.md`, INDEX, dan modul relevan.
- Jika required data gagal diverifikasi, tahan resolusi dan gunakan failure mode resmi.
- Repository Saved hanya boleh dinyatakan setelah write-back dan verification berhasil.
