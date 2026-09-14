# Module 32 — ALCHEMY & PILL REFINEMENT

## Status
Admin Canon v1.0

## Purpose
Menetapkan pipeline khusus untuk memproses herb/material menjadi Pill atau produk alkimia melalui formula, alchemist qualification, furnace, preparation, refinement, dan validated resolution.

## Boundary
- Module 32 menangani Alchemy, Pill Refinement, dan hasil alkimia.
- Module 31 menangani crafting/forging umum.
- Module 34 menangani refinement item/artifact/weapon yang sudah ada.
- Module 14 tetap menjadi sumber state/identity item hasil alchemy.

## Source Priority
`Canon/Admin → Fixed Formula/Pill Source → Current State → Valid Material Origin → Alchemist Qualification → Furnace/Tool → Runtime Resolution`

## Required Inputs
1. Herb/material yang valid.
2. Formula/recipe/prosedur yang valid, kecuali improvisasi alchemy memang didukung source.
3. Alchemist dengan knowledge/qualification yang sah.
4. Furnace/tool yang dibutuhkan.
5. Resource cost.
6. Waktu/proses.
7. Kondisi bahan yang relevan.

## Formula
Formula dapat berasal dari Canon, manual, teacher, faction, laboratory/workshop, event, discovery yang benar-benar terjadi, atau Admin Canon.
- Formula tidak otomatis diketahui Character.
- Formula menentukan bahan, proses, requirement, output, dan batas kualitas hanya bila sumber mendefinisikannya.
- Nama Pill tidak cukup untuk mengarang efek.

## Alchemist Qualification
Qualification harus memiliki Origin melalui training, teacher, manual, faction, experience, event, atau source resmi lain.
- Sekali mencoba tidak otomatis memberi mastery.
- Realm Character tidak otomatis menentukan alchemy skill.
- Alchemist tidak otomatis mampu membuat semua formula yang diketahui.

## Furnace & Process
Furnace adalah tool produksi. Preparation, heating, extraction, mixing, condensation, refinement, cooling, dan tahap lain hanya berlaku jika formula/proses mendukungnya.
Kondisi furnace/tool/environment hanya menjadi modifier bila ada aturan yang sah; tidak boleh membuat angka tersembunyi.

## Resource & Cost
Cost dapat berupa herb, material, fuel, waktu, stamina, Qi, currency, furnace durability, atau biaya workshop/laboratory bila memang ditentukan.
Tidak ada bahan atau resource gratis.

## Alchemy Pipeline
`Herb/Material → Formula → Alchemist Qualification → Furnace/Tool → Preparation → Refinement Process → Validation → Resolution → Failure/Deviation/Success → Pill Quality → Quantity → Effect → Defect/Side Effect → Item Origin → History → Save → Write-Back Verify`

## Resolution
Hasil yang sah:
- Success
- Partial Success
- Failure
- Defective Pill/Product
- Material Loss/Damage

Jika formula atau sistem menyediakan check, gunakan check tersebut. Jika tidak, gunakan requirement dan process validity yang tersedia; jangan mengarang probabilitas numerik tersembunyi.

## Pill Quality
Quality dapat berupa label yang sudah didefinisikan source. Jika source tidak menetapkan skala quality, GM tidak boleh menciptakan tier mekanis baru hanya untuk memperkuat hasil.
Quality tidak otomatis mengikuti Realm Alchemist.

## Quantity
Quantity mengikuti formula/fixed source bila tersedia. Jika tidak tersedia, quantity tidak boleh ditebak untuk menjamin reward.

## Effect & Defect
Efek, potency, duration, side effect, toxicity, atau defect harus memiliki source mekanis yang valid.
Jika tidak diketahui: `???`.
Tidak boleh mengubah Pill menjadi obat universal atau breakthrough item tanpa Canon/source.

## Failure
Failure dapat merusak/meniadakan bahan, menghabiskan resource, atau menghasilkan produk cacat bila proses mendukungnya.
Kegagalan tidak boleh diam-diam menjadi Pill sukses.

## Item Origin
Pill/product yang berhasil dibuat menjadi Item State menurut Module 14 dan wajib memiliki provenance:
`World Time / Entity ID / Action / Cause / Resolution / Before → After / Source`
Semua bahan yang dikonsumsi harus mempunyai Origin sebelumnya.

## Anti-Cheat
- Tidak ada herb/material gratis.
- Tidak ada formula gratis.
- Tidak ada instant alchemist mastery.
- Tidak ada automatic success.
- Tidak ada guaranteed high-quality pill.
- Tidak ada free breakthrough.
- Tidak ada effect yang tidak disumberkan.
- Tidak ada hidden time skip.
- Dynamic formula/result bukan Global Canon hanya karena muncul runtime.

## Persistence
Perubahan bahan, furnace/tool state, Pill/Item State, Character State, Origin, dan History yang material wajib melalui Save Pipeline sebagai transaction yang konsisten.

## Runtime Contract
`ROUTER → REQUIRED SOURCES → INPUT VALIDATION → COST → PROCESS → RESOLUTION → RESULT VALIDATION → ITEM ORIGIN → STATE/HISTORY → SAVE → VERIFY`
