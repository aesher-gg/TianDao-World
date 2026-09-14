# 00 — FIXED BESTIARY DATABASE

## Status
Admin Canon v1.3 — Fixed Bestiary Concepts, Habitats & Loot Profiles

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
`Fixed Canon Bestiary → Fixed Event/Mission Source → Dynamic Generation → ???`

## Anti-Catalog
Creature hasil Dynamic Generation tidak otomatis masuk database. Penambahan fixed creature harus melalui perubahan Admin Canon dan write-back terverifikasi.
