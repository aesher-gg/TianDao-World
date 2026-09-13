# Runtime Action Resolver

## Pipeline
`Intent → Context → Dynamic Generation (if relevant) → Validation → Cost → Resolution → Consequence/Reaction → Log → Integrity → Memory → Save/Write-Back`

## 1. Intent
Identifikasi satu aksi utama. Dalam situasi kritis, proses satu aksi utama terlebih dahulu.

## 2. Context
Muat World Time, lokasi, kondisi, target, kemampuan, resource, equipment, inventory, Character Knowledge, faction, event, Active Threads, history, dan modul relevan. Jika NPC/Event/Quest terlibat, muat Module 26 + `gm/NPC_EVENT_RUNTIME.md`. Jika Monster/Beast/Loot terlibat, muat Module 25 + modul terkait.

## 3. Dynamic Generation Gate
Jika konten belum fixed/Canon dan memang dibutuhkan runtime:
- NPC → Social Activity + Module 26.
- Local Event → Local Event Pressure + Module 26.
- Quest → Quest Generation Gate + Module 26.
- Monster/Beast/Loot → Module 25.
Generated result bukan otomatis Canon. Jangan membuat entity hanya untuk membenarkan Player intent.

## 4. Validation
Jalankan `STATE_VALIDATOR.md`. Pastikan fixed content memakai source fixed; dynamic content memakai formula/inputs yang sah; ID persistent unik/stabil; scope event benar; quest reward punya provenance; dan tidak ada hidden numeric fallback.

## 5. Cost
Gunakan biaya resmi untuk waktu, stamina, Qi, currency, item, durability, hunger, perjalanan, atau resource lain. Jangan membuat angka baru hanya agar aksi berjalan.

## 6. Resolution
Gunakan mekanik paling spesifik. Hasil dapat sukses, gagal, sebagian berhasil, atau sukses dengan konsekuensi. NPC dapat menolak/berbohong/gagal/pergi; event dapat tidak terjadi; quest dapat gagal/expired. Character Realm tidak otomatis menskalakan NPC, Event, Quest, difficulty, atau reward.

## 7. Consequence / Reaction
Proses konsekuensi terhadap Character, NPC, Event, Quest, faction, environment, Monster, dan Spirit Beast sesuai autonomy, agenda, trigger, knowledge, habitat, dan current state.

## 8. Log
Setiap perubahan material: `World Time / Entity ID / Action/Event / Cause / Resolution / Before → After / Source`. Untuk multi-entity transaction, log seluruh entity yang berubah.

## 9. Integrity
Jalankan State Validator sebelum state dianggap sah. Pastikan quest reward benar-benar diperoleh melalui resolusi yang valid dan provenance tercatat.

## 10. Memory
Setelah PASS, simpan hanya fakta material. Character History, NPC History, Quest State, Event/World State, Beast History, dan Active Threads harus mengikuti entity/scope masing-masing.

## 11. Save / Write-Back
Gunakan `SAVE_PIPELINE.md`. Semua entity yang berubah harus diproses. Jika write-back gagal, gunakan `PENDING SYNC`; jangan mengklaim save tersinkron.

## Special Rules
- Non-kultivasi maksimal 3 jam/turn.
- Tidak ada hidden time skip.
- Permanent death hanya jika mekanisme resmi berlaku.
- Generated ≠ Canon; persistence ≠ Global Canon.
- NPC_ID/QST_ID/EVT_ID/BEAST_ID unik dan stabil serta tidak dipakai ulang.
