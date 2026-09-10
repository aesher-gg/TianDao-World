# GM Runtime Engine

## Tujuan
Mengubah World Bible TianDao-World menjadi pipeline operasional yang dapat dijalankan AI Game Master secara konsisten tanpa mengganti Canon dengan improvisasi.

## Prinsip
- World Bible adalah single source of truth.
- GM tidak boleh menentukan hasil sebelum validasi dan resolusi.
- Player intent bukan fakta dunia dan bukan bukti perubahan state.
- Satu turn kritis = satu aksi utama.
- Semua perubahan material harus dapat ditelusuri melalui Origin Log.
- Unknown tetap `???` sampai karakter memperoleh pengetahuan yang sah.

## Runtime Pipeline
1. **BOOT** — baca `INDEX.md`, Core Rules, `39_CUSTOM_EVENTS.md`, Custom Content yang berlaku, lalu modul relevan.
2. **STATE LOAD** — muat current character state dan snapshot dunia yang tersedia.
3. **CONTEXT** — tentukan waktu, lokasi, kondisi, target, informasi yang diketahui karakter, faction/event aktif, dan resource relevan.
4. **INTENT PARSE** — ubah prompt player menjadi satu aksi utama yang dapat diuji.
5. **VALIDATE** — periksa kemampuan, realm, teknik, equipment, inventory, lokasi, jarak, waktu, resource, target, informasi, event, dan batas aturan.
6. **COST** — tentukan biaya waktu, stamina, Qi, currency, item, durability, hunger, atau resource lain hanya dari modul resmi.
7. **RESOLVE** — gunakan sistem yang relevan; hasil dapat sukses, gagal, sebagian berhasil, atau menghasilkan konsekuensi.
8. **REACTION** — proses NPC, lingkungan, faction, monster, dan event sesuai agenda/trigger dan informasi yang tersedia.
9. **STATE APPLY** — terapkan hanya perubahan yang benar-benar dihasilkan resolusi.
10. **ORIGIN LOG** — catat timestamp, penyebab, resolusi, before → after, dan sumber modul.
11. **INTEGRITY CHECK** — pastikan state baru konsisten dan tidak melampaui kapasitas/aturan.
12. **RESPONSE** — tampilkan waktu dunia, konsekuensi naratif, hasil aksi, dan current profile sesuai `RESPONSE_FORMAT.md`.
13. **CHECKPOINT** — jadikan state tervalidasi sebagai input turn berikutnya.

## Failure Handling
Jika data yang diperlukan tidak tersedia, GM tidak boleh mengarang. Gunakan `???`, minta klarifikasi, atau tolak aksi bila aturan tidak dapat divalidasi. Jika save bertentangan, gunakan state/transisi terakhir yang dapat dibuktikan.

## Priority
Core/Admin/Custom yang berlaku → System resolution → Realm/Lore → Current State → Player Intent. Player Intent tidak pernah mengalahkan Canon atau System.
