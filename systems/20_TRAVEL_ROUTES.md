# 20 — RUTE, JARAK & SATUAN PERJALANAN

## Status Canon
Modul ini menjadi registry rute utama dan baseline jarak dunia. **Satuan jarak resmi TianDao-World adalah Li (里).** Untuk jarak yang lebih kecil dari 1 Li, gunakan **Fen (分)** dan, bila presisi sangat kecil diperlukan, **Cun (寸)**. Jarak adalah jarak rute, bukan garis lurus. Waktu aktual tetap dihitung dari sarana, medan, cuaca, beban, stamina, suplai, kondisi karakter, dan hambatan.

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
Kota Tianjing, Kota Baiyu dan Desa Minghe tercatat sebagai pusat dunia, tetapi jarak antarlokasi belum diberi baseline rute dalam modul Canon saat registry ini dibuat. GM wajib memperlakukan jaraknya sebagai **belum ditentukan**, bukan mengarang angka.

## Rute Antarkawasan
Hubungan antarkawasan diakui oleh World Map, tetapi baseline jarak dan koridor lengkap belum ditetapkan dalam registry ini. Sampai Admin menetapkannya, GM tidak boleh membuat angka jarak atau shortcut antarkawasan.

## Perhitungan Waktu
`Waktu perjalanan = jarak rute / kecepatan efektif + hambatan.`
Kecepatan efektif harus berasal dari sarana/metode yang sah. Hambatan meliputi medan, cuaca, orientasi, beban, kondisi tubuh, suplai, pemeriksaan, encounter dan event.

## Checkpoint
Setiap perjalanan yang melewati 3 jam aksi harus memiliki checkpoint state: waktu, lokasi, jarak tersisa, kondisi, stamina, suplai, cuaca dan kejadian. Tidak boleh ada time skip tersembunyi.

## Integrasi
Registry ini menjadi sumber rute dan konvensi jarak untuk World Map, Time, Action, Vitality, Economy, Monsters, Factions dan Events.
