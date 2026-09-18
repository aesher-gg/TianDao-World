# 21 — REGIONAL ECONOMY

## Status Canon
Modul ini memetakan arus komoditas dan karakter pasar tiap kawasan. Ini bukan daftar harga tetap. Harga transaksi tetap mengikuti `systems/10_ECONOMY.md`, kualitas barang, legalitas, musim, suplai, permintaan, lokasi dan event.

## Prinsip
- Tidak ada currency baru di luar Economy.
- Komoditas lokal tidak berarti otomatis murah atau mudah diperoleh.
- Barang langka membutuhkan sumber/vendor/loot/event yang sah.
- Perubahan harga besar harus memiliki dasar suplai, permintaan, event, atau keputusan Admin.
- Pajak, bea, biaya pelabuhan, biaya karavan, penginapan dan jasa lain hanya digunakan jika ada dasar lokasi/faction atau angka ekonomi resmi.

## Dataran Cangyuan
**Basis pasar:** populasi dan perdagangan darat tinggi.
- Ekspor: beras, sayuran, serat, kayu, logam biasa, alat pertanian, perlengkapan perjalanan.
- Arus kultivator: herbal, jimat dan material monster tingkat rendah bila tersedia.
- Titik ekonomi: Yunjing sebagai simpul administrasi/perdagangan; Luoxing sebagai pasar terbuka; Baihe sebagai sumber pangan; Heiyu sebagai gerbang perbatasan.
- Risiko ekonomi: gangguan bandit, pemeriksaan perbatasan dan konflik kontrak.

## Pegunungan Qingluan
**Basis pasar:** bahan spiritual dan hasil hutan.
- Ekspor: herbal, jamur, madu, kayu, kulit, material spirit beast.
- Impor: pangan, alat, kain, perlengkapan pendakian dan barang kota.
- Titik ekonomi: Lingshan sebagai pasar kaki gunung; Yunmu sebagai pemasok hasil hutan.
- Risiko ekonomi: cuaca, jalur sulit, kualitas material dan biaya pengangkutan.

## Domain Yaohuang Selatan
**Basis pasar:** perdagangan lintas manusia-yao dan komoditas alam tropis.
- Ekspor: rempah, herbal, obat, kulit, sisik, bahan monster, hasil laut dari Chixia.
- Impor: logam, kain, barang manufaktur dan suplai perjalanan.
- Titik ekonomi: Nanyao dan Pelabuhan Chixia.
- Risiko ekonomi: penyakit, legalitas barang, jalur liar, konflik faction dan penyelundupan.

## Laut Dongming
**Basis pasar:** ekonomi maritim.
- Ekspor: ikan, garam, mutiara, hasil laut, herbal pesisir, kayu kapal, material makhluk laut.
- Impor: pangan darat, logam, kain, alat kapal dan barang antarwilayah.
- Titik ekonomi: Haicheng dan Pulau Yuehai.
- Risiko ekonomi: badai, kehilangan kapal, arus, keamanan laut dan keterbatasan suplai.

## Tanah Salju Beiming
**Basis pasar:** survival dan logistik dingin.
- Ekspor: hasil buruan, kulit, bulu, mineral, herbal dingin.
- Impor: pangan, pakaian musim dingin, obat, bahan bakar dan perlengkapan perjalanan.
- Titik ekonomi: Beixue dan Benteng Hanjiang.
- Risiko ekonomi: musim dingin, jarak, kelangkaan pangan, badai salju dan kerusakan transportasi.

## Gurun Jinyan
**Basis pasar:** oasis dan perdagangan kafilah.
- Ekspor: garam, mineral, herbal gurun, kaca pasir dan barang kafilah.
- Impor: air, pangan, kain, obat, perlengkapan perjalanan dan barang manufaktur.
- Titik ekonomi: Shajing dan Jinyue.
- Risiko ekonomi: dehidrasi, badai pasir, kehilangan arah, suplai air dan keamanan kafilah.

## Jantung Tianyuan
**Basis pasar:** administrasi, kerajinan, arsip dan konsumsi pusat.
- Ekspor: barang manufaktur, produk pengrajin, dokumen/layanan administratif sesuai akses sah.
- Impor: pangan dan komoditas dari berbagai kawasan.
- Titik ekonomi: Tianjing dan Baiyu; Minghe memasok produk agrikultur.
- Risiko ekonomi: pajak, pemeriksaan, regulasi dan akses administratif.

## Perdagangan Antarkawasan
Arus perdagangan antarkawasan membutuhkan rute, sarana, kontrak, suplai dan waktu yang sah. Jarak dan hambatan mengikuti `systems/20_TRAVEL_ROUTES.md`. GM tidak boleh menganggap semua komoditas tersedia di semua kota.

## Integrasi
Regional Economy terhubung dengan Items, Loot, Organizations, Factions, Travel, Time, Reputation, Karma dan Events.
## 8. Regional Commodity Chains — Item Canon Integration

Komoditas baru sekarang memiliki rantai ekonomi yang eksplisit. Ini bukan price list; harga tetap ditentukan oleh Module 10 dan kondisi pasar.

| Region | Source | Commodity Flow | Downstream Demand | Economic Role |
|---|---|---|---|---|
| Dataran Cangyuan | SRC-RES-CGY-001 | Serat Sungai Cangyuan → Tali Serat Cangyuan | perjalanan, workshop, pertanian, crafting | substitusi lokal material tali; memperkuat perdagangan sungai/darat |
| Pegunungan Qingluan | SRC-RES-QGL-001 | Getah Pinus Roh Qingluan → Bubuk Pengawet Qingluan | workshop kayu/material, alchemy | komoditas hutan bernilai proses |
| Pegunungan Qingluan | SRC-RES-QGL-002 | Jamur Kabut Wuyin → Bubuk Jamur Wuyin | alchemist/herbalist | meningkatkan nilai ekspedisi dan perdagangan herbal |
| Domain Yaohuang Selatan | SRC-RES-YHS-001 | Terak Besi Api Huoyan + Bijih Besi → Bilah Besi Huoyan | smith/weapon market | menghubungkan resource panas bumi dengan manufaktur |
| Domain Yaohuang Selatan | SRC-RES-YHS-002 | Madu Seratus Bunga → Sirup Madu Seratus Bunga | alchemist, apothecary, konsumsi | komoditas biologis bernilai proses |
| Laut Dongming | SRC-RES-DGM-001 | Mutiara Pasang Dongming → Manik Mutiara Dongming | pengrajin aksesori, perdagangan | komoditas laut bernilai tinggi tanpa fixed price |
| Laut Dongming | SRC-RES-DGM-002 | Cangkang Karang Lanyue → Lempeng Cangkang Lanyue | artisan/crafting | bahan kerajinan laut dengan jalur produksi |
| Tanah Salju Beiming | SRC-RES-BMG-001 | Kulit Dingin Beiming + Serat Cangyuan → Mantel Kulit Dingin | survival/travel/workshop | menghubungkan resource dingin dengan manufaktur pakaian |
| Jantung Tianyuan | SRC-RES-TYN-001 | Pecahan Giok Baiyu → Blank Giok Ukir | artisan/formation-compatible workshops | memberi nilai pada limbah produksi dan kerajinan giok |
| Gurun Jinyan | SRC-RES-GJY-001 | Kristal Garam Jinyan | preservation/trade/logistics | komoditas oasis dan kebutuhan pengawetan |

### 8.1 Economy Boundaries
- Canon chain tidak menetapkan harga tetap.
- Availability, quantity, quality, legal access, transport cost, tax, scarcity dan demand tetap dinamis/source-dependent.
- Barang regional tidak otomatis muncul di kota lain; perdagangan memerlukan rute, sarana, waktu, suplai dan kepemilikan yang sah.
- Resource source dan processing recipe tidak memberi akses Character secara otomatis.
- Jika source atau market state belum diketahui, nilai transaksi tetap mengikuti status data resmi; Qwen tidak boleh mengarang harga.
