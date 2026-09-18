# Module 34 — ARTIFACT & WEAPON REFINEMENT

## Status
Admin Canon v1.0

## Purpose
Menetapkan sistem untuk memperbaiki, memperkuat, temper, refine, upgrade, atau mengubah state item/artifact/weapon yang **sudah ada**.

## Boundary
- Module 34 memodifikasi existing Item State.
- Module 31 membuat item baru dari material.
- Module 32 membuat Pill/Alchemy Product.
- Module 33 menangani Formation/Array.
- Module 14 tetap menjadi sumber identity, category, ownership, condition, quality, dan inventory/equipment state item.

## Core Principle
`Existing Item → Valid Refinement Process → New Item State`.
Refinement tidak boleh digunakan sebagai shortcut untuk menciptakan item baru tanpa proses yang sah.

## Source Priority
`Canon/Admin → Fixed Refinement Method → Existing Item State → Refiner Qualification → Material → Tool/Furnace → Cost → Runtime Resolution`

## Required Inputs
1. Existing Item yang valid dan dimiliki/diakses secara sah.
2. Refinement method/procedure yang valid.
3. Refiner dengan qualification yang sah.
4. Material tambahan bila diperlukan.
5. Tool/furnace/workspace bila diperlukan.
6. Resource cost.
7. Waktu/proses.

## Refinement Method
Method dapat berasal dari Canon, manual, teacher, faction, workshop, event, discovery yang benar-benar terjadi, atau Admin Canon.
- Method tidak otomatis diketahui Character.
- Requirement dan batas perubahan hanya berlaku jika sumber mendefinisikannya.

## Qualification
Refiner skill/knowledge harus memiliki Origin melalui training, teacher, manual, faction, experience, event, atau source resmi lain.
Realm Character tidak otomatis menentukan refinement skill.

## Pipeline
`Existing Item → Refinement Method → Refiner Qualification → Material → Tool/Furnace/Workspace → Cost → Process → Validation → Resolution → Success/Partial/Failure → Quality/Property/Condition Change → Item State → Origin → History → Save → Write-Back Verify`

## Resolution
Hasil yang sah:
- Successful Refinement
- Partial Refinement
- Failure with Item Unchanged
- Item Damage/Defect
- Material Loss
- Item Destruction bila mekanisme/source mengizinkan.

Jika source menyediakan check, gunakan source tersebut. Jika tidak, gunakan requirement/process validity yang tersedia tanpa mengarang probabilitas numerik tersembunyi.

## Quality & Properties
Quality/property change hanya boleh terjadi jika refinement method mendukungnya.
Tidak ada automatic quality increase.
Character Realm tidak otomatis meningkatkan quality atau property.

## Category Boundary
Perubahan kategori/grade/tier item harus memiliki mekanisme Canon/Admin yang valid.
Contoh:
`Mortal Sword → Spiritual Artifact` tidak otomatis sah hanya karena refinement berhasil.

## Damage & Failure
Refinement dapat merusak item atau material bila proses mendukungnya.
Failure tidak boleh diam-diam menjadi success.
Item yang rusak harus memiliki state/condition yang sesuai Module 14.

## Durability
Durability/condition hanya berubah jika source atau proses valid mendukung perubahan tersebut. Jangan membuat angka durability baru tanpa dasar.

## Ownership & Provenance
Refinement tidak otomatis mengubah ownership.
Material tambahan harus memiliki Origin.
Jika item ownership berubah melalui hasil transaksi/transfer, gunakan rules Module 14 dan Economy/Contract yang relevan.

## Origin
Setiap refinement material wajib mencatat:
`World Time / Entity ID / Action/Event / Cause / Resolution / Before → After / Source`.
Item Origin lama tidak boleh dihapus; refinement menambahkan riwayat perubahan.

## Anti-Cheat
- Tidak ada existing item fiktif.
- Tidak ada material gratis.
- Tidak ada refinement method/skill gratis.
- Tidak ada guaranteed success.
- Tidak ada automatic breakthrough ke tier/category lebih tinggi.
- Tidak ada automatic Realm scaling.
- Tidak ada free ability/effect.
- Tidak ada hidden time skip.
- Dynamic refinement result bukan Global Canon hanya karena muncul runtime.

## Persistence
Karena refinement mengubah existing Item State, setiap hasil material wajib melalui Save Pipeline. Character State, Item State, consumed materials, currency/resource, Origin, dan History yang berubah harus konsisten sebagai satu transaction.

## Runtime Contract
`ROUTER → REQUIRED SOURCES → EXISTING ITEM VALIDATION → METHOD/QUALIFICATION → COST → PROCESS → RESOLUTION → ITEM STATE VALIDATION → ORIGIN/HISTORY → SAVE → VERIFY`


## DATA COMPLETENESS REFINEMENT GATE
Existing Item, refinement method, qualification, material, tool, cost, quality/property change, dan failure result wajib memiliki source sah. Jangan mengarang peningkatan property/grade/tier. Missing required method/input → RESOLUTION-BLOCKED; unknown non-required field → status resmi.


## 11. DYNAMIC REFINEMENT INTERFACE
Untuk refinement yang hasil konkretnya tidak fixed tetapi tetap dibatasi Canon, Module 34 menyediakan process contract kepada Module 25.

### Source Contract
Method wajib mendefinisikan, atau merujuk secara eksplisit ke source yang mendefinisikan:
- property dimension yang boleh berubah;
- compatibility dengan material/item;
- bound/ceiling perubahan;
- qualification;
- tool/workspace;
- cost/time;
- material consumption;
- success/partial/failure mechanism.

Jika contract tersebut tidak lengkap untuk required resolution, status menjadi `RESOLUTION-BLOCKED`. Module 34 tidak boleh meminta Module 25 untuk mengarang nilai yang hilang.


### Material Property Source Contract
Module 34 consumes the Material Refinement Property Schema defined by Module 14 §4A.

For refinement resolution, Module 34 must verify:
- `MATERIAL_ID`, quantity, and `MATERIAL_ORIGIN`;
- required `REFINEMENT_PROPERTIES`;
- `APPLICABLE_DIMENSIONS`;
- `COMPATIBILITY_TAGS` when present;
- `QUALITY_OR_GRADE` only when explicitly sourced;
- `BOUND_SOURCE` and `CONSUMPTION_RULE` when required;
- `PROPERTY_STATUS` and `PROPERTY_SOURCE`.

The existence of a schema field does not mean the field has a value. Missing required material property remains `UNRESOLVED` and blocks mechanical resolution as `RESOLUTION-BLOCKED` when required.

Material properties describe source capabilities/constraints; the refinement method still decides whether those properties are usable for the target item. Module 34 must not infer an effect from material name, rarity, price, grade, or narrative plausibility.


### 11A. REFINEMENT METHOD SCHEMA

Refinement Method adalah **source mekanis** yang menjelaskan bagaimana material properties yang tervalidasi boleh digunakan pada existing item. Method tidak boleh dipersingkat menjadi "material + item = upgrade".

#### 11A.1 Method Record
Setiap method yang dipakai runtime harus dapat direpresentasikan dengan:

| Field | Required | Fungsi |
|---|---|---|
| `METHOD_ID` | Yes | Identity stabil method/procedure. |
| `METHOD_SOURCE` | Yes | Canon/manual/teacher/faction/workshop/event/discovery/Admin source yang membuktikan method. |
| `TARGET_ITEM_CATEGORY` | Yes | Kategori existing item yang boleh diproses. |
| `TARGET_ITEM_CONSTRAINTS` | Conditional | Constraint tambahan terhadap identity/state item. |
| `MATERIAL_REQUIREMENTS` | Conditional | Material ID/category/property/quantity yang diwajibkan. |
| `COMPATIBILITY_RULE` | Yes | Rule yang menentukan apakah material dan target item dapat diproses bersama. |
| `REQUIRED_REFINER_QUALIFICATION` | Conditional | Qualification/knowledge/skill yang wajib dimiliki refiner. |
| `REQUIRED_TOOL_WORKSPACE` | Conditional | Tool, furnace, workshop, atau workspace yang wajib tersedia. |
| `PROCESS_STEPS` | Yes | Urutan proses yang sah. |
| `PROCESS_TIME` | Yes/Conditional | Waktu proses bila ditetapkan source. |
| `RESOURCE_COST` | Conditional | Resource/currency/stamina/Qi/fuel/tool durability yang benar-benar dibutuhkan bila ditetapkan source. |
| `ALLOWED_PROPERTY_DIMENSIONS` | Yes | Dimensi state/property existing item yang boleh berubah. |
| `CHANGE_BOUNDS` | Yes | Ceiling/range/batas perubahan untuk setiap dimension yang diizinkan. |
| `OUTCOME_MODEL` | Yes | Mekanisme Success/Partial/Failure yang sah. |
| `MATERIAL_CONSUMPTION_RULE` | Conditional | Jumlah/aturan konsumsi material pada outcome yang diizinkan. |
| `FAILURE_CONSEQUENCE` | Conditional | Damage/defect/destruction/material loss bila source mengizinkan. |
| `METHOD_STATUS` | Yes | Status menurut Module 07. |

#### 11A.2 Method Property Contract
Setiap `ALLOWED_PROPERTY_DIMENSIONS` harus dapat ditelusuri ke:
`DIMENSION_ID / TARGET_PROPERTY / DIRECTION_OR_ALLOWED_CHANGE / BOUND_SOURCE / SOURCE / STATUS`

Aturan:
1. Dimension yang tidak tercantum tidak boleh berubah melalui method tersebut.
2. Bound yang tidak memiliki source tidak boleh diisi dengan angka tebakan.
3. Method tidak boleh memperluas property material menjadi effect baru.
4. Method tidak boleh mengubah item category, grade, tier, ability, affinity, atau ownership kecuali mekanismenya secara eksplisit disediakan source.
5. Character Realm bukan substitute untuk qualification atau method bound.

#### 11A.3 Compatibility Contract
Compatibility minimal dievaluasi terhadap:
`Existing Item State + Material Refinement Properties + Method Requirements`

Hasil valid:
- `COMPATIBLE`
- `INCOMPATIBLE`
- `UNRESOLVED`
- `RESOLUTION-BLOCKED`

`UNRESOLVED` compatibility menjadi `RESOLUTION-BLOCKED` bila compatibility wajib untuk menjalankan method.

#### 11A.4 Outcome Contract
`OUTCOME_MODEL` wajib menyatakan mekanisme hasil yang digunakan. Bentuk yang sah dapat berupa:
- deterministic requirement/process validation;
- source-defined check;
- source-defined Success/Partial/Failure mechanism.

Tidak boleh membuat probabilitas, roll, multiplier, atau modifier tersembunyi bila source tidak menyediakannya.

#### 11A.5 Missing-Method Gate
Jika method tidak memiliki required source, target constraint, compatibility rule, allowed dimension, bound, atau outcome mechanism yang diperlukan untuk resolusi, hasilnya `RESOLUTION-BLOCKED`.

Module 25 hanya menerima method yang telah lolos gate ini; Module 25 tidak melengkapi field method yang hilang.

### Bounded Resolution Formula Contract

Module 34 adalah **permission/process authority**; Module 25 adalah **bounded result resolver**. Setelah seluruh precondition tervalidasi, context yang diserahkan ke Module 25 harus mengikuti:

ITEM_STATE + MATERIAL_PROPERTY_RECORDS + METHOD_RECORD + COMPATIBILITY + QUALIFICATION + PROCESS_CONDITIONS → BOUNDED RESOLUTION → BEFORE/AFTER

#### Resolver Input Contract
Module 34 wajib menyerahkan hanya data yang telah tervalidasi:
- Existing Item State dan target constraints;
- material identity, quantity, Origin, dan refinement properties;
- Method Record §11A;
- compatibility result;
- qualification result;
- tool/workspace dan process conditions;
- resource cost/time yang diwajibkan;
- allowed property dimensions, bounds, outcome model, consumption, dan failure consequence.

#### Legal Result Space
Untuk setiap allowed dimension:

LEGAL_RESULT = ItemConstraint ∩ MaterialBound ∩ MethodBound

Resolver tidak boleh keluar dari irisan constraint/bound yang tersedia. Dimension yang tidak tercantum dalam Method Record berada di luar result space. Bound yang tidak memiliki source tidak boleh dibuat.

#### Outcome Delegation
Module 34 menentukan mekanisme outcome melalui OUTCOME_MODEL. Module 25 hanya memilih concrete runtime result sesuai mekanisme tersebut. Bila source menyediakan roll/probability, hanya parameter source yang boleh digunakan; bila tidak, tidak boleh dibuat probabilitas/roll tersembunyi.

Jika required input, bound, compatibility, qualification, process condition, atau outcome mechanism tidak dapat dibuktikan, refinement tidak dilanjutkan dan statusnya RESOLUTION-BLOCKED.

#### Before/After Boundary
Resolver result harus dapat diterapkan sebagai satu transaction:
BEFORE → RESOLUTION → AFTER
yang mencakup Item State, consumed Material, resource/cost/time, serta Origin/History seluruh entity yang berubah.

### Resolver Boundary
- Module 34: validasi existing item + method + qualification + process permission.
- Module 25: memilih concrete runtime result di dalam bounds yang sah.
- Module 14: authoritative Item State.
- State Validator: validates before/after and provenance.
- Save Pipeline: persists the complete transaction.



## 12. OUTCOME / BOUND SOURCE CATALOG

Catalog ini adalah **source mekanis konkret** untuk refinement. Record di bawah adalah Admin Canon yang sengaja dibatasi pada perubahan yang dapat dijelaskan tanpa bonus numerik. Record catalog tidak boleh diperluas oleh Qwen.

### 12.1 Source Record Contract

Setiap source refinement aktif wajib memuat:

SOURCE_ID / SOURCE_STATUS / SOURCE_AUTHORITY / MATERIAL_SCOPE / TARGET_ITEM_SCOPE / PROPERTY_DIMENSIONS / COMPATIBILITY / BOUNDS / QUALIFICATION / PROCESS_CONDITIONS / OUTCOME_MODEL / CONSUMPTION / FAILURE_CONSEQUENCE

SOURCE_STATUS = CANON-ESTABLISHED hanya bila seluruh field yang required untuk eksekusi sudah ditetapkan. Record yang belum lengkap tidak dapat dipakai sebagai executable refinement.

### 12.2 SRC-REF-001 — Basic Iron Condition Restoration

| Field | Canonical Value |
|---|---|
| SOURCE_ID | SRC-REF-001 |
| SOURCE_STATUS | CANON-ESTABLISHED |
| SOURCE_AUTHORITY | Admin Canon — TianDao-World Refinement Source Catalog |
| MATERIAL_SCOPE | ITEM-MAT-001 — Bijih Besi Kasar |
| TARGET_ITEM_SCOPE | Existing Weapon dengan state CONDITION = DAMAGED atau CONDITION = SERVICEABLE |
| PROPERTY_DIMENSIONS | CONDITION saja |
| COMPATIBILITY | Compatible hanya bila target adalah existing Weapon berbahan logam dan material ITEM-MAT-001 tersedia |
| BOUND | DAMAGED → SERVICEABLE; SERVICEABLE → SERVICEABLE. Tidak ada transition ke quality/grade/tier/ability/affinity baru |
| QUALIFICATION | Refiner wajib memiliki source sah untuk basic metalworking/forging qualification |
| PROCESS_CONDITIONS | Forge/workspace metalworking yang valid wajib tersedia; material dan target item harus benar-benar tersedia |
| OUTCOME_MODEL | Deterministic requirement/process validation: bila seluruh requirement terpenuhi, transition yang diizinkan source dapat diterapkan; bila tidak terpenuhi, refinement diblokir |
| CONSUMPTION | Tidak ditetapkan pada source ini; bila quantity consumption diperlukan oleh proses aktual, harus berasal dari source proses tersendiri |
| FAILURE_CONSEQUENCE | Tidak ditetapkan; source ini tidak mengizinkan damage/destruction atau hidden failure mechanism |

**Hard boundary:** SRC-REF-001 hanya mengatur condition transition yang tertulis di atas. Ia tidak memberi attack bonus, defense bonus, durability angka, quality/grade/tier increase, ability, affinity, atau probability.

### 12.3 Source Execution Rule

Untuk SRC-REF-001:

ITEM CONDITION + MATERIAL SCOPE + COMPATIBILITY + QUALIFICATION + PROCESS CONDITIONS → CONDITION TRANSITION → BEFORE/AFTER

Jika target tidak memenuhi compatibility atau qualification, jangan mengubah item. Jika field required dari source ternyata tidak dapat diverifikasi pada runtime, gunakan RESOLUTION-BLOCKED.

### 12.4 Catalog Boundary

1. Catalog source adalah **whitelist**, bukan izin improvisasi.
2. Qwen hanya boleh memakai SOURCE_ID yang statusnya executable dan field required-nya lengkap.
3. Material yang tidak tercantum dalam MATERIAL_SCOPE tidak memperoleh effect dari source tersebut.
4. Property dimension yang tidak tercantum tidak boleh berubah.
5. Bound yang tidak tercantum tidak boleh dibuat.
6. Source tidak boleh digabungkan untuk menciptakan effect baru kecuali compatibility/method source secara eksplisit mengizinkan composition.
7. Dynamic selection tetap hanya memilih hasil di dalam bound source; catalog tidak memberi hak untuk memilih angka baru.
8. Bila source catalog dan source yang lebih spesifik bertentangan, gunakan source yang lebih spesifik dan terverifikasi; bila konflik tidak dapat diselesaikan, RESOLUTION-BLOCKED.

### 12.5 Numeric Boundary

Catalog ini **tidak** menetapkan bonus numerik, multiplier, probability, roll, atau scaling. DAMAGED → SERVICEABLE adalah state transition Canon, bukan angka bonus.

### 12.6 Expansion Rule

Penambahan material, property dimension, compatibility rule, bound, qualification, process condition, consumption, atau outcome baru wajib menjadi record SOURCE_ID tersendiri atau revisi Admin Canon yang terdokumentasi. Qwen tidak boleh memperluas catalog saat runtime.

### Explicit Prohibition
Material rarity, nama, market value, Character Realm, atau narrative plausibility tidak boleh dipakai sebagai implicit refinement effect.
