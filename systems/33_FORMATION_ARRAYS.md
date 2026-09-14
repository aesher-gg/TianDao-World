# Module 33 — FORMATION & ARRAY

## Status
Admin Canon v1.0

## Purpose
Menetapkan sistem untuk blueprint, construction, activation, operation, disruption, damage, repair, dan destruction Formation/Array.

## Boundary
Module 33 mengatur Formation/Array sebagai struktur mekanis. Module 14 mengatur item/material state yang menjadi bagian dari formation. Module 12 mengatur combat resolution bila formation berinteraksi dengan combat. Module 09 mengatur cultivation/Qi cost bila source memang menghubungkannya.

## Core Principle
`Blueprint ≠ Construction ≠ Activation ≠ Operation`.
Memiliki blueprint tidak berarti Character mampu membangun atau mengoperasikan formation.

## Source Priority
`Canon/Admin → Fixed Formation/Blueprint Source → Current State → Valid Knowledge/Technique → Materials → Array Core → Location/Environment → Runtime Resolution`

Jika input mekanis wajib tidak diketahui dan tidak ada fallback resmi, gunakan `???` atau tahan resolusi.

## Required Components
1. Formation blueprint/procedure yang valid.
2. Operator/builder dengan knowledge yang sah.
3. Array materials yang valid.
4. Array Core bila formation membutuhkannya.
5. Lokasi/area yang sesuai.
6. Resource cost.
7. Construction/activation process.

## Blueprint
Blueprint dapat berasal dari Canon, manual, teacher, faction, item, event, discovery yang benar-benar terjadi, atau Admin Canon.
- Blueprint tidak otomatis memberikan mastery.
- Effect, range, cost, stability, requirements, dan disruption rules hanya digunakan jika source mendefinisikannya.

## Formation State
`Blueprint Only → Unconstructed → Constructing → Constructed/Inactive → Active → Damaged/Disrupted → Collapsed/Destroyed`
State harus mencerminkan resolusi aktual, bukan intent Player.

## Construction
Construction mengonsumsi material, waktu, dan resource hanya sesuai source.
Kualitas konstruksi tidak boleh diada-adakan tanpa mekanisme yang mendukungnya.
Construction failure dapat menghasilkan incomplete, damaged, atau failed formation bila valid.

## Array Core
Array Core adalah komponen terpisah jika formation membutuhkannya.
- Core harus mempunyai Origin.
- Core memiliki state/condition yang dapat berubah.
- Core tidak muncul gratis.
- Memiliki Core tidak otomatis berarti memiliki Formation.

## Activation
Activation membutuhkan semua requirement yang berlaku. Activation dapat membutuhkan operator, Qi, fuel, item, timing, location, atau trigger resmi.
Formation terpasang tidak otomatis aktif.

## Operation
Saat aktif, formation memiliki state yang dapat berubah melalui cost, duration, damage, disruption, atau kondisi lain yang benar-benar didukung source.
Tidak ada automatic unlimited duration.

## Cost
Cost dapat berupa Qi, stamina, material/fuel, currency, durability, operator attention, atau resource lain bila ditentukan.
Jangan membuat numeric cost tersembunyi.

## Range & Effect
Range dan effect harus berasal dari Formation source atau Admin Canon.
Tidak boleh memperluas range/effect hanya karena Realm operator lebih tinggi.
Jika range/effect tidak diketahui: `???`.

## Disruption & Failure
Formation dapat gagal, terganggu, rusak, dinonaktifkan, runtuh, atau dihancurkan jika mekanisme/source memungkinkan.
Combat disruption memakai Module 12 bila menjadi combat resolution.
Tidak ada automatic immunity hanya karena formation adalah milik Character/faction.

## Formation Combat Interaction
Jika Formation memengaruhi combat:
`Formation State → Valid Effect → Combat Module → Resolution → Formation/Combat Consequence`.
Formation tidak menggantikan combat rules dan tidak memberikan automatic hit/kill/dodge/counter yang tidak disumberkan.

## Repair
Repair adalah perubahan state pada Formation/Array Core. Material, tool, skill, time, dan result harus valid. Repair tidak otomatis memulihkan formation ke kondisi sempurna tanpa dasar.

## Origin
Construction, activation, modification, disruption, repair, collapse, dan destruction yang material harus memiliki:
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
Formation yang material atau lintas turn harus mempunyai identity/state yang dapat dilacak. Semua entity yang berubah, termasuk Character, Formation, Array Core, consumed materials, dan shared location state bila relevan, diproses melalui Save Pipeline.

## Runtime Contract
`ROUTER → REQUIRED SOURCES → COMPONENT VALIDATION → CONSTRUCTION/ACTIVATION CHECK → COST → RESOLUTION → EFFECT/DAMAGE → ORIGIN → STATE/HISTORY → SAVE → VERIFY`
