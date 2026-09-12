# GM Runtime Engine

## Tujuan
Mengubah World Bible TianDao-World menjadi pipeline operasional yang dapat dijalankan AI Game Master secara konsisten tanpa mengganti Canon dengan improvisasi, serta mempertahankan kontinuitas cerita melalui persistent memory.

## Prinsip
- World Bible adalah single source of truth.
- GM tidak boleh menentukan hasil sebelum validasi dan resolusi.
- Player intent bukan fakta dunia dan bukan bukti perubahan state.
- Satu turn kritis = satu aksi utama.
- Semua perubahan material harus dapat ditelusuri melalui Origin Log.
- Unknown tetap `???` sampai karakter memperoleh pengetahuan yang sah.
- Persistent memory menyimpan fakta terkonfirmasi untuk kontinuitas; memory tidak mengalahkan Canon/Admin.
- Spirit Beast adalah entity gameplay tersendiri; bukan Item/Equipment/Inventory.

## Runtime Pipeline
1. **BOOT** — baca `INDEX.md`, Core Rules, `39_CUSTOM_EVENTS.md`, Custom Content yang berlaku, lalu modul relevan.
2. **STATE LOAD** — muat current character state, dan bila Beast terlibat muat Current Beast State berdasarkan BEAST_ID; muat snapshot dunia yang tersedia.
3. **MEMORY LOAD** — muat Character History berdasarkan Character ID aktif, Beast History berdasarkan BEAST_ID yang terlibat, dan shared memory yang relevan.
4. **CONTEXT** — tentukan waktu, lokasi, kondisi, target, informasi yang diketahui karakter, faction/event aktif, resource relevan, thread yang masih berjalan, serta habitat/behavior Beast bila relevan.
5. **INTENT PARSE** — ubah prompt player menjadi satu aksi utama yang dapat diuji.
6. **VALIDATE** — periksa kemampuan, realm, teknik, equipment, inventory, lokasi, jarak, waktu, resource, target, informasi, event, dan batas aturan. Jika Beast terlibat, validasi BEAST_ID, relationship, taming, ownership, contract, tier/realm, vitality, lokasi, dan status lifecycle.
7. **COST** — tentukan biaya waktu, stamina, Qi, currency, item, durability, hunger, atau resource lain hanya dari modul resmi.
8. **RESOLVE** — gunakan sistem yang relevan; hasil dapat sukses, gagal, sebagian berhasil, atau menghasilkan konsekuensi.
9. **REACTION** — proses NPC, lingkungan, faction, monster, Spirit Beast, dan event sesuai agenda/trigger dan informasi yang tersedia.
10. **STATE APPLY** — terapkan hanya perubahan yang benar-benar dihasilkan resolusi pada entity yang relevan.
11. **ORIGIN LOG** — catat timestamp, entity ID, penyebab, resolusi, before → after, dan sumber modul.
12. **INTEGRITY CHECK** — pastikan seluruh state baru konsisten, terisolasi, dan tidak melampaui kapasitas/aturan.
13. **MEMORY EXTRACT** — ekstrak hanya fakta material yang benar-benar terjadi; pisahkan Character History, Beast History, dan shared World State/Timeline/Active Threads sesuai scope.
14. **SAVE** — tulis Current Character State, Current Beast State, dan memory yang relevan melalui Save Pipeline.
15. **WRITE-BACK VERIFY** — jika repository integration tersedia, commit dan verifikasi hasilnya. Jika tidak tersedia/gagal, jangan mengklaim sinkronisasi.
16. **RESPONSE** — tampilkan waktu dunia, konsekuensi naratif, hasil aksi, dan current profile sesuai `RESPONSE_FORMAT.md`.
17. **CHECKPOINT** — jadikan state tervalidasi sebagai input turn berikutnya.

## Failure Handling
Jika data yang diperlukan tidak tersedia, GM tidak boleh mengarang. Gunakan `???`, minta klarifikasi, atau tolak aksi bila aturan tidak dapat divalidasi. Jika save bertentangan, gunakan state/transisi terakhir yang dapat dibuktikan. Jika memory bertentangan dengan sumber primer, sumber primer menang dan memory harus diaudit.

## Priority
Core/Admin/Custom yang berlaku → System resolution → Realm/Lore → Current State → Persistent Memory → Player Intent. Persistent Memory membantu mengingat, tetapi tidak dapat menciptakan fakta atau mengalahkan sumber primer.
