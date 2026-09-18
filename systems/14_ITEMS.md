# 14 — ITEMS

## 1. Kategori
Item dapat berupa consumable, material, weapon, armor/protection, accessory, artifact, currency, quest item, atau kategori resmi lain.

Spirit Beast bukan Item dan tidak boleh dimasukkan ke kategori Item hanya karena dimiliki, dibawa, dipanggil, atau memiliki contract.

## 2. Equipment
Equipment adalah item yang sedang aktif dipakai/digenggam dan dapat memengaruhi combat hanya jika efeknya tercatat.

Spirit Beast tidak menjadi Equipment. Jika Beast memiliki perlengkapan sendiri, perlengkapan tersebut tetap merupakan item yang memiliki origin dan tercatat pada Beast sesuai aturan Module 24, tanpa mengubah identitas Beast menjadi item.

## 3. Inventory
Inventory adalah barang yang dibawa tetapi tidak sedang dipakai. Item tetap membutuhkan sumber kepemilikan.

BEAST_ID tidak boleh disimpan sebagai Inventory Item ID. Beast State berada di `characters/beasts/<BEAST_ID>.md`.

## 4. Canon Item Identity
Item Canon yang dapat digunakan oleh fixed loot, recipe, quest reward, atau event reward menggunakan ID stabil berikut. ID ini adalah identity/content reference; kepemilikan individual tetap dicatat melalui Origin Log.

| Item ID | Nama | Kategori | Baseline fungsi |
|---|---|---|---|
| ITEM-MAT-001 | Bijih Besi Kasar | Material | bahan logam umum |
| ITEM-MAT-002 | Kayu Keras Cangyuan | Material | bahan konstruksi umum |
| ITEM-MAT-003 | Kulit Binatang Biasa | Material | bahan kulit umum |
| ITEM-MAT-004 | Taring Binatang Biasa | Material | komponen material umum |
| ITEM-HERB-001 | Rumput Embun Pagi | Herb | bahan herbal dasar |
| ITEM-HERB-002 | Rumput Jarum Beracun | Herb | bahan herbal beracun |
| ITEM-CONS-001 | Bubuk Penghenti Darah | Consumable | menghentikan perdarahan ringan sesuai prosedur medis |
| ITEM-CONS-002 | Pil Penetral Racun Dasar | Consumable | penanganan racun dasar; tidak universal |
| ITEM-WPN-001 | Pisau Belati Besi Tempa | Weapon | belati besi sederhana |
| ITEM-WPN-002 | Pedang Besi Standar | Weapon | pedang besi sederhana |
| ITEM-MAT-005 | Serat Rami | Material | bahan tali/kerajinan |
| ITEM-MAT-006 | Batu Api | Material/Tool | sumber api sederhana |

### Aturan Identity
- Item ID tidak berubah ketika item berpindah tangan.
- Dua item dengan Item ID sama tetap dapat menjadi dua instance fisik berbeda.
- Instance individual wajib memiliki Origin dan riwayat kepemilikan bila perubahan material.
- Nama item tidak otomatis menentukan kualitas, durability, effect, atau rarity di luar data Canon item.
- Item yang belum mempunyai Item ID Canon tidak boleh dimasukkan ke fixed loot table sebagai item spesifik.


## 4A. MATERIAL REFINEMENT PROPERTY SCHEMA

Bagian ini menetapkan **schema data**, bukan daftar efek material. Schema menjadi kontrak sumber untuk refinement existing item; nilai konkret hanya sah bila diisi oleh Canon/Admin atau source material yang terverifikasi.

### 4A.1 Purpose & Boundary
Material memiliki identity dan baseline function, tetapi **tidak otomatis memiliki refinement effect**. Refinement-relevant properties hanya boleh digunakan bila field tersebut benar-benar ditetapkan oleh source material yang sah.

Canonical boundary:
`Material Identity → Refinement Property Schema → Module 34 Compatibility/Method → Module 25 Bounded Runtime Resolution`

Module 14 adalah authority untuk identity/state item. Module 34 menentukan apakah property material dapat dipakai oleh refinement method. Module 25 hanya memilih hasil runtime di dalam bounds yang sudah tersedia.

### 4A.2 Schema
Setiap material yang dipakai sebagai input refinement wajib dapat direpresentasikan dengan field berikut:

| Field | Required | Fungsi |
|---|---|---|
| `MATERIAL_ID` | Yes | ID Canon atau instance material yang menjadi sumber input. |
| `MATERIAL_ORIGIN` | Yes | Provenance material; harus dapat ditelusuri. |
| `MATERIAL_QUANTITY` | Yes | Jumlah material yang benar-benar tersedia untuk proses. |
| `REFINEMENT_PROPERTIES` | Conditional | Kumpulan property yang secara eksplisit ditetapkan source sebagai relevan untuk refinement. |
| `APPLICABLE_DIMENSIONS` | Conditional | Dimensi item yang boleh dipengaruhi, mis. condition, durability, structural property, atau property lain **hanya bila source mendefinisikannya**. |
| `COMPATIBILITY_TAGS` | Conditional | Tag/constraint yang dapat dibandingkan dengan requirement refinement method. |
| `QUALITY_OR_GRADE` | Conditional | Kualitas/grade material bila source memang menetapkannya; tidak boleh diturunkan dari nama atau harga. |
| `BOUND_SOURCE` | Conditional | Referensi source yang menetapkan ceiling/range perubahan bila material property ikut menentukan batas. |
| `CONSUMPTION_RULE` | Conditional | Aturan jumlah material yang dikonsumsi bila proses refinement menetapkannya. |
| `PROPERTY_STATUS` | Yes | Status data menurut Module 07: `CANON-ESTABLISHED`, `STATE-ESTABLISHED`, `RUNTIME-GENERATED`, `NOT-APPLICABLE`, `NOT-INSTANTIATED`, `UNRESOLVED`, atau `RESOLUTION-BLOCKED`. |
| `PROPERTY_SOURCE` | Yes | Source yang membuktikan property; bukan narasi Player atau plausibility. |

### 4A.3 Property Record Contract
Setiap entry dalam `REFINEMENT_PROPERTIES` minimal memiliki:

`PROPERTY_ID / PROPERTY_NAME / VALUE_OR_RANGE / UNIT_IF_APPLICABLE / APPLICABLE_ITEM_CATEGORY / SOURCE / STATUS`

Aturan:
1. `PROPERTY_ID` harus stabil bila property menjadi Canon.
2. `VALUE_OR_RANGE` tidak boleh diisi dengan tebakan.
3. `UNIT_IF_APPLICABLE` hanya digunakan bila mekanik source memakai unit tersebut.
4. `APPLICABLE_ITEM_CATEGORY` membatasi target yang dapat memanfaatkan property.
5. `SOURCE` wajib menunjuk ke Canon/Admin atau source resmi yang menetapkan property.
6. `STATUS` wajib mengikuti vocabulary Module 07.

### 4A.4 Explicit Non-Inference
Property berikut **tidak boleh di-infer otomatis** dari material:
- rarity;
- market price;
- nama/deskripsi;
- visual appearance;
- origin location;
- Character Realm;
- narrative claim;
- hasil refinement sebelumnya;
- kategori material semata.

Khususnya, material tidak otomatis memberi:
- bonus attack/defense;
- durability increase;
- quality/grade/tier increase;
- affinity;
- ability/effect;
- bloodline;
- breakthrough;
- success probability.

Semua hal tersebut memerlukan source mekanis tersendiri.

### 4A.5 Missing Property Gate
Jika refinement method membutuhkan property tertentu dan material source tidak menyediakan property tersebut:
- field material → `UNRESOLVED` bila datanya belum dapat ditentukan;
- resolution → `RESOLUTION-BLOCKED` bila field tersebut required untuk keputusan mekanis.

Qwen tidak boleh mengisi property melalui improvisasi, memory, Player request, atau plausibility.

### 4A.6 Source/State Separation
`PROPERTY_SOURCE` menjelaskan **mengapa property ada**; `MATERIAL_ORIGIN` menjelaskan **dari mana instance material berasal**. Keduanya tidak boleh dipertukarkan.

Material Canon dapat memiliki property Canon, sementara instance material tetap memerlukan Origin dan quantity/state aktual.

### 4A.7 Compatibility Boundary
Schema property tidak otomatis berarti material kompatibel dengan semua item. Compatibility harus divalidasi oleh Module 34 melalui refinement method/source.

`Material Property → Compatibility Check → Allowed Dimension/Bound → Runtime Resolution`

Jika tidak ada compatibility rule yang sah, jangan menyimpulkan kompatibilitas dari kemiripan nama, kategori, atau narasi.

### 4A.8 No Concrete Effect Table Yet
Schema ini **sengaja tidak menetapkan nilai bonus, multiplier, probability, compatibility matrix, atau material-specific refinement effect**. Data tersebut menjadi tahap mechanics design berikutnya dan hanya boleh ditambahkan melalui source Canon yang terdokumentasi.


## 5. Origin
Setiap item harus memiliki asal:
- pembelian;
- loot;
- pemberian;
- crafting/forging;
- alchemy;
- atau sumber resmi lain yang eksplisit.

Origin Log mencatat item, sumber, waktu, dan perubahan kepemilikan.

## 6. Bobot & Kapasitas
Bobot item diperhitungkan bila data item mencantumkannya. Kapasitas angkut mengikuti kondisi karakter, equipment, mount, storage, atau aturan resmi.

Beast tidak otomatis dihitung sebagai item yang mengisi Inventory/Equipment capacity kecuali sistem transport/storage resmi secara eksplisit mengaturnya.

## 7. Penggunaan
Consumable berkurang/habis saat digunakan. Durability, charge, cooldown, atau batas penggunaan hanya berlaku jika dicatat oleh item/system.

Jika Character memberikan atau menggunakan item untuk Spirit Beast, item harus berasal dari state Character/Beast yang sah dan perubahan kepemilikan/penggunaan dicatat melalui Origin Log.

## 8. Integrasi
Items terhubung dengan Economy, Loot, Combat, Techniques, Organizations, Reputation, Spirit Beast, Crafting, Alchemy, Formation, Refinement, dan Save Integrity.


### 4A.9 Catalog-Sourced Canon Property

ITEM-MAT-001 memiliki satu refinement-relevant property yang ditetapkan oleh SRC-REF-001:

| PROPERTY_ID | PROPERTY_NAME | VALUE_OR_RANGE | APPLICABLE_ITEM_CATEGORY | SOURCE | STATUS |
|---|---|---|---|---|---|
| REFPROP-MAT-001-001 | METAL_FORMABILITY | BASIC | Metal Weapon | SRC-REF-001 — Basic Iron Condition Restoration | CANON-ESTABLISHED |

Property ini hanya menyatakan bahwa ITEM-MAT-001 memiliki formability dasar untuk source tersebut. Property ini **bukan bonus item** dan tidak boleh diterjemahkan menjadi attack, defense, durability, quality, tier, ability, affinity, atau probability.

Untuk SRC-REF-001, compatibility tetap harus mengikuti Method/Source Record; keberadaan property ini tidak membuat material kompatibel dengan seluruh Weapon secara otomatis.

## 4B. ADMIN CANON — REGIONAL MATERIAL & ITEM EXPANSION

> Penambahan ini bukan quota catalog. Setiap item di bawah harus memiliki **bibit/bebet/bobot**: sumber geografis atau ekologis yang jelas, jalur perolehan yang sah, fungsi yang benar-benar terhubung ke sistem TianDao, serta dampak dunia yang dapat diverifikasi. Item tidak menjadi milik Character tertentu hanya karena ditetapkan di Canon.

### 4B.1 Canon Item Registry

| Item ID | Nama | Kategori | Baseline fungsi | Canon Origin | Dampak TianDao |
|---|---|---|---|---|---|
| ITEM-MAT-007 | Getah Pinus Roh Qingluan | Material/Alchemy | bahan pengikat dan pengawet untuk proses material/kayu | Hutan pinus spiritual Pegunungan Qingluan; dipanen dari pohon yang benar-benar menghasilkan getah | membuka jalur material regional Qingluan untuk crafting/alchemy dan menjadi komoditas bahan spiritual |
| ITEM-HERB-003 | Jamur Kabut Wuyin | Herb | bahan herbal untuk proses alchemy/obat yang kompatibel | Hutan Wuyin, Pegunungan Qingluan; tumbuh pada area lembap berkabut | membuat Hutan Wuyin memiliki sumber bahan herbal bernilai dan memberi alasan gameplay untuk ekspedisi/pengumpulan berisiko |
| ITEM-MAT-008 | Terak Besi Api Huoyan | Material | bahan campuran/umpan material untuk forging yang membutuhkan sumber logam panas bumi | zona panas bumi Pegunungan Huoyan; berasal dari endapan/aktivitas mineral yang terekspos | menghubungkan geologi Huoyan dengan forging dan perdagangan material; tidak otomatis menaikkan kualitas senjata |
| ITEM-HERB-004 | Madu Seratus Bunga | Herb/Consumable Ingredient | bahan pangan/herbal dan input proses alchemy yang kompatibel | Lembah Seratus Bunga; berasal dari koloni penyerbuk lokal yang mengambil nektar flora lembah | menciptakan komoditas biologis regional yang menghubungkan flora, fauna, alchemy, dan ekonomi |
| ITEM-MAT-009 | Mutiara Pasang Dongming | Material/Accessory Material | bahan perhiasan, perdagangan, atau komponen proses yang secara eksplisit memerlukan material mutiara | perairan pesisir Laut Dongming; diperoleh dari kerang/makhluk laut yang benar-benar menghasilkan mutiara | menambah jalur ekonomi laut dan risiko pengambilan sumber daya; tidak otomatis memiliki efek spiritual |
| ITEM-MAT-010 | Kulit Dingin Beiming | Material | bahan pakaian/perlindungan dingin | hasil pengulitan sah fauna/monster yang hidup di habitat dingin Beiming dan memang memiliki kulit/fur yang dapat dimanfaatkan | menghubungkan survival wilayah dingin dengan crafting perlindungan; tidak menghapus aturan suhu otomatis |
| ITEM-MAT-011 | Kristal Garam Jinyan | Material | bahan pengawet, perdagangan, dan proses material yang membutuhkan garam mineral | endapan garam mineral Oasis/Jalur Gurun Jinyan yang dapat ditambang secara sah | memberi nilai ekonomi pada jalur oasis dan mendukung logistik pangan tanpa menciptakan air atau suplai gratis |
| ITEM-MAT-012 | Pecahan Giok Baiyu | Material | bahan kerajinan, ukiran, atau konstruksi/komponen formation bila recipe mengizinkan | endapan/limbah pengerjaan giok di sekitar Kota Baiyu; bukan otomatis berasal dari reruntuhan kuno | menghubungkan Kota Baiyu dengan kerajinan bernilai dan sumber material yang dapat diperdagangkan |
| ITEM-MAT-013 | Serat Sungai Cangyuan | Material | bahan anyaman, tali, dan perbaikan perlengkapan sederhana | tanaman serat di tepian sungai Dataran Cangyuan yang dipanen secara berkelanjutan | memperkuat ekonomi material dasar Cangyuan dan memberi alternatif lokal selain Serat Rami |
| ITEM-MAT-014 | Cangkang Karang Lanyue | Material | bahan kerajinan/komponen pelindung atau dekoratif yang membutuhkan cangkang keras | Kepulauan Lanyue; diperoleh dari organisme laut bercangkang yang telah mati/ditangkap secara sah | menghubungkan eksplorasi kepulauan dengan ekonomi bahan laut; tidak memberi armor stat otomatis |

### 4B.2 Provenance / Bibit-Bebet-Bobot Gate

Untuk seluruh ITEM-* di §4B:
1. **Bibit / source identity:** setiap item memiliki asal geografis/ekologis yang dinyatakan di Canon.
2. **Bebet / acquisition lineage:** item hanya sah diperoleh melalui panen, pengumpulan, pengolahan, loot, atau perdagangan yang kompatibel dengan source. Canon item tidak memberikan instance gratis.
3. **Bobot / systemic weight:** dampak item dinyatakan pada fungsi sistemik yang relevan; tidak boleh diterjemahkan menjadi stat, rarity, harga, atau efek khusus tanpa source mekanis.
4. **Instance provenance:** setiap instance tetap membutuhkan Origin Log berisi source entity/location, acquisition method, World Time, claimant/owner, dan perubahan kepemilikan.
5. **No universal availability:** asal regional tidak berarti item selalu tersedia, selalu muncul, atau dapat dibeli di semua kota.
6. **No automatic effect:** nama dan asal item tidak otomatis menciptakan affinity, buff, resistance, breakthrough, technique, bloodline, atau quality tier.
7. **No Character inheritance:** penambahan Canon item tidak mengubah inventory/current state Character yang sudah ada.
8. **Loot integration:** fixed loot hanya boleh menunjuk Item ID yang telah ada dan source condition yang sesuai.
9. **Dynamic boundary:** di luar fixed source, item tetap dapat menjadi hasil runtime hanya bila Dynamic Loot/Generation dan source validation memang mengizinkannya.
10. **Data completeness:** quantity, condition, quality, ownership, availability, dan instance location yang belum diketahui tetap mengikuti core/07_DATA_COMPLETENESS.md.

### 4B.3 Regional Source IDs

Sumber berikut adalah **Canon source class**, bukan instance item dan bukan jaminan spawn:
- SRC-RES-CGY-001 — Serat Sungai Cangyuan — tepian sungai Dataran Cangyuan
- SRC-RES-QGL-001 — Getah Pinus Roh Qingluan — hutan pinus Pegunungan Qingluan
- SRC-RES-QGL-002 — Jamur Kabut Wuyin — Hutan Wuyin
- SRC-RES-YHS-001 — Terak Besi Api Huoyan — zona panas bumi Pegunungan Huoyan
- SRC-RES-YHS-002 — Madu Seratus Bunga — Lembah Seratus Bunga
- SRC-RES-DGM-001 — Mutiara Pasang Dongming — pesisir Laut Dongming
- SRC-RES-DGM-002 — Cangkang Karang Lanyue — Kepulauan Lanyue
- SRC-RES-BMG-001 — Kulit Dingin Beiming — habitat dingin Tanah Salju Beiming
- SRC-RES-GJY-001 — Kristal Garam Jinyan — endapan garam mineral Gurun Jinyan
- SRC-RES-TYN-001 — Pecahan Giok Baiyu — rantai pengerjaan/limbah giok Kota Baiyu

Source class hanya membuktikan **asal yang sah**; actual quantity/condition/availability harus berasal dari runtime atau state yang tervalidasi.
