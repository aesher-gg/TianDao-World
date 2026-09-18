# 00 — FIXED BESTIARY DATABASE

## Status
Admin Canon v1.4 — Fixed Bestiary Concepts, Habitats, Provenance & World Impact

## Purpose
Registry untuk makhluk yang sengaja ditetapkan Admin sebagai fixed Canon. Database ini melengkapi, bukan menggantikan, Dynamic Monster/Spirit Beast Generation pada `systems/25_DYNAMIC_GENERATION.md`.

## Boundary
- Creature yang tercatat di file ini adalah fixed Bestiary Canon.
- Tidak tercatat bukan berarti tidak dapat ada.
- Species/archetype lain tetap dapat dihasilkan melalui Dynamic Generation jika validation gate terpenuhi.
- Fixed entry diprioritaskan ketika encounter/source secara eksplisit tercakup.
- Dynamic Generation digunakan ketika tidak ada fixed entry yang berlaku.
- Tier dan Realm tetap atribut terpisah.
- Fixed Bestiary tidak memberikan automatic encounter, taming, ownership, ability, loot, atau reward.
- Loot Profile mendefinisikan kemungkinan sumber loot, bukan guaranteed drop.
- Daging adalah possible biological loot bagi creature yang secara anatomi menghasilkan daging.
- Spirit Beast tidak memiliki Core/inti secara default.

## Habitat Boundary
Habitat pada entry berikut adalah **habitat utama Canon**, bukan jaminan encounter dan bukan pembatas seluruh spesies yang dapat muncul di wilayah tersebut.

Pemetaan habitat mengikuti `systems/19_REGIONAL_MONSTER_ECOSYSTEM.md`:
- Dataran Cangyuan: sungai/tepian hutan, pedalaman, area pertanian, jalan dagang.
- Pegunungan Qingluan: kaki gunung, hutan purba/Wuyin, jalur spiritual, puncak Tianque.
- Domain Yaohuang Selatan: Hutan Cangmang, rawa, Lembah Seratus Bunga, Pegunungan Huoyan.
- Laut Dongming: pesisir/pelabuhan, laut terbuka, Kepulauan Lanyue.
- Tanah Salju Beiming: sekitar permukiman, padang salju, Lembah Bingxin.
- Gurun Jinyan: oasis, jalur kafilah, Laut Pasir Wuheng.

## Fixed Entry Schema
Setiap entry fixed Canon memuat bila relevan:
- `CREATURE_ID` unik/stabil.
- Nama/species.
- Region dan habitat utama.
- Tier/Threat boundary.
- Perilaku/ecology.
- Kemampuan Canon dan batas penggunaannya.
- Kelemahan bila Canon.
- Spirit Beast capability bila ditetapkan.
- Loot Profile.
- Origin/Canon source.
- Persistence rule bila creature recurring/material.

## Loot Profile Rules
- **Daging:** possible biological material jika anatomi mendukung.
- **Material Biologis:** bagian tubuh yang secara logis tersedia.
- **Special Material:** material khas spesies yang mungkin tersedia bila kondisi dan metode akuisisi valid.
- **Habitat Resource:** resource yang hanya dapat diperoleh jika benar-benar ada dan dapat diakuisisi.
- **Acquisition:** metode perolehan yang valid.
- **Condition:** kerusakan tubuh dapat mengurangi atau menghancurkan hasil panen.
- **Core:** tidak ada secara default pada 25 entry ini.

Actual loot tetap mengikuti `systems/18_LOOT.md` dan `systems/25_DYNAMIC_GENERATION.md`.

## Fixed Entries — Spirit Beast

### SB-001 — Naga Sungai Kecil
- Tier: 2
- Region/Habitat: Dataran Cangyuan — Sungai & tepian hutan.
- Konsep: Naga kecil cerdas, menyukai benda berkilau, pandai berenang dan dapat meluncur di udara jarak pendek.
- Daging: Daging Naga Sungai.
- Material Biologis: Sisik Naga Sungai, Tanduk Muda.
- Special Material: Air Mata Naga Sungai.
- Habitat Resource: Benda berkilau yang benar-benar dikumpulkan creature.
- Acquisition: Harvest; Special Material membutuhkan kondisi akuisisi khusus.
- Condition: Sisik/tanduk dapat rusak atau patah.
- Core: Tidak ada.

### SB-002 — Rubah Ekor Embun
- Tier: 2
- Region/Habitat: Dataran Cangyuan — Sungai & tepian hutan; pedalaman lembap.
- Konsep: Rubah spiritual berafinitas air, sangat waspada dan sulit didekati.
- Daging: Daging Rubah Ekor Embun.
- Material Biologis: Bulu, Kulit, Cakar.
- Special Material: Kelenjar Embun.
- Habitat Resource: Tumbuhan air/embun hanya jika benar-benar tersedia.
- Acquisition: Harvest.
- Condition: Bulu dan kelenjar dapat rusak.
- Core: Tidak ada.

### SB-003 — Kura-kura Batu Giok
- Tier: 2
- Region/Habitat: Pegunungan Qingluan — Kaki gunung dan jalur berbatu; Puncak Tianque untuk habitat yang lebih ekstrem bila valid.
- Konsep: Makhluk tenang dengan cangkang sangat keras, cocok menjadi penjaga alami wilayah kecil.
- Daging: Daging Kura-kura Batu Giok.
- Material Biologis: Cangkang, Sisik, Cakar.
- Special Material: Fragmen Cangkang Giok.
- Habitat Resource: Mineral/batu hanya jika tersedia secara nyata.
- Acquisition: Harvest.
- Condition: Cangkang dapat retak atau hancur.
- Core: Tidak ada.

### SB-004 — Bangau Awan Putih
- Tier: 2
- Region/Habitat: Dataran Cangyuan — Sungai & tepian hutan; lembah/perairan tenang yang sesuai.
- Konsep: Burung spiritual dengan penglihatan tajam dan kemampuan terbang yang baik.
- Daging: Daging Bangau.
- Material Biologis: Bulu, Paruh, Cakar.
- Special Material: Bulu Awan Putih.
- Habitat Resource: Tidak ada default.
- Acquisition: Harvest.
- Condition: Bulu/sayap dapat rusak.
- Core: Tidak ada.

### SB-005 — Rusa Tanduk Bulan
- Tier: 2
- Region/Habitat: Pegunungan Qingluan — Hutan purba/Wuyin dan jalur spiritual.
- Konsep: Herbivora pemalu dengan tanduk yang menyimpan energi spiritual ringan.
- Daging: Daging Rusa.
- Material Biologis: Kulit, Bulu, Tanduk.
- Special Material: Serpihan Tanduk Bulan.
- Habitat Resource: Tumbuhan spiritual hanya jika memang ditemukan.
- Acquisition: Harvest; shedding hanya jika mekanisme ditetapkan/terbukti.
- Condition: Tanduk dapat retak/patah.
- Core: Tidak ada.

### SB-006 — Monyet Batu Cangyuan
- Tier: 1
- Region/Habitat: Dataran Cangyuan — Pedalaman berbukit; dapat berada di kaki gunung Qingluan bila context mendukung.
- Konsep: Cerdas dan lincah, menggunakan batu serta kayu sebagai alat sederhana.
- Daging: Daging Monyet.
- Material Biologis: Bulu, Cakar, Taring.
- Special Material: Batu Simpanan Roh hanya jika creature benar-benar membawa material tersebut.
- Habitat Resource: Batu/mineral lingkungan.
- Acquisition: Harvest / Collection.
- Condition: Material fisik dapat rusak.
- Core: Tidak ada.

### SB-007 — Kucing Roh Senja
- Tier: 2
- Region/Habitat: Dataran Cangyuan — Pedalaman dan tepian permukiman/area pertanian.
- Konsep: Predator kecil aktif menjelang malam dengan pendengaran sangat baik.
- Daging: Daging Kucing Roh.
- Material Biologis: Bulu, Kulit, Cakar, Taring.
- Special Material: Kumis Roh Senja.
- Habitat Resource: Tidak ada default.
- Acquisition: Harvest.
- Condition: Kumis/bulu mudah rusak.
- Core: Tidak ada.

### SB-008 — Ikan Pedang Biru
- Tier: 2
- Region/Habitat: Dataran Cangyuan — Sungai & tepian hutan, terutama sungai besar; habitat perairan sesuai.
- Konsep: Predator air cepat dan teritorial.
- Daging: Daging Ikan Pedang.
- Material Biologis: Sisik, Sirip, Gigi/Moncong Pedang.
- Special Material: Sisik Biru Spiritual.
- Habitat Resource: Tidak ada default.
- Acquisition: Harvest.
- Condition: Sisik/sirip dapat rusak.
- Core: Tidak ada.

### SB-009 — Kelinci Salju Xuanyin
- Tier: 1
- Region/Habitat: Tanah Salju Beiming — Padang salju dan area di luar permukiman.
- Konsep: Herbivora kecil yang beradaptasi terhadap dingin ekstrem.
- Daging: Daging Kelinci Salju.
- Material Biologis: Bulu, Kulit, Cakar.
- Special Material: Bulu Salju Xuanyin.
- Habitat Resource: Tumbuhan tahan dingin hanya jika tersedia.
- Acquisition: Harvest.
- Condition: Bulu dapat kotor, rusak, atau terbakar.
- Canon Item Mapping: `ITEM-MAT-010` Kulit Dingin Beiming — hanya untuk kulit/fur yang memenuhi source condition item; tidak mengubah Special Material `Bulu Salju Xuanyin` menjadi item Canon.
- Core: Tidak ada.

### SB-010 — Serigala Kabut Kelabu
- Tier: 2
- Region/Habitat: Pegunungan Qingluan — Hutan purba/Wuyin dan lembah berkabut.
- Konsep: Predator kawanan dengan koordinasi lebih baik daripada serigala biasa.
- Daging: Daging Serigala.
- Material Biologis: Kulit, Bulu, Taring, Cakar.
- Special Material: Bulu Kabut Kelabu.
- Habitat Resource: Tidak ada default.
- Acquisition: Harvest.
- Condition: Kulit/bulu/taring dapat rusak.
- Core: Tidak ada.

### SB-011 — Ular Daun Zamrud
- Tier: 1
- Region/Habitat: Domain Yaohuang Selatan — Hutan Cangmang dan tepian rawa.
- Konsep: Ular kecil berbisa ringan dengan kamuflase alami.
- Daging: Daging Ular.
- Material Biologis: Kulit/Sisik, Taring.
- Special Material: Racun Zamrud.
- Habitat Resource: Tidak ada default.
- Acquisition: Harvest.
- Condition: Kelenjar racun harus tetap utuh untuk memperoleh racun.
- Core: Tidak ada.

### SB-012 — Kambing Tebing Roh
- Tier: 1
- Region/Habitat: Pegunungan Qingluan — Kaki gunung dan jalur/puncak berbatu.
- Konsep: Pemanjat tebing luar biasa kuat dan dapat menjadi jinak terhadap individu yang dipercaya.
- Daging: Daging Kambing.
- Material Biologis: Kulit, Bulu, Tanduk, Kuku.
- Special Material: Tanduk Tebing Roh.
- Habitat Resource: Tidak ada default.
- Acquisition: Harvest.
- Condition: Tanduk/kuku dapat patah.
- Core: Tidak ada.

### SB-013 — Burung Api Bara
- Tier: 2
- Region/Habitat: Domain Yaohuang Selatan — Pegunungan Huoyan.
- Konsep: Burung spiritual kecil tahan panas; bukan Phoenix dan tidak memiliki api tingkat tinggi.
- Daging: Daging Burung.
- Material Biologis: Bulu, Cakar, Paruh.
- Special Material: Bulu Bara.
- Habitat Resource: Batu/mineral panas hanya jika benar-benar tersedia.
- Acquisition: Harvest.
- Condition: Bulu dapat terbakar atau rusak.
- Core: Tidak ada.

### SB-014 — Kepiting Giok Laut
- Tier: 2
- Region/Habitat: Laut Dongming — Pesisir/pelabuhan dan perairan dangkal Kepulauan Lanyue.
- Konsep: Krustasea spiritual dengan capit kuat dan cangkang keras.
- Daging: Daging Kepiting.
- Material Biologis: Cangkang, Capit.
- Special Material: Fragmen Cangkang Giok Laut.
- Habitat Resource: Tidak ada default.
- Acquisition: Harvest.
- Condition: Cangkang/capit dapat retak atau hancur.
- Canon Item Mapping: `ITEM-MAT-014` Cangkang Karang Lanyue — hanya untuk cangkang yang memenuhi source condition Kepulauan Lanyue; tidak mengubah `Fragmen Cangkang Giok Laut` menjadi item Canon.
- Core: Tidak ada.

### SB-015 — Kuda Angin Padang
- Tier: 2
- Region/Habitat: Dataran Cangyuan — Pedalaman dan area pertanian/padang terbuka.
- Konsep: Herbivora spiritual dengan kecepatan dan stamina perjalanan tinggi.
- Daging: Daging Kuda.
- Material Biologis: Kulit, Rambut, Kuku, Tulang.
- Special Material: Rambut Angin.
- Habitat Resource: Tumbuhan padang hanya jika tersedia.
- Acquisition: Harvest.
- Condition: Rambut/kulit dapat rusak, kuku dapat patah.
- Core: Tidak ada.

## Fixed Entries — Beast Liar

### BST-001 — Serigala Abu-abu Cangyuan
- Tier: 1
- Region/Habitat: Dataran Cangyuan — Pedalaman, perbukitan, dan tepian hutan.
- Konsep: Predator kawanan yang mengandalkan pengejaran dan koordinasi.
- Daging: Daging Serigala.
- Material Biologis: Kulit, Bulu, Taring, Cakar.
- Special Material: Tidak ada default.
- Habitat Resource: Tidak ada default.
- Acquisition: Harvest.
- Condition: Bagian tubuh dapat rusak.
- Core: Tidak ada.

### BST-002 — Beruang Cokelat Hutan
- Tier: 1
- Region/Habitat: Dataran Cangyuan — Pedalaman dan tepian hutan; habitat hutan kaki gunung Qingluan bila context mendukung.
- Konsep: Hewan besar dengan kekuatan fisik tinggi, biasanya menghindari manusia.
- Daging: Daging Beruang.
- Material Biologis: Kulit, Bulu, Cakar, Taring.
- Special Material: Lemak Beruang Hutan jika kondisi dan metode panen mendukung.
- Habitat Resource: Tidak ada default.
- Acquisition: Harvest.
- Condition: Kulit/daging dapat rusak.
- Core: Tidak ada.

### BST-003 — Babi Taring Hutan
- Tier: 1
- Region/Habitat: Dataran Cangyuan — Tepian hutan, pedalaman, dan area pertanian dekat hutan.
- Konsep: Agresif ketika terancam, menyerang dengan tubrukan dan taring.
- Daging: Daging Babi Hutan.
- Material Biologis: Kulit, Taring.
- Special Material: Taring Hutan Utuh.
- Habitat Resource: Tidak ada default.
- Acquisition: Harvest.
- Condition: Taring dapat patah; daging/kulit dapat rusak.
- Core: Tidak ada.

### BST-004 — Kera Batu Liar
- Tier: 1
- Region/Habitat: Pegunungan Qingluan — Kaki gunung dan jalur berbatu.
- Konsep: Hidup berkelompok, lincah, dan mampu melempar batu.
- Daging: Daging Kera.
- Material Biologis: Bulu, Cakar, Taring.
- Special Material: Tidak ada default.
- Habitat Resource: Batu yang dibawa creature hanya jika benar-benar ditemukan.
- Acquisition: Harvest / Collection.
- Condition: Material fisik dapat rusak.
- Core: Tidak ada.

### BST-005 — Macan Loreng Cangyuan
- Tier: 2
- Region/Habitat: Dataran Cangyuan — Pedalaman dan tepian hutan yang jarang dihuni manusia.
- Konsep: Predator soliter yang mengandalkan penyergapan.
- Daging: Daging Macan.
- Material Biologis: Kulit, Bulu, Cakar, Taring.
- Special Material: Kulit Loreng Utuh.
- Habitat Resource: Tidak ada default.
- Acquisition: Harvest.
- Condition: Kulit dapat rusak akibat serangan.
- Core: Tidak ada.

### BST-006 — Elang Tebing
- Tier: 1
- Region/Habitat: Pegunungan Qingluan — Tebing, kaki gunung, dan puncak berbatu.
- Konsep: Predator udara dengan penglihatan tajam dan serangan menukik.
- Daging: Daging Elang.
- Material Biologis: Bulu, Cakar, Paruh.
- Special Material: Bulu Sayap Tebing.
- Habitat Resource: Tidak ada default.
- Acquisition: Harvest.
- Condition: Sayap/bulu mudah rusak.
- Core: Tidak ada.

### BST-007 — Buaya Sungai Besar
- Tier: 2
- Region/Habitat: Dataran Cangyuan — Sungai & tepian hutan serta rawa/perairan dangkal yang sesuai.
- Konsep: Predator penyergap yang sangat kuat di air.
- Daging: Daging Buaya.
- Material Biologis: Kulit, Gigi, Cakar.
- Special Material: Kulit Punggung Utuh.
- Habitat Resource: Tidak ada default.
- Acquisition: Harvest.
- Condition: Kulit dapat rusak; gigi dapat patah.
- Core: Tidak ada.

### BST-008 — Kadal Tanduk Gurun
- Tier: 1
- Region/Habitat: Gurun Jinyan — Oasis, jalur kafilah, dan Laut Pasir Wuheng.
- Konsep: Reptil gurun tahan panas dengan kamuflase pasir.
- Daging: Daging Kadal.
- Material Biologis: Kulit, Tanduk, Cakar.
- Special Material: Sisik Gurun Utuh.
- Habitat Resource: Pasir/mineral gurun hanya jika diperoleh sebagai bagian terpisah.
- Acquisition: Harvest.
- Condition: Tanduk dapat patah; kulit dapat rusak.
- Core: Tidak ada.

### BST-009 — Rubah Pasir
- Tier: 1
- Region/Habitat: Gurun Jinyan — Oasis dan jalur kafilah; pinggiran Laut Pasir Wuheng bila context mendukung.
- Konsep: Omnivora kecil yang cepat dan oportunistik.
- Daging: Daging Rubah.
- Material Biologis: Bulu, Kulit, Cakar, Taring.
- Special Material: Bulu Pasir Halus.
- Habitat Resource: Tidak ada default.
- Acquisition: Harvest.
- Condition: Bulu/kulit dapat rusak.
- Core: Tidak ada.

### BST-010 — Rusa Tanduk Besi
- Tier: 1
- Region/Habitat: Dataran Cangyuan — Area pertanian dan pedalaman/padang terbuka.
- Konsep: Herbivora besar yang menggunakan tanduk sebagai pertahanan.
- Daging: Daging Rusa.
- Material Biologis: Kulit, Bulu, Tanduk, Kuku.
- Special Material: Serpihan Tanduk Besi.
- Habitat Resource: Tumbuhan padang/hutan hanya jika tersedia.
- Acquisition: Harvest.
- Condition: Tanduk dapat retak/patah.
- Core: Tidak ada.



## Fixed Entries — Additional Canon Creatures
> Penambahan berikut bukan quota species. Setiap entry dipilih karena mengisi niche ekologis atau rantai interaksi dunia yang sebelumnya kurang terwakili. Tidak ada entry yang memberikan instance kepada Character, dan tidak ada Item ID baru yang diciptakan di bagian ini.

### BST-011 — Kerbau Lumpur Cangyuan
- Tier: 1
- Region/Habitat: Dataran Cangyuan — sawah, tepian rawa, dan sungai dangkal.
- Bibit / Origin: populasi herbivora lokal yang berkembang di lahan basah Cangyuan; bukan hasil mutasi atau summon.
- Bebet / Acquisition: hewan liar; dapat ditemui saat merumput atau berkubang; domestic specimen hanya sah jika berasal dari penangkaran/pemilikan terpisah.
- Bobot / World Impact: membantu membentuk jalur pertanian, kebutuhan pakan, dan risiko kerusakan sawah; predator lokal dapat mengikuti konsentrasi mangsa di sekitar lahan basah.
- Konsep: herbivora besar, defensif bila anak atau kawanan terancam.
- Daging: possible biological loot.
- Material Biologis: kulit, tanduk, tulang.
- Special Material: tidak ada default.
- Habitat Resource: lumpur/tumbuhan lahan basah hanya jika benar-benar diperoleh sebagai resource terpisah.
- Acquisition: harvest; domestic acquisition memerlukan sumber kepemilikan yang sah.
- Condition: tanduk dapat patah; kulit/daging dapat rusak.
- Core: Tidak ada.

### BST-012 — Laba-laba Kabut Wuyin
- Tier: 2
- Region/Habitat: Pegunungan Qingluan — Hutan Wuyin, terutama celah lembap dan semak berkabut.
- Bibit / Origin: arthropoda predator lokal yang beradaptasi pada kelembapan dan kabut hutan Wuyin.
- Bebet / Acquisition: hidup soliter atau dalam konsentrasi kecil; sarang menjadi tanda ekologis yang dapat ditemukan sebelum encounter.
- Bobot / World Impact: menghubungkan populasi serangga dengan predator kecil dan menciptakan zona sarang yang memengaruhi jalur pemburu/pengumpul.
- Konsep: predator penyergap yang memakai jaring sebagai alat berburu; agresivitas meningkat bila sarang terganggu.
- Daging: tidak relevan sebagai loot utama.
- Material Biologis: cangkang luar/kaki hanya jika metode harvest mendukung.
- Special Material: serat jaring hanya sebagai possible biological source bila benar-benar dapat dipanen.
- Habitat Resource: tidak ada default.
- Acquisition: harvest/collection setelah sarang atau creature benar-benar ditemukan.
- Condition: bagian tubuh dan serat dapat rusak.
- Core: Tidak ada.

### BST-013 — Belut Bara Huoyan
- Tier: 2
- Region/Habitat: Domain Yaohuang Selatan — aliran panas bumi dan celah air hangat Pegunungan Huoyan.
- Bibit / Origin: fauna air lokal yang beradaptasi terhadap aliran mineral dan panas bumi Huoyan.
- Bebet / Acquisition: ditemukan di kolam/aliran panas yang benar-benar memiliki kondisi habitat sesuai; tidak muncul otomatis di seluruh wilayah Huoyan.
- Bobot / World Impact: menjadi indikator perubahan kualitas aliran panas bumi dan sumber mangsa bagi predator air lokal; gangguan populasi dapat mengubah pola penangkapan ikan di sumber air tertentu.
- Konsep: predator air licin dengan toleransi panas tinggi; cenderung menghindar kecuali wilayahnya diganggu.
- Daging: possible biological loot.
- Material Biologis: kulit, gigi, tulang.
- Special Material: tidak ada default.
- Habitat Resource: mineral panas bumi hanya jika source environment menyediakan dan acquisition benar-benar dilakukan.
- Acquisition: harvest.
- Condition: kulit/tubuh dapat rusak oleh metode penangkapan.
- Core: Tidak ada.

### BST-014 — Kepiting Pasir Jinyan
- Tier: 1
- Region/Habitat: Gurun Jinyan — pinggiran oasis dan tanah berpasir dekat sumber air.
- Bibit / Origin: krustasea darat lokal yang bergantung pada kelembapan oasis.
- Bebet / Acquisition: menggali liang dan aktif pada jam yang sesuai; kepadatan mengikuti kondisi oasis, bukan spawn tetap.
- Bobot / World Impact: bagian dari rantai pembersihan organik oasis; perubahan populasinya memengaruhi bangkai kecil, hama, dan sumber pangan lokal.
- Konsep: omnivora kecil, defensif ketika liangnya diganggu.
- Daging: possible biological loot.
- Material Biologis: cangkang, capit.
- Special Material: tidak ada default.
- Habitat Resource: pasir/lempung hanya bila diperoleh melalui aktivitas terpisah.
- Acquisition: harvest.
- Condition: cangkang/capit dapat retak.
- Core: Tidak ada.

### BST-015 — Anjing Hutan Salju Beiming
- Tier: 2
- Region/Habitat: Tanah Salju Beiming — padang salju dan jalur antara permukiman.
- Bibit / Origin: canid liar yang mengikuti migrasi herbivora dan bangkai pada musim dingin.
- Bebet / Acquisition: berburu dalam kelompok kecil; jejak dan sisa buruan menjadi bagian penting dari encounter.
- Bobot / World Impact: predator menekan populasi herbivora kecil dan memindahkan risiko ke jalur pengangkut; kelaparan ekstrem dapat mendekatkan kawanan ke permukiman.
- Konsep: predator oportunistik, menghindari konflik yang tidak perlu tetapi berbahaya bila kawanan terpojok.
- Daging: possible biological loot.
- Material Biologis: kulit, bulu, taring, cakar.
- Special Material: tidak ada default.
- Habitat Resource: tidak ada default.
- Acquisition: harvest.
- Condition: bulu/kulit dapat basah, beku, atau rusak.
- Canon Item Mapping: `ITEM-MAT-010` Kulit Dingin Beiming — kulit/fur hasil harvest sah yang memenuhi source condition item.
- Core: Tidak ada.

### BST-016 — Ubur-Ubur Cahaya Dongming
- Tier: 2
- Region/Habitat: Laut Dongming — perairan dangkal dan arus pesisir Kepulauan Lanyue.
- Bibit / Origin: organisme laut lokal yang memancarkan cahaya biologis lemah dan mengikuti arus pesisir.
- Bebet / Acquisition: encounter bergantung pada arus, musim, cuaca, dan kondisi perairan; tidak dijamin muncul di setiap pelabuhan.
- Bobot / World Impact: menjadi indikator perubahan arus/ekosistem pesisir dan memengaruhi pola makan ikan kecil; konsentrasi besar dapat mengubah rute nelayan lokal.
- Konsep: tidak agresif terhadap manusia secara default; sengatan terjadi ketika terganggu atau terjebak.
- Daging: tidak relevan sebagai loot utama.
- Material Biologis: jaringan tubuh hanya jika metode harvest memungkinkan.
- Special Material: tidak ada default.
- Habitat Resource: tidak ada default.
- Acquisition: harvest/collection dengan metode yang benar-benar tersedia.
- Condition: jaringan sangat mudah rusak.
- Core: Tidak ada.

### SB-016 — Kerbau Roh Sungai Cangyuan
- Tier: 2
- Region/Habitat: Dataran Cangyuan — lahan basah, sungai dangkal, dan padang dekat sawah.
- Bibit / Origin: Spirit Beast lokal yang berasal dari populasi kerbau liar Cangyuan yang hidup lama dalam lingkungan spiritual; bukan hasil kontrak atau summon.
- Bebet / Acquisition: biasanya hidup liar; kedekatan dengan lahan pertanian dapat membuatnya berinteraksi dengan manusia, tetapi tidak berarti jinak.
- Bobot / World Impact: menjaga vegetasi tepian sungai dan dapat mengganggu atau membantu jalur air secara alami; keberadaannya menjadi faktor bagi petani, pemburu, dan penjaga sungai.
- Konsep: tenang tetapi sangat teritorial saat anaknya terancam.
- Growth Potential: stabil; pertumbuhan mengikuti age, nutrition, environment, dan species mechanics.
- Spiritual Affinity: air/tanah hanya sebagai affinity descriptor; tidak memberi ability otomatis.
- Possible Biological Loot: kulit, tanduk, tulang hanya bila makhluk benar-benar mati/berhasil di-harvest.
- Special Material: tidak ada default.
- Core: Tidak ada.

### SB-017 — Kijang Kabut Wuyin
- Tier: 2
- Region/Habitat: Pegunungan Qingluan — Hutan Wuyin dan jalur spiritual yang lembap.
- Bibit / Origin: Spirit Beast herbivora yang berkembang dari fauna kijang lokal yang terpapar lingkungan spiritual Wuyin secara alami.
- Bebet / Acquisition: bergerak mengikuti tumbuhan dan sumber air; migrasi kecilnya dapat membawa pemburu ke bagian hutan yang jarang didatangi.
- Bobot / World Impact: penyebar biji dan bagian penting rantai makanan; kepadatan populasi menjadi indikator tekanan predator dan kesehatan vegetasi.
- Konsep: sangat waspada, mengandalkan pendengaran dan kemampuan membaca perubahan lingkungan.
- Growth Potential: sedang; dipengaruhi umur, nutrisi, habitat, dan kondisi.
- Spiritual Affinity: kabut/air sebagai descriptor lingkungan, bukan buff otomatis.
- Possible Biological Loot: kulit, bulu, tanduk bila acquisition sah.
- Special Material: tidak ada default.
- Core: Tidak ada.

### SB-018 — Salamander Bara Huoyan
- Tier: 3
- Region/Habitat: Domain Yaohuang Selatan — zona panas bumi Pegunungan Huoyan.
- Bibit / Origin: Spirit Beast amfibi yang berkembang di mata air panas/mineral tertentu Huoyan; bukan Phoenix, dragon, atau hasil eksperimen.
- Bebet / Acquisition: cenderung menetap dekat sumber panas yang stabil; perpindahan terjadi bila sumber air/temperatur berubah.
- Bobot / World Impact: menjadi predator lokal sekaligus indikator biologis kestabilan habitat panas bumi; konflik pengambilan sumber air dapat mengubah wilayah jelajahnya.
- Konsep: teritorial, toleran terhadap panas, tetapi tidak otomatis menyerang manusia.
- Growth Potential: sedang–tinggi sesuai species/environment; tidak otomatis berevolusi.
- Spiritual Affinity: fire/heat sebagai descriptor; tidak memberi serangan api numerik tanpa ability source.
- Possible Biological Loot: kulit, cakar, tulang bila acquisition sah.
- Special Material: tidak ada default.
- Core: Tidak ada.

### SB-019 — Rubah Debu Jinyan
- Tier: 2
- Region/Habitat: Gurun Jinyan — oasis, semak gurun, dan pinggiran jalur kafilah.
- Bibit / Origin: Spirit Beast kecil yang berasal dari fauna gurun lokal dan beradaptasi terhadap siklus air oasis.
- Bebet / Acquisition: berpindah antara oasis dan tempat berlindung mengikuti ketersediaan air/mangsa; jejaknya dapat memberi informasi ekologis tetapi tidak menjamin encounter.
- Bobot / World Impact: predator kecil yang menekan hama dan scavenger; perubahan perilakunya dapat menjadi tanda gangguan suplai air atau aktivitas kafilah.
- Konsep: cerdas, oportunistik, cenderung menghindari manusia kecuali terbiasa atau terdesak.
- Growth Potential: sedang.
- Spiritual Affinity: earth/wind sebagai descriptor lingkungan; tidak memberi technique otomatis.
- Possible Biological Loot: bulu, kulit, cakar, taring bila acquisition sah.
- Special Material: tidak ada default.
- Core: Tidak ada.

### SB-020 — Anjing Laut Bulan Dongming
- Tier: 2
- Region/Habitat: Laut Dongming — teluk tenang dan pantai berbatu Kepulauan Lanyue.
- Bibit / Origin: Spirit Beast mamalia laut yang berkembang pada habitat pesisir Dongming; bukan hasil kontrak Istana Naga.
- Bebet / Acquisition: hidup berkelompok kecil dan mengikuti ikan; interaksi dengan nelayan bergantung pada pengalaman lokal.
- Bobot / World Impact: predator ikan pesisir yang membantu membentuk distribusi ikan; koloni dapat menjadi penanda kesehatan perairan dangkal.
- Konsep: sosial, penasaran, tetapi dapat agresif saat anak atau wilayah istirahat terganggu.
- Growth Potential: stabil.
- Spiritual Affinity: water sebagai descriptor.
- Possible Biological Loot: kulit, lemak, gigi hanya bila acquisition sah.
- Special Material: tidak ada default.
- Core: Tidak ada.

### SB-021 — Rusa Salju Xuanyin
- Tier: 3
- Region/Habitat: Tanah Salju Beiming — Lembah Bingxin dan padang salju yang memiliki vegetasi tahan dingin.
- Bibit / Origin: Spirit Beast herbivora yang beradaptasi dengan musim dingin Beiming melalui generasi alami.
- Bebet / Acquisition: migrasi mengikuti vegetasi dan kondisi salju; kawanan dapat berpindah jauh tanpa campur tangan manusia.
- Bobot / World Impact: mangsa utama beberapa predator Beiming dan penyebar vegetasi dingin; perubahan kawanan dapat memengaruhi rute pemburu dan suplai pangan lokal.
- Konsep: waspada, kuat dalam medan salju, tidak agresif kecuali terancam.
- Growth Potential: sedang.
- Spiritual Affinity: cold/wood sebagai descriptor, bukan resistance otomatis.
- Possible Biological Loot: kulit, bulu, tanduk, tulang bila acquisition sah.
- Canon Item Mapping: `ITEM-MAT-010` Kulit Dingin Beiming — hanya bagian kulit/fur yang memenuhi source condition item; tanduk/tulang tetap tanpa Item ID Canon yang terverifikasi.
- Special Material: tidak ada default.
- Core: Tidak ada.

### SB-022 — Kura-kura Garam Jinyan
- Tier: 2
- Region/Habitat: Gurun Jinyan — oasis mineral dan tepi endapan garam.
- Bibit / Origin: Spirit Beast reptil yang beradaptasi dengan air mineral/garam tertentu di oasis Jinyan.
- Bebet / Acquisition: bergerak lambat antara sumber air dan tempat berteduh; tidak muncul di gurun kering tanpa habitat pendukung.
- Bobot / World Impact: memengaruhi vegetasi sekitar oasis melalui pola makan dan pergerakan; keberadaannya dapat menjadi salah satu indikator kestabilan mikrohabitat oasis.
- Konsep: tenang, defensif, memiliki cangkang keras secara biologis.
- Growth Potential: stabil.
- Spiritual Affinity: earth/water descriptor.
- Possible Biological Loot: cangkang, sisik, cakar bila acquisition sah.
- Special Material: tidak ada default.
- Core: Tidak ada.

### SB-023 — Burung Karang Lanyue
- Tier: 2
- Region/Habitat: Laut Dongming — tebing pesisir dan pulau-pulau kecil Kepulauan Lanyue.
- Bibit / Origin: Spirit Beast avian pesisir yang berkembang dari burung laut lokal dan beradaptasi pada lingkungan karang/pesisir.
- Bebet / Acquisition: bersarang pada tebing/pulau tertentu; pola migrasi mengikuti musim, cuaca, dan ketersediaan ikan.
- Bobot / World Impact: predator ikan kecil dan penyebar material organik pesisir; perubahan koloni dapat memengaruhi nelayan serta menjadi indikator perubahan rantai makanan laut.
- Konsep: terbang cepat, hidup berkoloni, defensif terhadap sarang.
- Growth Potential: sedang.
- Spiritual Affinity: wind/water descriptor.
- Possible Biological Loot: bulu, cakar, paruh hanya bila acquisition sah.
- Special Material: tidak ada default.
- Core: Tidak ada.

## Provenance & World-Impact Gate for Fixed Creatures
Untuk seluruh BST-011—BST-016 dan SB-016—SB-023:
1. **Bibit:** species harus memiliki asal ekologis/geografis yang eksplisit; tidak boleh berasal dari summon, eksperimen, atau sejarah tersembunyi tanpa Canon.
2. **Bebet:** jalur kemunculan dan acquisition harus kompatibel dengan habitat, perilaku, dan lifecycle; entry tidak memberikan creature instance secara gratis.
3. **Bobot:** setiap entry harus mempunyai konsekuensi yang dapat berinteraksi dengan ekologi, survival, agriculture, travel, fishing, hunting, market supply, atau encounter pressure. Dampak bukan stat bonus otomatis.
4. **No free item:** possible biological loot di entry ini bukan Item Canon baru dan tidak membuat Item ID baru. Actual loot tetap tunduk pada Module 18/25 dan Item Identity Gate.
5. **No automatic relationship:** Spirit Beast entry tidak memberikan taming, ownership, contract, trust, bond, loyalty, atau BEAST_ID kepada Character.
6. **No automatic ability:** affinity, habitat adaptation, atau concept tidak boleh diterjemahkan menjadi ability/technique/effect numerik tanpa source.
7. **Regional anchoring:** creature tidak dianggap tersedia di luar habitat utamanya tanpa context/runtime yang sah.
8. **Persistence:** encounter individual hanya menjadi persistent entity bila resolution membutuhkan continuity; saat itu Module 24/Save Pipeline berlaku.

## Dynamic Loot Boundary
- Semua loot di atas adalah possible source, bukan guaranteed drop.
- Actual result wajib melewati Loot Eligibility, Loot Potential, Loot Band, Dynamic Result, Quantity, dan Item/Material Validation.
- Kerusakan bagian tubuh, metode acquisition, kondisi creature, habitat, dan special event dapat memengaruhi hasil.
- Special Material tidak otomatis berarti Rare/Very Rare/Exceptional.
- Character Realm tidak otomatis menaikkan Tier atau kualitas loot.
- Tidak ada automatic technique, artifact, currency, breakthrough, atau Core dari entry ini.

## Origin / Canon Source
Admin-established Bestiary Canon v1.3.

## Persistence
Entry fixed Bestiary bersifat Canon. Encounter aktual, kondisi individual creature, hasil loot, Spirit Beast relationship/ownership, dan perubahan runtime tetap harus dicatat melalui state/history/origin sesuai modul terkait.

## Resolution & Validation
Jika fixed entry berlaku, GM mengambil data entry sebagai source fixed dan tetap menjalankan validation. Jika tidak berlaku, gunakan Dynamic Generation. Fixed entry tidak boleh digunakan untuk memberikan atribut yang tidak tercatat.

## Priority
`Fixed Canon Bestiary → Fixed Event/Mission Source → Dynamic Generation → RESOLUTION-BLOCKED`

## Anti-Catalog
Creature hasil Dynamic Generation tidak otomatis masuk database. Penambahan fixed creature harus melalui perubahan Admin Canon dan write-back terverifikasi.
