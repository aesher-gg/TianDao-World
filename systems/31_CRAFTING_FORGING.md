# Module 31 — CRAFTING & FORGING

## Status
Admin Canon v1.0

## Purpose
Menetapkan sistem universal untuk membuat, membentuk, memproses, atau menempa item dari material yang valid. Module ini adalah production framework untuk Crafting/Smithing/Forging dan tidak menggantikan Module 14 Items.

## Boundary
- Module 31 membuat **item baru** atau hasil material processing yang menjadi item.
- Module 34 menangani perubahan pada **item yang sudah ada** melalui refinement/upgrade.
- Module 32 khusus Alchemy/Pill.
- Module 33 khusus Formation/Array.
- Module 14 tetap menjadi sumber state/identity item.

## Core Principle
`Material ≠ Recipe ≠ Skill ≠ Tool ≠ Workspace`.
Memiliki salah satu tidak otomatis memberikan yang lain. Player intent bukan bukti bahwa recipe, skill, tool, atau hasil tersedia.

## Source Priority
`Canon/Admin → Fixed Recipe/Technique/Item Source → Current State → Valid Material Origin → Valid Crafter Skill/Knowledge → Tool/Workspace → Runtime Resolution`

Jika input wajib tidak diketahui dan tidak memiliki fallback resmi, gunakan `UNRESOLVED` atau tahan proses. Jika input tersebut wajib untuk resolusi, status hasil menjadi `RESOLUTION-BLOCKED`.

## Required Inputs
1. Material yang sah dan cukup.
2. Recipe/blueprint/prosedur yang valid, kecuali proses improvisasi memang didukung oleh source.
3. Crafter dengan skill/knowledge yang valid.
4. Tool/workspace yang diperlukan.
5. Resource cost yang dapat dibayar.
6. Waktu/proses yang sesuai.
7. Material condition yang diketahui bila memengaruhi hasil.

## Recipe
Recipe dapat berasal dari Canon, manual, teacher, faction, workshop, event, discovery yang benar-benar terjadi, atau Admin Canon.
- Recipe tidak otomatis diketahui Character.
- Recipe dapat memiliki requirement, material, tool, process, difficulty, output, dan quality ceiling bila sumber mendefinisikannya.
- Jika output/quality/effect tidak didefinisikan sumber, jangan mengarang spesifikasi mekanis.

## Crafting Qualification
Qualification dapat berasal dari skill/technique/profession training yang valid.
- Training membutuhkan source dan proses yang nyata.
- Skill tidak otomatis naik karena sekali mencoba.
- Realm Character tidak otomatis menentukan crafting skill.

## Tools & Workspace
Tool dan workspace harus benar-benar tersedia dan valid untuk proses.
Kondisi tool/workspace dapat memblokir atau memengaruhi proses hanya jika aturan/recipe mendukungnya. Jangan membuat modifier numerik baru tanpa dasar.

## Resource & Cost
Cost dapat mencakup material, bahan bakar, waktu, stamina, Qi, currency, durability, atau biaya workshop.
Hanya cost yang memiliki source mekanis yang boleh diterapkan. Tidak ada material, currency, atau resource gratis.

## Universal Production Pipeline
`Material → Recipe/Procedure → Crafter Qualification → Tool/Workspace → Cost → Process → Validation → Resolution → Success/Partial/Failure → Quality → Result → Item State → Item Origin → History → Save → Write-Back Verify`

## Resolution
Resolusi mengikuti mekanik paling spesifik yang tersedia.
Hasil yang sah dapat berupa:
- Success
- Partial Success
- Failure
- Defective Result
- Material Loss/Damage

Tidak ada automatic success.
Jika source menyediakan success/failure check, gunakan source tersebut. Jika tidak, gunakan kemampuan/requirement yang telah ditetapkan Admin tanpa mengarang angka tersembunyi.

## Quality
Quality adalah hasil proses, bukan hadiah otomatis berdasarkan Realm Character.
- Quality ceiling mengikuti recipe/source bila tersedia.
- Material condition, tool, qualification, dan process hanya memengaruhi quality bila sistem/recipe menetapkannya.
- Tidak boleh menciptakan tier/quality baru hanya karena hasil terasa kuat.

## Failure
Failure dapat menghabiskan sebagian/seluruh material, waktu, resource, atau menghasilkan defective item jika didukung proses.
Failure tidak boleh diam-diam diubah menjadi success.

## Item Result
Setiap item baru harus memiliki identity/state sesuai Module 14 dan provenance yang dapat ditelusuri.
Minimum Origin:
`World Time / Entity ID / Action / Cause / Resolution / Before → After / Source`
Material yang dikonsumsi harus dapat ditelusuri ke Origin sebelumnya.

## Anti-Cheat
- Tidak ada crafting dari material yang tidak dimiliki.
- Tidak ada recipe/skill/tool/workspace gratis.
- Tidak ada instant mastery.
- Tidak ada guaranteed success.
- Tidak ada hidden time skip.
- Tidak ada automatic Realm scaling.
- Item hasil tidak otomatis memiliki ability/technique/effect yang tidak disumberkan.
- Dynamic recipe/result tidak menjadi Global Canon hanya karena muncul sekali.

## Persistence
Crafting lintas turn atau perubahan material/item yang material wajib melewati Save Pipeline. Current Item State, Character State, consumed materials, Origin, dan History yang terdampak harus diproses sebagai transaction yang konsisten.

## Runtime Contract
`ROUTER → REQUIRED SOURCES → INPUT VALIDATION → COST → PROCESS → RESOLUTION → RESULT VALIDATION → ITEM ORIGIN → STATE/HISTORY → SAVE → WRITE-BACK VERIFY`


## DATA COMPLETENESS PRODUCTION GATE
Recipe, blueprint, procedure, skill, qualification, tool, workspace, cost, quality, dan result hanya boleh berasal dari source yang sah atau mekanisme improvisasi yang secara eksplisit didukung source. Improvisasi yang sekadar membuat crafting berhasil dilarang. Missing required input → RESOLUTION-BLOCKED; unknown non-required field → status resmi.

## 14. ADMIN CANON — REGIONAL CRAFTING RECIPES

Recipe berikut dibuat karena masing-masing memiliki input regional yang jelas dan output yang mempunyai kegunaan lanjutan. Recipe bukan skill/qualification otomatis.

### RECIPE-CRAFT-001 — Tali Serat Cangyuan
- Input: ITEM-MAT-013 Serat Sungai Cangyuan ×2
- Tool: alat pemintal/anyam yang valid
- Process: pengeringan → pemintalan → pemilinan → pengikatan
- Output: ITEM-CRAFT-001 Tali Serat Cangyuan ×1
- Cost: seluruh input dikonsumsi; waktu proses mengikuti resolution produksi yang valid
- Quality: Basic bila seluruh requirement terpenuhi dan tidak ada failure

### RECIPE-CRAFT-002 — Mantel Kulit Dingin Beiming
- Input: ITEM-MAT-010 Kulit Dingin Beiming ×2 + ITEM-MAT-013 Serat Sungai Cangyuan ×1
- Tool: jarum/peralatan jahit yang valid
- Process: pemotongan → fitting → jahit → finishing
- Output: ITEM-EQP-001 Mantel Kulit Dingin ×1
- Effect: tidak menambahkan resistance numerik; fungsi pakaian dingin mengikuti equipment rules yang terpisah

### RECIPE-CRAFT-003 — Blank Giok Ukir
- Input: ITEM-MAT-012 Pecahan Giok Baiyu ×3
- Tool: alat pemotong/pemoles giok yang valid
- Process: sortir → pemotongan → perataan → pemolesan kasar
- Output: ITEM-CRAFT-002 Blank Giok Ukir ×1
- Purpose: input untuk recipe ukiran/formation yang kompatibel; tidak memberi efek formation otomatis

### RECIPE-CRAFT-004 — Manik Mutiara Dongming
- Input: ITEM-MAT-009 Mutiara Pasang Dongming ×1
- Tool: bor/pemoles material yang valid
- Process: pengeboran → pemolesan → finishing
- Output: ITEM-CRAFT-003 Manik Mutiara Dongming ×1
- Purpose: komponen aksesori/perdagangan; tidak menetapkan nilai pasar tetap

### RECIPE-CRAFT-005 — Lempeng Cangkang Lanyue
- Input: ITEM-MAT-014 Cangkang Karang Lanyue ×2
- Tool: alat potong/poles yang valid
- Process: pembersihan → pemotongan → perataan → finishing
- Output: ITEM-CRAFT-004 Lempeng Cangkang Lanyue ×1
- Purpose: komponen kerajinan; efek armor/defense harus berasal dari recipe/equipment source

### RECIPE-CRAFT-006 — Bilah Besi Huoyan
- Input: ITEM-MAT-001 Bijih Besi Kasar ×2 + ITEM-MAT-008 Terak Besi Api Huoyan ×1
- Tool: forge/workspace valid
- Process: peleburan → pemurnian → penempaan → pendinginan
- Output: ITEM-WPN-003 Bilah Besi Huoyan ×1
- Purpose: weapon dasar; quality ceiling dan performance mengikuti source produksi, bukan nama Huoyan saja

Semua recipe tunduk pada Module 31: material, recipe, qualification, tool/workspace, cost, time, validation, resolution, Origin dan Save tetap wajib.
