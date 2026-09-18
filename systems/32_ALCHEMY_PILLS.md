# Module 32 — ALCHEMY & PILL REFINEMENT

## Status
Admin Canon v1.2

## Purpose
Menetapkan pipeline khusus untuk memproses herb/material menjadi Pill atau produk alkimia melalui formula, alchemist qualification, furnace, preparation, refinement, dan validated resolution.

## Boundary
- Module 32 menangani Alchemy, Pill Refinement, dan hasil alkimia.
- Module 31 menangani crafting/forging umum.
- Module 34 menangani refinement item/artifact/weapon yang sudah ada.
- Module 14 tetap menjadi sumber state/identity item hasil alchemy. Seluruh output `ITEM-ALC-*` yang ditetapkan oleh formula wajib memiliki identity di `systems/14_ITEMS.md` §4D sebelum dapat diperlakukan sebagai output production yang sah.

## Source Priority
`Canon/Admin → Fixed Formula/Pill Source → Current State → Valid Material Origin → Alchemist Qualification → Furnace/Tool → Runtime Resolution`

## Required Inputs
1. Herb/material yang valid.
2. Formula/recipe/prosedur yang valid.
3. Alchemist dengan qualification yang sah.
4. Furnace/tool yang dibutuhkan.
5. Resource cost.
6. Waktu/proses.
7. Kondisi bahan yang relevan.

## Canon Formula Registry
Formula dasar berikut adalah formula Admin Canon dan dapat diajarkan/disalin hanya melalui Origin yang sah.

### FORMULA-ALC-001 — Bubuk Penjernih Dasar
- Input: `ITEM-HERB-001` Rumput Embun Pagi ×2.
- Tool: mortar/penggiling bersih; furnace tidak wajib.
- Process: keringkan → tumbuk → ayak.
- Output: 1 unit bubuk herbal dasar.
- Effect: tidak menetapkan efek combat/medis baru; digunakan sebagai bahan proses.
- Cost: bahan input dikonsumsi; waktu proses minimal 30 menit.

### FORMULA-ALC-002 — Pil Penetral Racun Dasar
- Input: `ITEM-HERB-001` Rumput Embun Pagi ×2 + `ITEM-HERB-002` Rumput Jarum Beracun ×1.
- Tool: furnace alkimia sederhana.
- Process: ekstraksi → pemurnian → kondensasi → pendinginan.
- Output: 1 `ITEM-CONS-002` Pil Penetral Racun Dasar.
- Effect: hanya menangani racun dasar; tidak menetapkan efektivitas terhadap racun tingkat tinggi.
- Failure: bahan dapat hilang atau produk menjadi cacat bila proses gagal.
- Cost: seluruh input dikonsumsi pada resolusi.

### FORMULA-ALC-003 — Salep Penghenti Darah Dasar
- Input: `ITEM-HERB-001` Rumput Embun Pagi ×2 + `ITEM-MAT-005` Serat Rami ×1.
- Tool: wadah pemrosesan bersih; pemanasan ringan.
- Process: ekstraksi → pencampuran → pemanasan → pendinginan.
- Output: 1 `ITEM-CONS-001` Bubuk/produk penghenti darah dasar sesuai Item State.
- Effect: hanya fungsi penghentian perdarahan ringan yang sudah ditetapkan Item Canon.
- Cost: seluruh input dikonsumsi pada resolusi.

Formula di atas tidak otomatis memberi Character mastery. Knowledge formula dan qualification tetap membutuhkan Origin.

## Alchemist Qualification
Qualification harus memiliki Origin melalui training, teacher, manual, faction, experience, event, atau source resmi lain.
- Sekali mencoba tidak otomatis memberi mastery.
- Realm Character tidak otomatis menentukan alchemy skill.
- Alchemist tidak otomatis mampu membuat semua formula yang diketahui.

## Furnace & Process
Furnace adalah tool produksi. Preparation, heating, extraction, mixing, condensation, refinement, cooling, dan tahap lain hanya berlaku jika formula/proses mendukungnya.

## Resource & Cost
Cost dapat berupa herb, material, fuel, waktu, stamina, Qi, currency, furnace durability, atau biaya workshop/laboratory bila ditentukan. Tidak ada bahan atau resource gratis.

## Alchemy Pipeline
`Herb/Material → Formula → Alchemist Qualification → Furnace/Tool → Preparation → Refinement Process → Validation → Resolution → Failure/Deviation/Success → Pill Quality → Quantity → Effect → Defect/Side Effect → Item Origin → History → Save → Write-Back Verify`

## Resolution
Hasil yang sah: Success, Partial Success, Failure, Defective Pill/Product, atau Material Loss/Damage.

Jika formula atau sistem menyediakan check, gunakan check tersebut. Jika tidak, gunakan requirement dan process validity yang tersedia; jangan mengarang probabilitas numerik tersembunyi.

## Pill Quality
Untuk formula Canon di atas, kualitas default adalah **Basic** bila seluruh requirement terpenuhi dan tidak ada failure. Kualitas lebih tinggi tidak diberikan tanpa source/qualification/proses yang menetapkannya.

## Quantity
Quantity mengikuti formula: setiap formula di atas menghasilkan 1 unit output per successful batch. Batch tambahan membutuhkan input tambahan dan resolusi tambahan.

## Effect & Defect
Efek, potency, duration, side effect, toxicity, atau defect harus memiliki source mekanis yang valid. Formula baseline di atas hanya memakai efek yang secara eksplisit tercantum; tidak ada efek tersembunyi.

## Failure
Failure dapat merusak/meniadakan bahan, menghabiskan resource, atau menghasilkan produk cacat bila proses mendukungnya. Kegagalan tidak boleh diam-diam menjadi Pill sukses.

## Item Origin
Pill/product yang berhasil dibuat menjadi Item State menurut Module 14 dan wajib memiliki provenance:
`World Time / Entity ID / Action / Cause / Resolution / Before → After / Source`

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


## DATA COMPLETENESS ALCHEMY GATE
Formula, material, qualification, tool, cost, quality, quantity, effect, potency, side effect, dan defect wajib bersumber dari formula/procedure/state yang sah. Jangan menciptakan effect atau angka untuk melengkapi hasil. Missing required source/input → RESOLUTION-BLOCKED; unknown field → status resmi.

## 11. ADMIN CANON — REGIONAL ALCHEMY MATERIAL PATHS

Path berikut memperluas fungsi item regional tanpa menciptakan efek medis tersembunyi.

### FORMULA-ALC-004 — Bubuk Pengawet Getah Qingluan
- Input: ITEM-MAT-007 Getah Pinus Roh Qingluan ×1 + ITEM-HERB-001 Rumput Embun Pagi ×1
- Tool: mortar/penggiling bersih; pemanasan ringan
- Process: pengeringan → penggilingan → pencampuran → pengeringan akhir
- Output: ITEM-ALC-001 Bubuk Pengawet Qingluan ×1
- Effect: bahan proses pengawetan; tidak memberi buff atau durability bonus otomatis
- Cost: input dikonsumsi pada successful resolution

### FORMULA-ALC-005 — Bubuk Jamur Kabut Wuyin
- Input: ITEM-HERB-003 Jamur Kabut Wuyin ×2
- Tool: alat pengering dan penggiling bersih
- Process: pengeringan → pemilahan → penggilingan → penyimpanan kedap
- Output: ITEM-ALC-002 Bubuk Jamur Wuyin ×1
- Effect: bahan alchemy/obat untuk formula lain yang secara eksplisit menerima bahan ini; tidak memberi efek ketika hanya disimpan
- Cost: input dikonsumsi pada successful resolution

### FORMULA-ALC-006 — Sirup Madu Seratus Bunga
- Input: ITEM-HERB-004 Madu Seratus Bunga ×1
- Tool: wadah proses bersih
- Process: penyaringan → pemanasan ringan → pendinginan
- Output: ITEM-ALC-003 Sirup Madu Seratus Bunga ×1
- Effect: bahan consumable/alchemy; tidak menetapkan pemulihan HP/Qi numerik
- Cost: input dikonsumsi pada successful resolution

### 11.1 Output Identity
- ITEM-ALC-001 Bubuk Pengawet Qingluan — Alchemy Material.
- ITEM-ALC-002 Bubuk Jamur Wuyin — Alchemy Material.
- ITEM-ALC-003 Sirup Madu Seratus Bunga — Consumable/Alchemy Material.

Semua formula tetap membutuhkan qualification, tool, process, resource cost, resolution, Origin, History, dan Save sesuai Module 32.
