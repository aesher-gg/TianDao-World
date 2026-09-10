# AUDIT INTEGRITAS YELLOW — TIANDAO-WORLD

## Status
Audit menyeluruh terhadap hasil pengembangan Yellow. Audit ini **tidak memulai item ❌** dan tidak menambah canon baru tanpa sumber.

## Scope
Dicek terhadap:
- `INDEX.md`
- `realms/01_WORLD_MAP.md`
- seluruh modul regional `realms/02`–`realms/07`
- database sect, dojo, imperial, criminal, organization
- `lore/CITY_VILLAGE_DATABASE.md`
- `lore/NPC_DATABASE.md`
- `core/04_ANTI_CHEAT.md`
- `core/05_SAVE_INTEGRITY.md`
- `custom/41_CUSTOM_SECTS.md`
- `events/39_CUSTOM_EVENTS.md`

## Hasil Ringkas
### PASS — Tidak ditemukan konflik nama exact pada registry utama
- ID faction pada database Yellow menggunakan namespace terpisah: SEC, DOJ, ORG, CRI.
- `Seratus Racun` tidak lagi muncul; nama aktif adalah **Serikat Seratus Daun**.
- **Paviliun Seribu Daun** dan **Serikat Seratus Daun** bukan nama exact yang sama. Keduanya wajib diperlakukan sebagai dua faction berbeda.
- `Aula Segel Tianhe` dan `Persekutuan Pengrajin Tianhe` juga merupakan dua faction berbeda; kemiripan kata tidak boleh dianggap sebagai identitas yang sama.

### FIXED — Konflik deskripsi Serikat Seratus Daun
Temuan awal: modul Domain Yaohuang Selatan menggambarkan Serikat Seratus Daun sebagai organisasi pemburu/pedagang bahan alam langka, sedangkan registry kriminal CRI-001 menetapkannya sebagai faction kriminal dengan penyelundupan, kontrak ilegal dan informasi.

Perbaikan: deskripsi regional sekarang menyatakan bahwa aktivitas pemburu/pedagang dapat menjadi tampilan permukaan, sementara aktivitas ilegal mengikuti registry CRI-001. Status kriminal dan konsekuensi hukum tidak hilang. Dengan demikian satu faction memiliki identitas yang konsisten lintas modul.

### FIXED — Sinkronisasi lokasi
Registry kota/desa sebelumnya tidak memuat semua permukiman yang disebut modul regional. Registry sekarang menampung seluruh kota/desa/pos/benteng/pelabuhan yang dirujuk, sekaligus membedakan lokasi non-permukiman seperti lembah, hutan, puncak, reruntuhan, oasis dan wilayah laut/gurun.

Contoh yang disinkronkan: Kota Lingshan, Desa Yunmu, Kota Nanyao, Pelabuhan Chixia, Benteng Hanjiang, Desa Xuehe, Kota Shajing, Kota Jinyue, serta lokasi non-permukiman seperti Lembah Qinghe.

### OPEN — Referensi Dojo Godam Besi belum memiliki registry faction
`Desa Tiedao` merujuk pada lapangan uji **Dojo Godam Besi**, tetapi dojo tersebut belum memiliki entri di `factions/dojos/00_DOJO_DATABASE.md`.

Keputusan audit: **jangan mengarang kepala dojo, struktur, spesialisasi, teknik, NPC, rank, atau modifier.** Referensi lokasi dipertahankan karena sudah menjadi fakta pada registry lokasi, tetapi interaksi faction yang membutuhkan data resmi harus dianggap belum terdefinisi sampai Admin mendaftarkannya.

### OPEN — Faction regional belum seluruhnya masuk global registry
Beberapa faction pada modul regional belum memiliki ID pada database faction global. Ini bukan bukti kontradiksi isi, tetapi merupakan celah sinkronisasi yang dapat menyebabkan GM membuat data ganda.

Faction yang perlu registry resmi sebelum diberi data operasional tambahan:
- Pegunungan Qingluan: Sekte Gunung Qingluan; Istana Bambu Giok; Paviliun Pemburu Roh.
- Domain Yaohuang Selatan: Istana Yaohuang; Sekte Api Merah.
- Laut Dongming: Istana Naga Dongming; Sekte Pedang Ombak; Aliansi Pedagang Haixu.
- Tanah Salju Beiming: Sekte Salju Xuanyin; Benteng Besi Beichen; Paviliun Salju Putih.
- Gurun Jinyan: Kuil Sembilan Teratai; Sekte Pasir Emas; Liga Kafilah Jinyue.

Aturan sementara: modul regional hanya boleh menggunakan fakta yang sudah tertulis di modul tersebut untuk faction-faction ini. GM tidak boleh mengisi struktur, pemimpin, teknik, aset, rank, bonus, atau agenda tambahan dari tebakan.

### PASS — NPC knowledge / information leakage
NPC Database tidak memberikan realm, inventory, lokasi rahasia, teknik tersembunyi, atau akses global yang tidak perlu. Pengetahuan NPC dibatasi oleh peran, pengalaman dan akses. NPC kriminal `???` tetap dilindungi dari kebocoran identitas.

Tambahan pengaman pada Anti-Cheat: NPC tidak boleh mengetahui identitas, lokasi, inventory, niat, teknik atau riwayat player hanya karena diketahui GM/pembaca.

### PASS — Relasi faction utama
Relasi yang diperiksa tidak memiliki kontradiksi langsung yang memaksa dua sikap berlawanan pada faction yang sama. Kompetisi Canglan–Feiyun konsisten antara database dan Dataran Cangyuan. Hubungan Dinasti–faction juga tetap bersifat selektif/kontraktual dan tidak mengubah faction independen menjadi bawahan otomatis.

Relasi regional tetap diperlakukan sebagai hubungan dasar, bukan keadaan permanen yang meniadakan agenda NPC atau event.

### PASS — Anti-cheat / save integrity setelah hardening
Celah yang diperkuat:
- klaim item/currency/technique/status tanpa provenance;
- time skip tersembunyi dan aksi berantai ilegal;
- auto-hit/auto-crit/auto-kill;
- penghapusan status negatif tanpa pemulihan;
- kebocoran knowledge NPC;
- perubahan Current State tanpa transisi;
- retcon terhadap inventory, debt, cooldown, reputation, faction rank dan waktu;
- generated GM content yang diam-diam menjadi canon dunia luas;
- recovery save dengan tebakan yang menguntungkan player.

`core/05_SAVE_INTEGRITY.md` sekarang mewajibkan Origin Log untuk perubahan material dan pemeriksaan sebelum menerima state baru.

## Kesimpulan Audit
**Yellow lulus audit integritas pada level aturan inti, dengan 2 open sync items:**
1. Dojo Godam Besi belum diregistrasikan.
2. 14 faction regional belum memiliki entri global registry.

Kedua temuan tersebut sengaja **tidak diisi dengan data buatan** selama audit. Penyelesaian harus berasal dari keputusan Canon/Admin atau tahap pengembangan berikutnya.

**Status ❌:** BELUM DIMULAI.
