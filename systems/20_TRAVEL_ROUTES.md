# 20 — RUTE & JARAK PERJALANAN

## Status Canon
Modul ini menjadi registry rute utama dan baseline jarak dunia. Jarak adalah jarak rute, bukan garis lurus. Waktu aktual tetap dihitung dari sarana, medan, cuaca, beban, stamina, suplai, kondisi karakter, dan hambatan.

## Aturan Dasar
- Semua perjalanan menghabiskan waktu nyata dalam state dunia.
- Aksi non-kultivasi tetap maksimal 3 jam per turn; perjalanan panjang harus dipecah menjadi beberapa turn/checkpoint bila berlangsung melewati batas tersebut.
- Angka jarak tidak otomatis berarti durasi tetap.
- Jalan kaki, tunggangan, karavan, kapal, dan metode kultivasi memiliki kecepatan berbeda sesuai data sistem/metode yang sah.
- Cuaca buruk, encounter, cedera, kehilangan arah, pemeriksaan, dan kerusakan sarana dapat memperpanjang perjalanan.
- Teleportasi/transportasi khusus hanya sah jika sumber Canon menyediakannya.

## Kategori Jarak
- **Sangat dekat:** <10 km
- **Dekat:** 10–30 km
- **Sedang:** >30–80 km
- **Jauh:** >80–200 km
- **Sangat jauh:** >200–500 km
- **Antarkawasan:** >500 km atau lintasan laut/medan ekstrem; wajib memakai rute dan sarana yang sah.

## Rute Regional — Dataran Cangyuan
| Rute | Jarak baseline | Medan |
|---|---:|---|
| Kota Yunjing ↔ Kota Luoxing | 72 km | jalan dagang |
| Kota Luoxing ↔ Desa Baihe | 38 km | jalur pertanian/sungai |
| Kota Luoxing ↔ Kota Heiyu | 126 km | jalur dagang/perbatasan |
| Desa Baihe ↔ Lembah Qinghe | 54 km | jalan pedalaman |

## Rute Regional — Pegunungan Qingluan
| Rute | Jarak baseline | Medan |
|---|---:|---|
| Kota Lingshan ↔ Desa Yunmu | 24 km | kaki gunung/jalur pemburu |
| Kota Lingshan ↔ Lembah Qingsong | 46 km | jalur spiritual |
| Lembah Qingsong ↔ Puncak Tianque | 31 km | pendakian sulit |
| Desa Yunmu ↔ Hutan Wuyin | 19 km | hutan/kabut |

## Rute Regional — Domain Yaohuang Selatan
| Rute | Jarak baseline | Medan |
|---|---:|---|
| Kota Nanyao ↔ Pelabuhan Chixia | 61 km | jalur perdagangan |
| Kota Nanyao ↔ Hutan Cangmang | 18 km | pintu hutan |
| Hutan Cangmang ↔ Lembah Seratus Bunga | 47 km | pedalaman/berisiko |
| Kota Nanyao ↔ Pegunungan Huoyan | 83 km | jalur pegunungan |

## Rute Regional — Laut Dongming
| Rute | Jarak baseline | Medan |
|---|---:|---|
| Kota Haicheng ↔ Pulau Yuehai | 96 km | laut utama |
| Pulau Yuehai ↔ Kepulauan Lanyue | 138 km | laut antarpulau |
| Kota Haicheng ↔ Pulau Qionghua | 164 km | jalur dagang spiritual |
| Kepulauan Lanyue ↔ Jurang Laut Canglong | 218 km | laut dalam/ekspedisi |

## Rute Regional — Tanah Salju Beiming
| Rute | Jarak baseline | Medan |
|---|---:|---|
| Kota Beixue ↔ Benteng Hanjiang | 77 km | jalur benteng |
| Benteng Hanjiang ↔ Desa Xuehe | 43 km | jalur permukiman |
| Desa Xuehe ↔ Lembah Bingxin | 69 km | ekspedisi es |
| Kota Beixue ↔ Reruntuhan Tianhan | 154 km | ekspedisi utara |

## Rute Regional — Gurun Jinyan
| Rute | Jarak baseline | Medan |
|---|---:|---|
| Kota Shajing ↔ Kota Jinyue | 91 km | jalur kafilah |
| Kota Shajing ↔ Oasis Qingyu | 57 km | gurun/persinggahan |
| Kota Jinyue ↔ Laut Pasir Wuheng | 42 km | ekspedisi gurun |
| Laut Pasir Wuheng ↔ Makam Tianri | 118 km | gurun/ekspedisi |

## Rute — Jantung Tianyuan
Kota Tianjing, Kota Baiyu dan Desa Minghe tercatat sebagai pusat dunia, tetapi jarak antarlokasi belum diberi baseline rute dalam modul Canon saat registry ini dibuat. GM wajib memperlakukan jaraknya sebagai **belum ditentukan**, bukan mengarang angka.

## Rute Antarkawasan
Hubungan antarkawasan diakui oleh World Map, tetapi baseline kilometer dan koridor lengkap belum ditetapkan dalam registry ini. Sampai Admin menetapkannya, GM tidak boleh membuat angka jarak atau shortcut antarkawasan.

## Perhitungan Waktu
`Waktu perjalanan = jarak rute / kecepatan efektif + hambatan.`
Kecepatan efektif harus berasal dari sarana/metode yang sah. Hambatan meliputi medan, cuaca, orientasi, beban, kondisi tubuh, suplai, pemeriksaan, encounter dan event.

## Checkpoint
Setiap perjalanan yang melewati 3 jam aksi harus memiliki checkpoint state: waktu, lokasi, jarak tersisa, kondisi, stamina, suplai, cuaca dan kejadian. Tidak boleh ada time skip tersembunyi.

## Integrasi
Registry ini menjadi sumber rute untuk World Map, Time, Action, Vitality, Economy, Monsters, Factions dan Events.