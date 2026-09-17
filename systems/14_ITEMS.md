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
