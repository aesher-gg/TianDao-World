# 20 — RUTE, JARAK & SATUAN PERJALANAN

## Status Canon
Modul ini menjadi registry rute utama dan baseline jarak dunia. **Satuan jarak resmi TianDao-World adalah Li (里).** Untuk jarak yang lebih kecil dari 1 Li, gunakan **Fen (分)** dan, bila presisi sangat kecil diperlukan, **Cun (寸)**. Jarak adalah jarak rute, bukan garis lurus. Waktu aktual dihitung dari sarana, medan, cuaca, beban, stamina, suplai, kondisi karakter, dan hambatan yang benar-benar berlaku.

## Konversi Resmi
- **1 Li (里) = 10 Fen (分) = 100 Cun (寸).**
- **1 Li = 500 meter = 0,5 km.**
- **1 Fen = 0,1 Li = 50 meter.**
- **1 Cun = 0,01 Li = 5 meter.**
- Meter/kilometer hanya boleh digunakan sebagai konversi penjelas jika diperlukan; bukan satuan runtime utama.
- Gunakan Li untuk jarak perjalanan/geografi dan Fen untuk jarak pendek. Cun dipakai hanya bila presisi sangat kecil benar-benar relevan.
- Semua jarak baru di World Bible, NPC, perjalanan, lokasi, encounter, combat range, dan event harus dinyatakan dalam Li/Fen/Cun sesuai skala kecuali sumber Canon/Admin menetapkan satuan khusus.

## Panduan Pemakaian
- **Li:** perjalanan, jarak antarlokasi, radius wilayah, peta, ekspedisi, dan jarak geografis.
- **Fen:** jarak pendek antarkarakter, jarak encounter, jangkauan serangan, posisi dalam arena, atau jarak objek yang kurang dari 1 Li.
- **Cun:** presisi sangat kecil seperti jarak antarobjek/posisi tubuh ketika Fen terlalu kasar.
- Jangan menulis `0,5 Li` dalam runtime bila dapat ditulis lebih alami sebagai **5 Fen**.
- Jangan mengubah jarak yang belum diketahui menjadi angka. Gunakan `UNRESOLVED` sampai ada sumber yang sah.

## Aturan Dasar
- Semua perjalanan menghabiskan waktu nyata dalam state dunia.
- Aksi non-kultivasi tetap maksimal 3 jam per turn; perjalanan panjang harus dipecah menjadi beberapa turn/checkpoint bila berlangsung melewati batas tersebut.
- Angka jarak tidak otomatis berarti durasi tetap.
- Jalan kaki, tunggangan, karavan, kapal, dan metode kultivasi memiliki kecepatan berbeda sesuai data sistem/metode yang sah.
- Cuaca buruk, encounter, cedera, kehilangan arah, pemeriksaan, dan kerusakan sarana dapat memperpanjang perjalanan.
- Teleportasi/transportasi khusus hanya sah jika sumber Canon menyediakannya.

## Baseline Kecepatan Resmi
Baseline berikut adalah **kecepatan perjalanan standar** pada kondisi normal, sarana layak, beban wajar, jalur dapat dilalui, cuaca tidak menghambat, dan tanpa kejadian tambahan. Baseline ini dipakai hanya jika jenis sarana sudah diketahui tetapi tidak ada modifier khusus yang berlaku.

| Metode | Kecepatan baseline |
|---|---:|
| Jalan kaki | 8 Li/jam |
| Tunggangan darat biasa | 20 Li/jam |
| Karavan darat biasa | 12 Li/jam |
| Kapal dagang/kapal perjalanan biasa | 30 Li/jam |

### Aturan Kecepatan
- Baseline di atas bukan jaminan durasi rute; hambatan yang benar-benar terjadi tetap dihitung.
- Jangan membuat multiplier, bonus persen, penalti persen, atau kecepatan baru untuk medan/cuaca/beban/cedera tanpa sumber Canon/Admin yang menetapkannya.
- Jika sarana khusus, tunggangan khusus, teknik kultivasi, artefak transportasi, atau efek lain memiliki kecepatan resmi, gunakan nilai resmi tersebut dan jangan memakai baseline generik di atas.
- Metode kultivasi/gerakan khusus tidak memiliki baseline generik. Jika belum memiliki nilai resmi, durasi harus ditahan sampai metode/sarana dengan kecepatan resmi tersedia.
- Jika jenis sarana tidak diketahui, jangan mengasumsikan jalan kaki; sarana harus ditentukan sebelum durasi numerik dihitung.
- Jika suatu modifier disebutkan tetapi tidak memiliki nilai numerik resmi, modifier tersebut tidak boleh dikonversi menjadi angka oleh GM.

## Kategori Jarak
- **Sangat dekat:** <20 Li
- **Dekat:** 20–60 Li
- **Sedang:** >60–160 Li
- **Jauh:** >160–400 Li
- **Sangat jauh:** >400–1.000 Li
- **Antarkawasan:** >1.000 Li atau lintasan laut/medan ekstrem; wajib memakai rute dan sarana yang sah.

## Rute Regional — Dataran Cangyuan
| Rute | Jarak baseline | Medan |
|---|---:|---|
| Kota Yunjing ↔ Kota Luoxing | 144 Li | jalan dagang |
| Kota Luoxing ↔ Desa Baihe | 76 Li | jalur pertanian/sungai |
| Kota Luoxing ↔ Kota Heiyu | 252 Li | jalur dagang/perbatasan |
| Desa Baihe ↔ Lembah Qinghe | 108 Li | jalan pedalaman |

## Rute Regional — Pegunungan Qingluan
| Rute | Jarak baseline | Medan |
|---|---:|---|
| Kota Lingshan ↔ Desa Yunmu | 48 Li | kaki gunung/jalur pemburu |
| Kota Lingshan ↔ Lembah Qingsong | 92 Li | jalur spiritual |
| Lembah Qingsong ↔ Puncak Tianque | 62 Li | pendakian sulit |
| Desa Yunmu ↔ Hutan Wuyin | 38 Li | hutan/kabut |

## Rute Regional — Domain Yaohuang Selatan
| Rute | Jarak baseline | Medan |
|---|---:|---|
| Kota Nanyao ↔ Pelabuhan Chixia | 122 Li | jalur perdagangan |
| Kota Nanyao ↔ Hutan Cangmang | 36 Li | pintu hutan |
| Hutan Cangmang ↔ Lembah Seratus Bunga | 94 Li | pedalaman/berisiko |
| Kota Nanyao ↔ Pegunungan Huoyan | 166 Li | jalur pegunungan |

## Rute Regional — Laut Dongming
| Rute | Jarak baseline | Medan |
|---|---:|---|
| Kota Haicheng ↔ Pulau Yuehai | 192 Li | laut utama |
| Pulau Yuehai ↔ Kepulauan Lanyue | 276 Li | laut antarpulau |
| Kota Haicheng ↔ Pulau Qionghua | 328 Li | jalur dagang spiritual |
| Kepulauan Lanyue ↔ Jurang Laut Canglong | 436 Li | laut dalam/ekspedisi |

## Rute Regional — Tanah Salju Beiming
| Rute | Jarak baseline | Medan |
|---|---:|---|
| Kota Beixue ↔ Benteng Hanjiang | 154 Li | jalur benteng |
| Benteng Hanjiang ↔ Desa Xuehe | 86 Li | jalur permukiman |
| Desa Xuehe ↔ Lembah Bingxin | 138 Li | ekspedisi es |
| Kota Beixue ↔ Reruntuhan Tianhan | 308 Li | ekspedisi utara |

## Rute Regional — Gurun Jinyan
| Rute | Jarak baseline | Medan |
|---|---:|---|
| Kota Shajing ↔ Kota Jinyue | 182 Li | jalur kafilah |
| Kota Shajing ↔ Oasis Qingyu | 114 Li | gurun/persinggahan |
| Kota Jinyue ↔ Laut Pasir Wuheng | 84 Li | ekspedisi gurun |
| Laut Pasir Wuheng ↔ Makam Tianri | 236 Li | gurun/ekspedisi |

## Rute — Jantung Tianyuan
| Rute | Jarak baseline | Medan |
|---|---:|---|
| Kota Tianjing ↔ Kota Baiyu | 84 Li | jalan administrasi/akademi |
| Kota Baiyu ↔ Desa Minghe | 66 Li | jalan agrikultur |
| Kota Tianjing ↔ Desa Minghe | 120 Li | jalan administrasi/agrikultur |

Jarak di atas adalah baseline rute Canon untuk perjalanan normal. Rute cabang tetap mengikuti kondisi aktual dan tidak boleh dianggap sebagai garis lurus.

## Koridor Antarkawasan — Baseline Canon
Koridor berikut menetapkan **rute utama**, bukan jarak garis lurus. Setiap koridor harus memakai titik jangkar yang disebut dan sarana yang sesuai.

| Koridor utama | Jarak baseline | Sarana/medan utama |
|---|---:|---|
| Kota Yunjing ↔ Kota Tianjing | 1.180 Li | jalan dagang/administrasi |
| Kota Yunjing ↔ Kota Lingshan | 420 Li | jalan darat/kaki gunung |
| Kota Yunjing ↔ Kota Nanyao | 1.860 Li | jalan dagang/perbatasan |
| Kota Yunjing ↔ Kota Haicheng | 1.740 Li | jalan dagang + pelabuhan |
| Kota Yunjing ↔ Kota Beixue | 2.420 Li | jalan dagang/benteng |
| Kota Yunjing ↔ Kota Jinyang | 2.060 Li | jalur dagang/kafilah |

Koridor di atas menjadi anchor rute dunia. Cabang atau rute alternatif tetap membutuhkan pencatatan Admin sebelum menjadi baseline baru.

## Perhitungan Waktu
`Waktu perjalanan = jarak rute / kecepatan efektif + hambatan.`

Kecepatan efektif harus berasal dari baseline resmi di atas atau sumber sarana/metode yang sah. Hambatan hanya boleh diberi nilai numerik bila sumber Canon/Admin menetapkan nilainya. Hambatan kualitatif tetap diterapkan sebagai konsekuensi tanpa dikonversi menjadi angka tersembunyi.

## Checkpoint
Setiap perjalanan yang melewati 3 jam aksi harus memiliki checkpoint state: waktu, lokasi, jarak tersisa, kondisi, stamina, suplai, cuaca dan kejadian. Tidak boleh ada time skip tersembunyi.

## Integrasi
Registry ini menjadi sumber rute dan konvensi jarak untuk World Map, Time, Action, Vitality, Economy, Monsters, Factions dan Events.

## DATA COMPLETENESS TRAVEL GATE
Jarak, rute, sarana, kecepatan, modifier, dan durasi numerik hanya boleh berasal dari source resmi yang tersedia. Jika field required tidak memiliki baseline sah, jangan mengarang angka atau mengasumsikan sarana; gunakan UNRESOLVED/RESOLUTION-BLOCKED sesuai Data Completeness.


## 20A — ROUTE RECORD STANDARD & MAINTENANCE HARDENING

### Route Record Contract
Setiap baseline route yang executable harus dapat dipetakan ke record berikut:
- `ROUTE_ID` — ID unik route.
- `ORIGIN` — settlement/location node Canon.
- `DESTINATION` — settlement/location node Canon.
- `DISTANCE_BASELINE` — jarak route resmi dalam Li/Fen/Cun.
- `TERRAIN` — medan yang sudah ditetapkan oleh source route.
- `PRIMARY_TRANSPORT` — sarana utama bila source menetapkannya.
- `ROUTE_STATUS` — `CANON-ESTABLISHED`, `UNRESOLVED`, atau `RESOLUTION-BLOCKED` sesuai Data Completeness.
- `SOURCE` — sumber Canon/Admin yang menetapkan record.
- `CHECKPOINT_RULE` — penerapan checkpoint bila perjalanan melewati batas aksi.
- `ACCESS_CONDITION` — kondisi akses yang memang memiliki source; jangan diasumsikan.

### Canon Route IDs
ID berikut mengidentifikasi seluruh baseline route yang **sudah memiliki angka** pada registry ini. ID tidak mengubah jarak atau menciptakan route baru.

#### Dataran Cangyuan
- `TRV-CGY-001` — Kota Yunjing ↔ Kota Luoxing — 144 Li — jalan dagang — CANON-ESTABLISHED.
- `TRV-CGY-002` — Kota Luoxing ↔ Desa Baihe — 76 Li — jalur pertanian/sungai — CANON-ESTABLISHED.
- `TRV-CGY-003` — Kota Luoxing ↔ Kota Heiyu — 252 Li — jalur dagang/perbatasan — CANON-ESTABLISHED.
- `TRV-CGY-004` — Desa Baihe ↔ Lembah Qinghe — 108 Li — jalan pedalaman — CANON-ESTABLISHED.

#### Pegunungan Qingluan
- `TRV-QGL-001` — Kota Lingshan ↔ Desa Yunmu — 48 Li — kaki gunung/jalur pemburu — CANON-ESTABLISHED.
- `TRV-QGL-002` — Kota Lingshan ↔ Lembah Qingsong — 92 Li — jalur spiritual — CANON-ESTABLISHED.
- `TRV-QGL-003` — Lembah Qingsong ↔ Puncak Tianque — 62 Li — pendakian sulit — CANON-ESTABLISHED.
- `TRV-QGL-004` — Desa Yunmu ↔ Hutan Wuyin — 38 Li — hutan/kabut — CANON-ESTABLISHED.

#### Domain Yaohuang Selatan
- `TRV-YHS-001` — Kota Nanyao ↔ Pelabuhan Chixia — 122 Li — jalur perdagangan — CANON-ESTABLISHED.
- `TRV-YHS-002` — Kota Nanyao ↔ Hutan Cangmang — 36 Li — pintu hutan — CANON-ESTABLISHED.
- `TRV-YHS-003` — Hutan Cangmang ↔ Lembah Seratus Bunga — 94 Li — pedalaman/berisiko — CANON-ESTABLISHED.
- `TRV-YHS-004` — Kota Nanyao ↔ Pegunungan Huoyan — 166 Li — jalur pegunungan — CANON-ESTABLISHED.

#### Laut Dongming
- `TRV-DGM-001` — Kota Haicheng ↔ Pulau Yuehai — 192 Li — laut utama — CANON-ESTABLISHED.
- `TRV-DGM-002` — Pulau Yuehai ↔ Kepulauan Lanyue — 276 Li — laut antarpulau — CANON-ESTABLISHED.
- `TRV-DGM-003` — Kota Haicheng ↔ Pulau Qionghua — 328 Li — jalur dagang spiritual — CANON-ESTABLISHED.
- `TRV-DGM-004` — Kepulauan Lanyue ↔ Jurang Laut Canglong — 436 Li — laut dalam/ekspedisi — CANON-ESTABLISHED.

#### Tanah Salju Beiming
- `TRV-BMG-001` — Kota Beixue ↔ Benteng Hanjiang — 154 Li — jalur benteng — CANON-ESTABLISHED.
- `TRV-BMG-002` — Benteng Hanjiang ↔ Desa Xuehe — 86 Li — jalur permukiman — CANON-ESTABLISHED.
- `TRV-BMG-003` — Desa Xuehe ↔ Lembah Bingxin — 138 Li — ekspedisi es — CANON-ESTABLISHED.
- `TRV-BMG-004` — Kota Beixue ↔ Reruntuhan Tianhan — 308 Li — ekspedisi utara — CANON-ESTABLISHED.

#### Gurun Jinyan
- `TRV-GJY-001` — Kota Shajing ↔ Kota Jinyue — 182 Li — jalur kafilah — CANON-ESTABLISHED.
- `TRV-GJY-002` — Kota Shajing ↔ Oasis Qingyu — 114 Li — gurun/persinggahan — CANON-ESTABLISHED.
- `TRV-GJY-003` — Kota Jinyue ↔ Laut Pasir Wuheng — 84 Li — ekspedisi gurun — CANON-ESTABLISHED.
- `TRV-GJY-004` — Laut Pasir Wuheng ↔ Makam Tianri — 236 Li — gurun/ekspedisi — CANON-ESTABLISHED.

#### Jantung Tianyuan
- `TRV-TYN-001` — Kota Tianjing ↔ Kota Baiyu — 84 Li — jalan administrasi/akademi — CANON-ESTABLISHED.
- `TRV-TYN-002` — Kota Baiyu ↔ Desa Minghe — 66 Li — jalan agrikultur — CANON-ESTABLISHED.
- `TRV-TYN-003` — Kota Tianjing ↔ Desa Minghe — 120 Li — jalan administrasi/agrikultur — CANON-ESTABLISHED.

#### Koridor Antarkawasan
- `TRV-XRG-001` — Kota Yunjing ↔ Kota Tianjing — 1.180 Li — jalan dagang/administrasi — CANON-ESTABLISHED.
- `TRV-XRG-002` — Kota Yunjing ↔ Kota Lingshan — 420 Li — jalan darat/kaki gunung — CANON-ESTABLISHED.
- `TRV-XRG-003` — Kota Yunjing ↔ Kota Nanyao — 1.860 Li — jalan dagang/perbatasan — CANON-ESTABLISHED.
- `TRV-XRG-004` — Kota Yunjing ↔ Kota Haicheng — 1.740 Li — jalan dagang + pelabuhan — CANON-ESTABLISHED.
- `TRV-XRG-005` — Kota Yunjing ↔ Kota Beixue — 2.420 Li — jalan dagang/benteng — CANON-ESTABLISHED.
- `TRV-XRG-006` — Kota Yunjing ↔ Kota Jinyang — 2.060 Li — jalur dagang/kafilah — CANON-ESTABLISHED.

### Route Coverage Audit — Settlement Database
Route registry **sudah memiliki baseline numerik**, tetapi tidak semua settlement pada `lore/CITY_VILLAGE_DATABASE.md` memiliki route langsung. Itu bukan izin untuk mengarang route.

Settlement/lokasi yang **belum memiliki route langsung yang terdaftar** harus tetap diperlakukan sebagai `UNRESOLVED` untuk hubungan tersebut sampai Admin menetapkan route baru dengan record lengkap:
- Kota Qingluan
- Kota Huoyan
- Desa Nanyue
- Desa Xingcun
- Desa Tiedao
- Pos Gunung Lianfeng
- Desa Yunhe
- Kota Nanyao ↔ kota/settlement Yaohuang lain di luar route yang tercatat
- Desa Nelayan Qingyu
- Kota Haicheng ↔ Pelabuhan Donghai
- Kota Haicheng ↔ settlement pesisir lain yang belum tercatat
- Kota Jinyang ↔ settlement Gurun Jinyan lain yang belum tercatat
- Kota Tianjing ↔ settlement Jantung Tianyuan lain di luar baseline yang tercatat

Catatan: daftar ini adalah **coverage gap**, bukan daftar route yang boleh ditebak. Route baru membutuhkan source Admin/Cannon yang menetapkan endpoint, jarak, medan, dan sarana yang relevan.

### Route Resolution Rules
1. Endpoint harus merupakan location node yang sudah Canon atau valid runtime location.
2. Jarak route tidak boleh dihitung sebagai garis lurus dari peta.
3. Jika route langsung tidak terdaftar tetapi terdapat beberapa route Canon yang membentuk chain, GM hanya boleh menghitung perjalanan multi-leg jika setiap leg memang sah dan endpoint-nya tersambung.
4. Tidak boleh membuat edge implisit hanya karena dua settlement berada dalam region yang sama.
5. Route distance tidak menentukan durasi tanpa transport speed yang sah.
6. Jika sarana tidak ditentukan dan durasi numerik dibutuhkan, resolution menggunakan `UNRESOLVED`/`RESOLUTION-BLOCKED`, bukan asumsi jalan kaki.
7. Route event, encounter, weather, checkpoint, dan state update harus mengikuti runtime systems; route registry hanya menyediakan baseline geografis.
8. Route yang belum memiliki baseline tidak boleh dibuat oleh GM hanya untuk menyelesaikan perjalanan Player.

### Travel Maintenance Status
**🟢 TRAVEL ROUTE DATABASE — BASELINE ROUTES ESTABLISHED & ROUTE-ID HARDENED**


## 20B — GLOBAL ROUTE CONNECTIVITY EXPANSION

### Status
**Admin Canon — Global Route Graph Connectivity Established**

Bagian ini menetapkan baseline route tambahan agar seluruh node yang tercatat dalam `lore/CITY_VILLAGE_DATABASE.md` memiliki jalur sah menuju jaringan global. Keterhubungan berarti **reachable melalui satu atau lebih route leg**, bukan setiap node harus memiliki direct route ke semua node lain.

### Route Tambahan — Dataran Cangyuan
| ROUTE_ID | Route | Distance | Terrain | Primary Transport | Status |
|---|---|---:|---|---|---|
| TRV-CGY-005 | Kota Yunjing ↔ Desa Xingcun | 58 Li | jalan desa/pertanian | Jalan kaki / tunggangan darat biasa | CANON-ESTABLISHED |
| TRV-CGY-006 | Kota Yunjing ↔ Desa Tiedao | 92 Li | jalan dagang/kerja logam | Jalan kaki / tunggangan darat biasa | CANON-ESTABLISHED |

### Route Tambahan — Pegunungan Qingluan
| ROUTE_ID | Route | Distance | Terrain | Primary Transport | Status |
|---|---|---:|---|---|---|
| TRV-QGL-005 | Kota Qingluan ↔ Kota Lingshan | 64 Li | kaki gunung/jalan dagang | Jalan kaki / tunggangan darat biasa | CANON-ESTABLISHED |
| TRV-QGL-006 | Kota Qingluan ↔ Desa Yunhe | 72 Li | lembah/jalur gunung | Jalan kaki / tunggangan darat biasa | CANON-ESTABLISHED |
| TRV-QGL-007 | Desa Yunhe ↔ Desa Yunmu | 54 Li | jalur lembah/hutan | Jalan kaki / tunggangan darat biasa | CANON-ESTABLISHED |
| TRV-QGL-008 | Kota Qingluan ↔ Pos Gunung Lianfeng | 118 Li | jalur pegunungan | Jalan kaki / tunggangan darat biasa | CANON-ESTABLISHED |

### Route Tambahan — Domain Yaohuang Selatan
| ROUTE_ID | Route | Distance | Terrain | Primary Transport | Status |
|---|---|---:|---|---|---|
| TRV-YHS-005 | Kota Nanyao ↔ Kota Huoyan | 88 Li | jalan selatan/panas | Jalan kaki / tunggangan darat biasa | CANON-ESTABLISHED |
| TRV-YHS-006 | Kota Nanyao ↔ Desa Nanyue | 74 Li | jalur perbatasan/desa | Jalan kaki / tunggangan darat biasa | CANON-ESTABLISHED |

### Route Tambahan — Laut Dongming
| ROUTE_ID | Route | Distance | Terrain | Primary Transport | Status |
|---|---|---:|---|---|---|
| TRV-DGM-005 | Pelabuhan Donghai ↔ Kota Haicheng | 52 Li | jalan pesisir | Jalan kaki / tunggangan darat biasa | CANON-ESTABLISHED |
| TRV-DGM-006 | Kota Haicheng ↔ Desa Nelayan Qingyu | 68 Li | jalan pesisir | Jalan kaki / tunggangan darat biasa | CANON-ESTABLISHED |

### Route Tambahan — Tanah Salju Beiming
| ROUTE_ID | Route | Distance | Terrain | Primary Transport | Status |
|---|---|---:|---|---|---|
| TRV-BMG-005 | Kota Beixue ↔ Desa Hanlin | 72 Li | jalur salju/permukiman | Jalan kaki / tunggangan darat biasa | CANON-ESTABLISHED |
| TRV-BMG-006 | Desa Xuehe ↔ Pos Es Fengbei | 64 Li | jalur sungai beku/salju | Jalan kaki / tunggangan darat biasa | CANON-ESTABLISHED |

### Route Tambahan — Gurun Jinyan
| ROUTE_ID | Route | Distance | Terrain | Primary Transport | Status |
|---|---|---:|---|---|---|
| TRV-GJY-005 | Kota Jinyang ↔ Kota Shajing | 96 Li | jalur oasis/kafilah | Karavan darat biasa / tunggangan darat biasa | CANON-ESTABLISHED |
| TRV-GJY-006 | Kota Jinyang ↔ Desa Shazhen | 54 Li | jalur oasis | Jalan kaki / tunggangan darat biasa | CANON-ESTABLISHED |
| TRV-GJY-007 | Kota Jinyue ↔ Pos Karavan Huangfeng | 70 Li | jalur kafilah gurun | Karavan darat biasa / tunggangan darat biasa | CANON-ESTABLISHED |
| TRV-GJY-008 | Kota Shajing ↔ Pos Karavan Huangfeng | 82 Li | jalur kafilah gurun | Karavan darat biasa / tunggangan darat biasa | CANON-ESTABLISHED |

### Global Connectivity Rules
1. Semua settlement dan non-settlement regional location yang tercatat pada City/Village Database kini memiliki sedikitnya satu edge route dalam graph ini.
2. Route baru di atas adalah **baseline geografis Canon**, bukan jaminan sarana tersedia pada saat Character melakukan perjalanan. Ketersediaan sarana tetap diverifikasi pada runtime.
3. Primary Transport menunjukkan sarana yang kompatibel dengan karakteristik route; jika sarana aktual tidak diketahui, GM tidak boleh mengubahnya menjadi durasi numerik tanpa validasi runtime.
4. Jalur laut tetap mengikuti aturan kapal, cuaca, pelayaran, dan checkpoint. Route registry tidak menjamin keberangkatan kapal.
5. Route darat tetap tunduk pada kondisi medan, cuaca, keamanan, suplai, stamina, encounter, dan event yang benar-benar berlaku.
6. Route graph tidak menciptakan jalan pintas. Perjalanan antarnode yang tidak memiliki direct edge harus menggunakan chain dari route yang masing-masing valid.
7. Jarak multi-leg adalah jumlah route leg yang benar-benar dipakai; tidak boleh menggantikan chain dengan jarak garis lurus atau direct route yang tidak tercatat.
8. Semua perjalanan lebih dari 3 jam aksi wajib menggunakan checkpoint sesuai aturan modul ini dan Time System.

### Connectivity Verification Target
Node yang sebelumnya berada di coverage gap sekarang masuk ke graph melalui route berikut:
- Xingcun → Yunjing
- Tiedao → Yunjing
- Qingluan → Lingshan/Yunhe/Lianfeng
- Yunhe → Yunmu → jaringan Lingshan
- Huoyan → Nanyao
- Nanyue → Nanyao
- Pelabuhan Donghai → Haicheng → jaringan Laut Dongming
- Desa Nelayan Qingyu → Haicheng
- Hanlin → Beixue
- Pos Es Fengbei → Xuehe
- Jinyang → Shajing → jaringan Gurun Jinyan
- Shazhen → Jinyang
- Pos Karavan Huangfeng → Jinyue/Shajing

Dengan route anchor antarkawasan yang sudah ada, graph regional tersebut terhubung ke satu jaringan dunia melalui Yunjing dan koridor Canon antarkawasan.

### Maintenance Boundary
- Penambahan ini tidak menetapkan populasi, NPC, toko, harga, event, quest, jadwal kapal, kondisi cuaca, atau akses Character.
- Tidak ada route baru yang boleh diasumsikan hanya karena dua lokasi tampak berdekatan di peta.
- Perubahan jarak baseline selanjutnya harus melalui Admin maintenance dan verifikasi graph agar tidak memutus konektivitas atau menciptakan konflik route.


## 20C — AERIAL TRAVEL / FLIGHT MAINTENANCE

### Status
**Admin Canon — Aerial Travel Framework Established**

Aerial Travel adalah metode perjalanan terpisah dari route darat/laut. Registry route permukaan tetap menjadi authority untuk perjalanan darat dan laut. Kemampuan terbang tidak otomatis mengubah route permukaan menjadi route udara.

### Aerial Travel Record Contract
Setiap rute atau koridor udara yang sudah memiliki baseline numerik harus dapat dipetakan ke:
- `AER_ID` — ID unik koridor/rute udara.
- `ORIGIN` — location node Canon atau posisi runtime yang valid.
- `DESTINATION` — location node Canon atau tujuan runtime yang valid.
- `AERIAL_DISTANCE_BASELINE` — jarak udara resmi dalam Li/Fen/Cun; jika belum ditetapkan gunakan `UNRESOLVED`.
- `FLIGHT_METHOD` — teknik, ability, item/artifact, mount, atau metode lain yang benar-benar dimiliki/tersedia.
- `FLIGHT_SPEED_SOURCE` — source yang memberikan kecepatan numerik; tanpa source numerik, kecepatan tetap `UNRESOLVED`.
- `FLIGHT_REQUIREMENT` — syarat aktivasi/metode.
- `AIRSPACE_CONDITION` — kondisi atau pembatasan udara yang memang memiliki source.
- `CHECKPOINT_RULE` — checkpoint sesuai Time/Action bila perjalanan melewati batas aksi.
- `ROUTE_STATUS` — `CANON-ESTABLISHED`, `UNRESOLVED`, atau `RESOLUTION-BLOCKED`.
- `SOURCE` — sumber Canon/Admin yang menetapkan record.

### Flight Eligibility
- **FLIGHT-ELIGIBLE** hanya jika Character benar-benar memiliki metode terbang yang tervalidasi.
- Realm tinggi **tidak otomatis** berarti dapat terbang.
- Teknik/ability yang menyebut dapat terbang belum otomatis memiliki kecepatan numerik.
- Jika teknik/ability/artifact memiliki kecepatan resmi, gunakan nilai tersebut.
- Jika kemampuan terbang ada tetapi speed source tidak ada, Character dapat dianggap memiliki kemampuan terbang untuk validasi eligibility, tetapi durasi numerik perjalanan menjadi `UNRESOLVED` dan resolusi yang membutuhkan durasi numerik menjadi `RESOLUTION-BLOCKED`.
- Flight method yang tidak tercatat pada Character State/Origin tidak boleh diasumsikan dimiliki.

### Aerial Distance
- Jarak route permukaan **tidak boleh dipakai sebagai jarak udara** kecuali source Canon/Admin secara eksplisit menyatakannya.
- Jarak udara tidak boleh dibuat dari perkiraan garis lurus, peta visual, atau angka dunia nyata.
- Jika belum ada baseline aerial distance yang sah untuk pasangan lokasi/koridor, field tetap `UNRESOLVED`.
- Admin dapat menetapkan aerial corridor/baseline baru melalui maintenance berikutnya tanpa mengubah route permukaan.

### Aerial Resolution
Untuk perjalanan udara:
`Waktu perjalanan = jarak udara / kecepatan terbang efektif + hambatan yang memiliki dasar sah.`

- Kecepatan efektif wajib berasal dari source flight method yang tervalidasi.
- Jangan membuat multiplier atau penalti persen untuk ketinggian, cuaca, angin, beban, atau cedera tanpa source Canon/Admin.
- Airspace restriction, barrier, faction control, encounter, weather, stamina, altitude, dan kondisi lain hanya diterapkan bila relevan dan bersumber dari sistem/Canon.
- Flight dapat mengabaikan medan permukaan yang tidak relevan dengan lintasan udara, tetapi tidak otomatis mengabaikan hambatan udara, barrier, wilayah terlarang, encounter, atau biaya resource.
- Teleportasi tetap merupakan metode berbeda dan hanya sah jika source Canon menyediakannya.

### Checkpoint & Persistence
- Perjalanan udara yang melewati 3 jam aksi mengikuti checkpoint Travel + Time System.
- Checkpoint minimal mencatat waktu, posisi/lokasi, jarak udara tersisa bila diketahui, kondisi, stamina/Qi bila relevan, dan kejadian perjalanan.
- Jika flight method memiliki maximum flight duration/range, nilai tersebut wajib berasal dari source method dan harus divalidasi sebelum perjalanan.
- Perubahan material pada lokasi, kondisi, resource, atau metode flight mengikuti Save Pipeline dan Origin/History bila diperlukan.

### Current Aerial Baseline Boundary
Tidak ada kecepatan terbang generik berbasis Realm dan tidak ada aerial distance generik yang diturunkan dari route permukaan. Sampai Admin menetapkan source numerik, kedua field tersebut tetap `UNRESOLVED`.

### Data Completeness Aerial Gate
Required input:
`FLIGHT_METHOD + FLIGHT_REQUIREMENT + AERIAL_DISTANCE_BASELINE + FLIGHT_SPEED_SOURCE`.

Jika eligibility belum tervalidasi → `RESOLUTION-BLOCKED`.
Jika eligibility tervalidasi tetapi distance/speed numerik belum tersedia → jangan mengarang durasi; gunakan `UNRESOLVED` untuk field yang hilang dan `RESOLUTION-BLOCKED` untuk resolusi yang memerlukan angka tersebut.


### 20C-1 — Canon Flight Source Registry

Bagian ini menetapkan source Canon numerik untuk kecepatan terbang. Record di bawah adalah sumber metode, bukan pemberian otomatis kepada Character.

| FLIGHT_SOURCE_ID | Canon Method | Minimum Realm | Flight Speed | Scope |
|---|---|---|---:|---|
| FLY-SRC-001 | Teknik Perjalanan Awan Dasar | Realm 2 — Qi Refining | 60 Li/jam | penerbangan stabil jarak dekat–menengah |
| FLY-SRC-002 | Teknik Perjalanan Awan Lanjutan | Realm 3 — Foundation Establishment | 120 Li/jam | penerbangan stabil jarak menengah |
| FLY-SRC-003 | Teknik Arus Langit | Realm 4 — Core Formation | 240 Li/jam | penerbangan cepat lintas wilayah |
| FLY-SRC-004 | Teknik Langit Roh | Realm 5 — Nascent Soul | 480 Li/jam | penerbangan jarak jauh |
| FLY-SRC-005 | Teknik Melintasi Kekosongan | Realm 6 — Soul Transformation | 800 Li/jam | penerbangan berkecepatan tinggi |
| FLY-SRC-006 | Teknik Jalan Bintang | Realm 7 — Void Severing | 1.200 Li/jam | lintasan udara ekstrem |
| FLY-SRC-007 | Teknik Menembus Langit | Realm 8 — Tribulation Crossing | 1.800 Li/jam | penerbangan ekstrem |
| FLY-SRC-008 | Teknik Kenaikan Abadi | Realm 9 — Immortal Ascension | 2.500 Li/jam | mobilitas udara tingkat Immortal |

#### Source Authority Rules
1. FLIGHT_SOURCE_ID adalah Admin Canon Source untuk speed ketika metode tersebut benar-benar diperoleh dan aktif pada Character.
2. Minimum Realm adalah requirement metode, bukan aturan bahwa seluruh Character pada Realm tersebut otomatis dapat terbang.
3. Character yang memenuhi requirement tetap membutuhkan Technique/Ability Origin yang membuktikan metode tersebut benar-benar diperoleh dan aktif.
4. Character tidak boleh memilih FLIGHT_SOURCE_ID hanya karena mencapai Realm minimum.
5. Jika Character memiliki metode flight lain dengan speed resmi yang berbeda, speed metode Character tersebut menjadi source yang digunakan.
6. Jika technique hanya membuktikan FLIGHT-ELIGIBLE tetapi tidak menunjuk ke speed source, speed tetap UNRESOLVED.
7. Artifact, mount, Spirit Beast, atau metode eksternal dapat memiliki speed source sendiri dan tidak otomatis memakai registry kultivasi ini.
8. Tidak ada stacking speed antar-technique. Satu metode flight aktif menjadi source movement speed untuk resolusi perjalanan, kecuali Canon method secara eksplisit mendefinisikan kombinasi.
9. Angka speed adalah baseline normal untuk metode tersebut. Cuaca, barrier, combat, stamina, resource cost, maximum range, dan kondisi lain tidak mendapat modifier numerik kecuali memiliki source resmi.
10. Kecepatan ini tidak mengubah jarak route permukaan dan tidak mengubah Character State secara otomatis.

#### Flight Method Resolution
- FLIGHT-ELIGIBLE + SPEED-DEFINED + AERIAL-DISTANCE-DEFINED → perjalanan udara dapat dihitung secara numerik.
- FLIGHT-ELIGIBLE + SPEED-DEFINED + AERIAL-DISTANCE-UNRESOLVED → durasi tetap UNRESOLVED.
- FLIGHT-ELIGIBLE + SPEED-UNRESOLVED → durasi tetap UNRESOLVED.
- Tidak ada FLIGHT-ELIGIBLE → flight action RESOLUTION-BLOCKED.
- Flight source tidak memberikan technique, item, artifact, mount, atau permission kepada Character.

#### Canon Provenance
- Source Type: Admin Canon
- Source Authority: systems/20_TRAVEL_ROUTES.md
- Acquisition: wajib berasal dari Technique/Ability/Item/Mount Origin yang sah.
- Runtime Status: hanya ACTIVE setelah source method tervalidasi pada Character.
- Version: AERIAL-SOURCE-BASELINE-001
