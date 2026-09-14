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

## 5. Validation
Jalankan `STATE_VALIDATOR.md`. Pastikan fixed content memakai source fixed; dynamic content memakai formula/input sah; ID persistent unik/stabil; scope benar; reward provenance valid; organization detail mengikuti database/individual file; tidak ada hidden numeric fallback.

## 6. Cost
Gunakan biaya resmi untuk waktu, stamina, Qi, currency, item, durability, hunger, perjalanan, atau resource lain. Jangan membuat angka baru hanya agar aksi berjalan.

## 7. Resolution
Gunakan mekanik paling spesifik. Hasil dapat sukses, gagal, sebagian berhasil, atau sukses dengan konsekuensi. NPC dapat menolak/berbohong/gagal/pergi. Event dapat tidak terjadi. Quest dapat gagal/expired. Character Realm tidak otomatis menskalakan NPC, Event, Quest, difficulty, atau reward.

## 8. Consequence / Reaction
Proses konsekuensi terhadap Character, NPC, Event, Quest, faction, environment, Monster, dan Spirit Beast sesuai autonomy, agenda, trigger, knowledge, habitat, dan current state.

## 9. Origin / Log
Setiap perubahan material: `World Time / Entity ID / Action/Event / Cause / Resolution / Before → After / Source`. Multi-entity transaction wajib mencatat seluruh entity yang berubah.

## 10. Integrity
Jalankan State Validator. Pastikan ownership, provenance, scope, ID, time, resource, memory isolation, reward, Law/Technique, dan organization state sah.

## 11. Memory
Setelah PASS, simpan hanya fakta material ke Character History, NPC History, Quest State, Event/World State, Beast History, dan Active Threads sesuai entity/scope.

## 12. Save / Write-Back
Gunakan `SAVE_PIPELINE.md`. Semua entity yang berubah harus diproses. Jika write-back gagal → `PENDING SYNC`; jangan mengklaim Repository Saved.

## Special Rules
- Non-kultivasi maksimal 3 jam/turn.
- Tidak ada hidden time skip.
- Permanent death hanya jika mekanisme resmi berlaku.
- Generated ≠ Canon; persistence ≠ Global Canon.
- NPC_ID/QST_ID/EVT_ID/BEAST_ID unik dan stabil serta tidak dipakai ulang.
