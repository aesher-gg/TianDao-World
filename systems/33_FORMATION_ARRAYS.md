# Module 33 — FORMATION & ARRAY

## Status
Admin Canon v1.2

## Purpose
Menetapkan sistem untuk blueprint, construction, activation, operation, disruption, damage, repair, dan destruction Formation/Array.

## Boundary
Module 33 mengatur Formation/Array sebagai struktur mekanis. Module 14 mengatur item/material state yang menjadi bagian dari formation. Module 12 mengatur combat resolution bila formation berinteraksi dengan combat. Module 09 mengatur cultivation/Qi cost bila source memang menghubungkannya.

## Core Principle
`Blueprint ≠ Construction ≠ Activation ≠ Operation`.

## Source Priority
`Canon/Admin → Fixed Formation/Blueprint Source → Current State → Valid Knowledge/Technique → Materials → Array Core → Location/Environment → Runtime Resolution`

## Canon Formation Registry
Baseline berikut tersedia sebagai blueprint Admin Canon. Blueprint tidak otomatis menjadi construction atau mastery.

### FORM-BP-001 — Formasi Penjaga Pintu Dasar
- Purpose: peringatan/pertahanan sederhana pada satu pintu atau jalur sempit.
- Materials: `ITEM-MAT-002` Kayu Keras Cangyuan ×4 + `ITEM-MAT-001` Bijih Besi Kasar ×1.
- Core: tidak wajib.
- Area: maksimal 2 Fen dari titik pemasangan.
- Activation: 1 operator dengan blueprint valid; membutuhkan pemasangan selesai.
- Effect: memberi tanda/alert ketika batas formasi terganggu; tidak memberikan automatic damage.
- Duration: selama struktur terpasang dan belum rusak; pemeriksaan state diperlukan tiap aktivasi.

### FORM-BP-002 — Formasi Pengumpul Cahaya Dasar
- Purpose: menyediakan pencahayaan area kerja kecil.
- Materials: `ITEM-MAT-002` Kayu Keras Cangyuan ×2 + `ITEM-MAT-001` Bijih Besi Kasar ×1.
- Core: tidak wajib.
- Area: maksimal 3 Fen dari titik pusat.
- Activation: operator dengan blueprint valid dan resource yang diperlukan.
- Effect: penerangan area; tidak memberi bonus combat atau cultivation.
- Duration: satu periode operasi sampai resource/condition yang berlaku habis.

### FORM-BP-003 — Formasi Penahan Angin Dasar
- Purpose: mengurangi gangguan angin pada area kerja terbatas.
- Materials: `ITEM-MAT-002` Kayu Keras Cangyuan ×6 + `ITEM-MAT-005` Serat Rami ×2.
- Core: tidak wajib.
- Area: maksimal 5 Fen dari titik pusat.
- Activation: operator dengan blueprint valid.
- Effect: membatasi gangguan angin biasa di dalam area; tidak menetralisir badai atau fenomena spiritual.
- Duration: satu periode operasi; tidak unlimited.

## Required Components
1. Blueprint/procedure valid.
2. Operator/builder dengan knowledge yang sah.
3. Materials yang valid.
4. Array Core bila blueprint membutuhkannya.
5. Lokasi/area sesuai.
6. Resource cost.
7. Construction/activation process.

## Formation Identity & Persistence
Formation persisten menggunakan `FORM-####`; Array Core persisten menggunakan `ARRAYCORE-####`.
- Current Formation State: `formations/FORM-####.md`
- Current Array Core State: `formations/cores/ARRAYCORE-####.md`
- Registry: `formations/formation_registry.md`
- History: `formation_history/FORM-####_HISTORY.md` dan `formation_history/ARRAYCORE-####_HISTORY.md` bila continuity material memerlukannya.

## Formation State
`Blueprint Only → Unconstructed → Constructing → Constructed/Inactive → Active → Damaged/Disrupted → Collapsed/Destroyed`

## Construction
Construction mengonsumsi material, waktu, dan resource sesuai blueprint/source. Failure dapat menghasilkan incomplete, damaged, atau failed formation.

## Array Core
Array Core adalah komponen terpisah bila formation membutuhkannya. Core harus mempunyai Origin dan tidak muncul gratis.

## Activation
Activation membutuhkan semua requirement yang berlaku. Formation terpasang tidak otomatis aktif.

## Operation
Formation aktif memiliki state yang dapat berubah melalui cost, duration, damage, disruption, atau kondisi yang didukung source.

## Cost
Cost hanya berasal dari blueprint/source atau resource rule resmi. Tidak ada numeric cost tersembunyi.

## Range & Effect
Range/effect baseline untuk tiga blueprint Canon di atas sudah ditetapkan pada registry. Formation lain yang belum memiliki blueprint Canon tetap menggunakan `UNRESOLVED` dan tidak boleh diberi effect mekanis secara asumtif.

## Disruption & Failure
Formation dapat gagal, terganggu, rusak, dinonaktifkan, runtuh, atau dihancurkan jika mekanisme/source memungkinkan.

## Formation Combat Interaction
Jika Formation memengaruhi combat:
`Formation State → Valid Effect → Combat Module → Resolution → Formation/Combat Consequence`.

Tidak ada automatic hit/kill/dodge/counter yang tidak disumberkan.

## Repair
Repair adalah perubahan state. Material, tool, skill, time, dan result harus valid. Repair tidak otomatis memulihkan kondisi sempurna.

## Origin
Construction, activation, modification, disruption, repair, collapse, dan destruction yang material wajib memiliki:
`World Time / Entity ID / Action/Event / Cause / Resolution / Before → After / Source`.

## Anti-Cheat
- Tidak ada blueprint/formation gratis.
- Tidak ada Array Core gratis.
- Tidak ada automatic activation.
- Tidak ada unlimited duration.
- Tidak ada automatic high-level formation karena Realm.
- Tidak ada effect/range/cost yang diimprovisasi sebagai fakta.
- Tidak ada hidden time skip.
- Dynamic formation tidak menjadi Global Canon hanya karena muncul runtime.

## Persistence
Formation material atau lintas turn harus mempunyai identity/state yang dapat dilacak dan diproses melalui Save Pipeline.

## Runtime Contract
`ROUTER → REQUIRED SOURCES → COMPONENT VALIDATION → CONSTRUCTION/ACTIVATION CHECK → COST → RESOLUTION → EFFECT/DAMAGE → ORIGIN → STATE/HISTORY → SAVE → VERIFY`


## DATA COMPLETENESS FORMATION GATE
Blueprint, material, core, operator qualification, range, effect, cost, stability, dan activation state wajib memiliki source sah. Jangan mengarang parameter untuk membuat formasi aktif. Jika required parameter tidak tersedia, tahan resolusi sebagai RESOLUTION-BLOCKED.
