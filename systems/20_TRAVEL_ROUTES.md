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
- Jangan mengubah jarak yang belum diketahui menjadi angka. Gunakan `???` sampai ada sumber yang sah.

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
- Metode kultivasi/gerakan khusus **tidak memiliki baseline generik**. Jika tidak ada nilai kecepatan resmi, kecepatan tetap `???` dan durasi tidak boleh dihitung dengan angka tebakan.
- Jika jenis sarana tidak diketahui, jangan mengasumsikan jalan kaki; gunakan `???` sampai sarana ditentukan.
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
Kota Tianjing, Kota Baiyu dan Desa Minghe tercatat sebagai pusat dunia, tetapi jarak antarlokasi belum diberi baseline rute dalam modul Canon. GM wajib memperlakukan jaraknya sebagai **belum ditentukan**, bukan mengarang angka.

## Rute Antarkawasan
Hubungan antarkawasan diakui oleh World Map, tetapi baseline jarak dan koridor lengkap belum ditetapkan dalam registry ini. Sampai Admin menetapkannya, GM tidak boleh membuat angka jarak atau shortcut antarkawasan.

## Perhitungan Waktu
`Waktu perjalanan = jarak rute / kecepatan efektif + hambatan.`

Kecepatan efektif harus berasal dari baseline resmi di atas atau sumber sarana/metode yang sah. Hambatan hanya boleh diberi nilai numerik bila sumber Canon/Admin menetapkan nilainya. Hambatan yang belum memiliki nilai numerik tidak boleh diubah menjadi angka oleh GM; resolusi harus tetap kualitatif atau menggunakan `???` sampai ada data sah.

## Checkpoint
Setiap perjalanan yang melewati 3 jam aksi harus memiliki checkpoint state: waktu, lokasi, jarak tersisa, kondisi, stamina, suplai, cuaca dan kejadian. Tidak boleh ada time skip tersembunyi.

## Integrasi
Registry ini menjadi sumber rute dan konvensi jarak untuk World Map, Time, Action, Vitality, Economy, Monsters, Factions dan Events.
