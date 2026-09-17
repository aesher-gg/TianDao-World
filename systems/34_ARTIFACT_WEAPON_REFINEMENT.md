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

### Resolver Boundary
- Module 34: validasi existing item + method + qualification + process permission.
- Module 25: memilih concrete runtime result di dalam bounds yang sah.
- Module 14: authoritative Item State.
- State Validator: validates before/after and provenance.
- Save Pipeline: persists the complete transaction.

### Explicit Prohibition
Material rarity, nama, market value, Character Realm, atau narrative plausibility tidak boleh dipakai sebagai implicit refinement effect.
