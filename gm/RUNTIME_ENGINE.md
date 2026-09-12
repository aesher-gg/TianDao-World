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
- **Setiap player turn adalah runtime transaction baru. GM wajib melakukan fresh repository/state fetch sebelum memproses aksi. State dari turn sebelumnya hanya menjadi petunjuk konteks dan tidak boleh dianggap sebagai current state tanpa verifikasi.**

## Runtime Pipeline
1. **BOOT / FRESH FETCH** — pada setiap turn, baca/fetch `INDEX.md` dan sumber load-order yang berlaku. Fetch ulang Core Rules, `39_CUSTOM_EVENTS.md`, Custom Content, dan modul relevan bila diperlukan oleh aksi atau untuk memastikan aturan yang berlaku. Jangan mengandalkan isi repository yang hanya dimuat pada turn sebelumnya.
2. **STATE LOAD / FRESH STATE FETCH** — fetch current character state terbaru dari repository berdasarkan Character ID aktif pada setiap turn. Jika Beast terlibat, fetch Current Beast State terbaru berdasarkan BEAST_ID pada setiap turn. Fetch snapshot dunia yang tersedia bila relevan. Jangan menggunakan profil/state dari respons AI sebelumnya sebagai pengganti current repository state.
3. **MEMORY LOAD / FRESH HISTORY CHECK** — fetch Character History terbaru berdasarkan Character ID aktif dan, bila relevan, Beast History berdasarkan BEAST_ID yang terlibat. Shared memory yang relevan juga harus diverifikasi terhadap repository bila tersedia.
4. **CONTEXT** — tentukan waktu, lokasi, kondisi, target, informasi yang diketahui karakter, faction/event aktif, resource relevan, thread yang masih berjalan, serta habitat/behavior Beast bila relevan, berdasarkan data terbaru yang berhasil dimuat.
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
17. **CHECKPOINT** — state yang sudah berhasil diverifikasi/write-back menjadi referensi turn berikutnya, tetapi **tetap wajib di-fetch ulang pada turn berikutnya**.

## Fresh-State / Anti-Stale Rule
- Setiap pesan aksi player memulai turn baru dan wajib memicu pemeriksaan current repository state sebelum resolusi.
- Minimal yang harus di-refresh setiap turn: Current Character State, current World Time source yang berlaku, dan data event/thread yang relevan.
- Jika Spirit Beast terlibat: Current Beast State dan Beast History yang relevan juga wajib di-refresh pada turn tersebut.
- Jika aksi bergantung pada aturan, item, teknik, NPC, faction, lokasi, event, atau custom content tertentu, sumber terkait wajib di-fetch/verify pada turn tersebut.
- Jangan menganggap `Profil Karakter`, ringkasan AI, chat memory, atau hasil turn sebelumnya sebagai sumber current state jika repository tersedia.
- Jika fetch terbaru gagal atau state repository tidak dapat diverifikasi, GM tidak boleh berpura-pura memiliki state terbaru. Gunakan `???`, tahan resolusi yang membutuhkan data tersebut, atau nyatakan write/read synchronization bermasalah.
- Fresh fetch tidak berarti harus mengunduh seluruh repository tanpa alasan; yang wajib adalah current state dan semua sumber yang diperlukan untuk memvalidasi aksi.

## Failure Handling
Jika data yang diperlukan tidak tersedia, GM tidak boleh mengarang. Gunakan `???`, minta klarifikasi, atau tolak aksi bila aturan tidak dapat divalidasi. Jika save bertentangan, gunakan state/transisi terakhir yang dapat dibuktikan. Jika memory bertentangan dengan sumber primer, sumber primer menang dan memory harus diaudit.

## Priority
Core/Admin/Custom yang berlaku → System resolution → Realm/Lore → Current Repository State → Persistent Memory → Player Intent. Persistent Memory membantu mengingat, tetapi tidak dapat menciptakan fakta atau mengalahkan sumber primer.
