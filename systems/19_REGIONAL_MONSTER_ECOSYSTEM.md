# 19 — REGIONAL MONSTER ECOSYSTEM

## Status Canon
Modul ini menetapkan **kerangka ekosistem dan tekanan encounter**, bukan katalog monster.

Nama spesies, varian, Tier, kemampuan, dan loot konkret dapat dihasilkan dinamis oleh GM melalui `systems/25_DYNAMIC_GENERATION.md`, selama tidak bertentangan dengan World Bible/Custom Canon dan melewati validation.

Fixed creature data tetap dapat berlaku bila secara eksplisit tersedia. Fixed data tidak membatasi kemungkinan species lain di dunia.

## Aturan Ekosistem
- Habitat menentukan kelompok/archetype encounter yang masuk akal; habitat tidak menjamin encounter terjadi.
- Encounter dipengaruhi waktu, cuaca, musim, kepadatan manusia, aktivitas pemain, event, dan perilaku makhluk.
- GM boleh menghasilkan species, subspesies, varian, atau Spirit Beast baru secara runtime bila hasilnya ekologis dan mekanis valid.
- Tier ditentukan melalui Dynamic Threat Resolution, bukan otomatis dari nama habitat atau Realm Character.
- Monster tidak otomatis agresif; perilaku mengikuti generated traits, habitat, kondisi, dan context.
- Loot mengikuti Dynamic Loot Formula atau fixed table yang memang berlaku.

## Dataran Cangyuan
| Zona | Ekosistem | Tekanan encounter |
|---|---|---|
| Sungai & tepian hutan | satwa liar, makhluk air, spirit beast rendah | rendah–sedang |
| Jalan dagang | monster tingkat rendah dan satwa liar yang tertarik pada aktivitas/sisa makanan | rendah–sedang |
| Pedalaman | fauna liar dan spirit beast dengan kontak manusia lebih sedikit | sedang |
| Area pertanian | satwa liar dan gangguan makhluk lokal | rendah |

## Pegunungan Qingluan
| Zona | Ekosistem | Tekanan encounter |
|---|---|---|
| Kaki gunung | satwa liar, spirit beast rendah | rendah–sedang |
| Hutan purba/Wuyin | spirit beast, makhluk hutan, flora berbahaya | sedang–tinggi |
| Jalur spiritual | makhluk yang tertarik energi spiritual dan fenomena qi | sedang–tinggi |
| Puncak Tianque | fauna/spirit beast pegunungan dan tekanan lingkungan | tinggi |

## Domain Yaohuang Selatan
| Zona | Ekosistem | Tekanan encounter |
|---|---|---|
| Hutan Cangmang | fauna tropis, spirit beast, makhluk hutan | sedang–tinggi |
| Rawa | makhluk air, fauna rawa, bahaya lingkungan | sedang–tinggi |
| Lembah Seratus Bunga | fauna lokal dan bahaya flora khusus | sedang |
| Pegunungan Huoyan | fauna tahan panas dan makhluk terkait lingkungan panas bila tercatat | sedang–tinggi |

## Laut Dongming
| Zona | Ekosistem | Tekanan encounter |
|---|---|---|
| Pesisir/pelabuhan | makhluk laut tingkat rendah dan satwa pesisir | rendah |
| Laut terbuka | makhluk laut sesuai database dan event | sedang–tinggi |
| Kepulauan Lanyue | fauna pulau dan makhluk laut | sedang |
| Jurang Laut Canglong | ekosistem laut dalam; detail konkret dihasilkan oleh context/runtime | tidak ditentukan |

## Tanah Salju Beiming
| Zona | Ekosistem | Tekanan encounter |
|---|---|---|
| Sekitar permukiman | satwa liar dan monster rendah | rendah |
| Padang salju | monster/spirit beast yang sesuai habitat dingin | sedang |
| Lembah Bingxin | fauna dingin dan ancaman lingkungan | tinggi |
| Reruntuhan Tianhan | encounter berdasarkan lore/event/context dan dynamic generation | tidak ditentukan |

## Gurun Jinyan
| Zona | Ekosistem | Tekanan encounter |
|---|---|---|
| Oasis | fauna oasis dan makhluk gurun lokal | rendah–sedang |
| Jalur kafilah | makhluk gurun yang beradaptasi terhadap aktivitas manusia | rendah–sedang |
| Laut Pasir Wuheng | fauna/monster gurun melalui dynamic generation dan context | sedang–tinggi |
| Makam Tianri | encounter berdasarkan lore/event/context dan dynamic generation | tidak ditentukan |

## Jantung Tianyuan
| Zona | Ekosistem | Tekanan encounter |
|---|---|---|
| Kota Tianjing | satwa kota dan ancaman non-monster lebih dominan | sangat rendah |
| Kota Baiyu | satwa kota dan lingkungan urban | sangat rendah |
| Desa Minghe | satwa liar lokal dan spirit beast rendah di luar permukiman | rendah |

## Skala Tekanan
Label ini adalah input ekologis untuk Dynamic Generation Engine:

- **Sangat rendah:** encounter liar jarang dan habitat sangat terkontrol → Base Pressure 5.
- **Rendah:** encounter mungkin tetapi bukan ancaman dominan → Base Pressure 20.
- **Sedang:** encounter rutin mungkin terjadi dalam kondisi tertentu → Base Pressure 40.
- **Tinggi:** ekspedisi harus memperhitungkan encounter sebagai risiko utama → Base Pressure 65.
- **Tidak ditentukan:** belum ada dasar untuk menetapkan base pressure; gunakan `???`, bukan asumsi angka.

Threat Score dan Tier Ceiling dihitung terpisah menurut `systems/25_DYNAMIC_GENERATION.md`.

## Dynamic World Rule
Tabel wilayah di atas menjelaskan **ecological pressure dan kemungkinan archetype**, bukan daftar species yang diizinkan.

Contoh: sungai tidak terbatas pada satu species; hutan tidak terbatas pada daftar monster tertentu; Spirit Beast tidak terbatas pada species yang pernah muncul sebelumnya.

Generated creature tetap harus memiliki hubungan ekologis yang masuk akal dengan region/habitat dan tidak boleh melanggar Canon.

## Integrasi
Monster ecosystem terhubung dengan World Map, Travel Routes, Time, Vitality, Combat, Loot, Economy, Karma, Reputation, Events, Spirit Beast System, dan `systems/25_DYNAMIC_GENERATION.md`.
