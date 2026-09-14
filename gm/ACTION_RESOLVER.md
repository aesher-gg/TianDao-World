# Runtime Action Resolver

## Pipeline
`Fresh INDEX → Module Router → Intent → Context → Required Modules → Dynamic Generation → Validation → Cost → Resolution → Consequence/Reaction → Origin/Log → Integrity → Memory → Save → Write-Back Verify`

## 1. Fresh INDEX & Routing
Fetch `INDEX.md` first. Jalankan `systems/27_MODULE_ROUTER.md`. Semua REQUIRED module harus berhasil dimuat sebelum resolusi yang bergantung padanya. Tidak ada silent fallback.

## 2. Intent
Identifikasi satu aksi utama. Dalam situasi kritis, proses satu aksi utama terlebih dahulu.

## 3. Context
Muat World Time, lokasi, kondisi, target, kemampuan, resource, equipment, inventory, Character Knowledge, faction, event, Active Threads, history, dan modul relevan. NPC/Event/Quest → Module 26 + runtime. Monster/Beast/Loot → Module 25 + modul terkait.

## 4. Dynamic Generation Gate
Jika konten belum fixed/Canon dan memang dibutuhkan runtime:
- NPC → Social Activity + Module 26.
- Local Event → Local Event Pressure + Module 26.
- Quest → Quest Generation Gate + Module 26.
- Monster/Beast/Loot → Module 25.
Generated result bukan otomatis Canon dan tidak boleh dibuat hanya untuk membenarkan intent.

## 5. Production Routing Gate
Jika intent adalah produksi/perubahan produksi:
- Crafting/Forging/Smithing/material processing/new item → Module 31.
- Alchemy/Pill → Module 32.
- Formation/Array construction/activation/operation/disruption/repair → Module 33.
- Existing artifact/weapon/item refinement/temper/upgrade → Module 34.
Jika proses lintas modul, semua REQUIRED module diproses. Module 14 Items tetap wajib ketika Item State/identity/ownership/condition/quality/inventory/equipment berubah.

## 6. Validation
Jalankan `STATE_VALIDATOR.md`. Pastikan fixed content memakai source fixed; dynamic content memakai formula/input sah; ID persistent unik/stabil; scope benar; reward provenance valid; organization detail mengikuti database/individual file; tidak ada hidden numeric fallback.
Untuk production, validasi material, source recipe/formula/blueprint/method, qualification, tool/workspace/furnace, cost, process, result, quality/effect/property, provenance, dan cross-entity before → after sesuai Module 31–34.

## 7. Cost
Gunakan biaya resmi untuk waktu, stamina, Qi, currency, item, durability, hunger, perjalanan, material, fuel, tool/workspace, atau resource lain. Jangan membuat angka baru hanya agar aksi berjalan.

## 8. Resolution
Gunakan mekanik paling spesifik. Hasil dapat sukses, gagal, sebagian berhasil, atau sukses dengan konsekuensi. NPC dapat menolak/berbohong/gagal/pergi. Event dapat tidak terjadi. Quest dapat gagal/expired. Production dapat menghasilkan success, partial success, failure, defective result, damage, atau loss bila modul terkait mengizinkannya. Character Realm tidak otomatis menskalakan NPC, Event, Quest, difficulty, reward, quality, atau production success.

## 9. Production Result Rules
- Module 31 membuat item baru atau hasil material processing yang sah.
- Module 32 menghasilkan Pill/Alchemy Product dengan effect/quality/quantity hanya dari formula/source yang valid.
- Module 33 menghasilkan/mengubah Formation/Array state dan tidak menggantikan Combat/Cultivation rules.
- Module 34 mengubah existing Item State; tidak otomatis menaikkan category/grade/tier.
- Tidak ada automatic success, free material, free recipe, free qualification, hidden modifier, atau effect/ability yang tidak disumberkan.

## 10. Consequence / Reaction
Proses konsekuensi terhadap Character, NPC, Event, Quest, faction, environment, Monster, Spirit Beast, Item, Material, Formation, dan Array Core sesuai autonomy, agenda, trigger, knowledge, habitat, current state, dan production resolution.

## 11. Origin / Log
Setiap perubahan material: `World Time / Entity ID / Action/Event / Cause / Resolution / Before → After / Source`. Multi-entity transaction wajib mencatat seluruh entity yang berubah.
Production chain harus mempertahankan provenance dari input → process → result. Existing Item Origin tidak dihapus saat refinement; Origin baru ditambahkan untuk perubahan tersebut.

## 12. Integrity
Jalankan State Validator. Pastikan ownership, provenance, scope, ID, time, resource, memory isolation, reward, Law/Technique, organization state, Item State, production result, dan cross-entity transaction sah.

## 13. Memory
Setelah PASS, simpan hanya fakta material ke Character History, NPC History, Quest State, Event/World State, Beast History, Active Threads, dan state/history production entity sesuai entity/scope.

## 14. Save / Write-Back
Gunakan `SAVE_PIPELINE.md`. Semua entity yang berubah harus diproses. Jika write-back gagal → `PENDING SYNC`; jangan mengklaim Repository Saved.

## Special Rules
- Non-kultivasi maksimal 3 jam/turn.
- Tidak ada hidden time skip.
- Permanent death hanya jika mekanisme resmi berlaku.
- Generated ≠ Canon; persistence ≠ Global Canon.
- NPC_ID/QST_ID/EVT_ID/BEAST_ID unik dan stabil serta tidak dipakai ulang.
- Production result tidak menjadi Global Canon hanya karena muncul runtime.
