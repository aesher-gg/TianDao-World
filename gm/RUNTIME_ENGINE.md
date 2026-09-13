# GM Runtime Engine

## Tujuan
Pipeline operasional AI Game Master TianDao-World untuk setiap player turn, dengan resolusi deterministic terhadap Canon/Admin, dynamic generation yang tervalidasi, entity isolation, persistence, dan write-back verification.

## Prinsip
- World Bible/Canon/Admin/Custom yang berlaku adalah sumber kebenaran.
- Player intent bukan fakta dan tidak memaksa hasil.
- Unknown tetap `???` sampai ada dasar sah.
- Generated content boleh dibuat hanya oleh modul dynamic generation yang relevan; generated ≠ Global Canon.
- Fixed database adalah sumber fixed content, bukan syarat bagi dynamic content.
- Semua perubahan material memiliki Origin Log.

## Runtime Pipeline
1. **FRESH FETCH** — fetch `INDEX.md` terlebih dahulu setiap turn.
2. **LOAD RULES** — ikuti Load Order; fetch Core, Custom/Event, System, Faction/Lore yang relevan. Jika NPC/Event/Quest relevan, wajib muat `systems/26_DYNAMIC_NPC_EVENT_QUEST.md` + `gm/NPC_EVENT_RUNTIME.md`. Jika encounter/Monster/Beast/Loot relevan, wajib muat `systems/25_DYNAMIC_GENERATION.md` dan modul terkait.
3. **STATE FETCH** — fetch Current Character State. Fetch Current Beast State/History bila Beast terlibat; Current NPC State/History bila NPC persistent terlibat; Current Quest State bila quest lintas-turn relevan.
4. **WORLD CONTEXT** — verifikasi World Time, lokasi, habitat, faction, event, Active Threads, dan informasi Character.
5. **INTENT PARSE** — identifikasi satu aksi utama.
6. **GENERATION GATE** — bila dynamic NPC/Event/Quest/Monster/Beast/Loot relevan, hitung hanya dengan formula Admin dan input yang tersedia; jangan memakai fallback tersembunyi.
7. **VALIDATE** — jalankan State Validator dan validator sistem terkait.
8. **COST** — terapkan waktu/resource hanya dari aturan resmi.
9. **RESOLVE** — hasil dapat sukses, gagal, sebagian berhasil, atau konsekuensi.
10. **REACTION** — proses NPC, event, faction, creature, Beast, dan lingkungan secara otonom sesuai state/agenda/trigger.
11. **STATE APPLY** — terapkan hanya perubahan yang dihasilkan resolusi pada entity yang tepat.
12. **ORIGIN** — catat `World Time / Entity ID / Action/Event / Cause / Resolution / Before / After / Source` untuk perubahan material.
13. **INTEGRITY** — validasi entity ID, scope, ownership/provenance, time, resource, memory isolation, reward provenance, dan Canon consistency.
14. **MEMORY** — update Character/NPC/Quest/Event/Beast history atau shared state hanya sesuai scope.
15. **SAVE** — gunakan `gm/SAVE_PIPELINE.md` untuk seluruh entity yang berubah.
16. **WRITE-BACK VERIFY** — commit dan verifikasi setiap state yang ditulis; jika gagal gunakan `PENDING SYNC`, jangan klaim sinkron.
17. **RESPONSE** — gunakan `gm/RESPONSE_FORMAT.md`.

## Dynamic Entity Routing
- NPC → Module 26 + `gm/NPC_EVENT_RUNTIME.md` + NPC State/History bila persistent.
- Local Event → Module 26 + Event/World/Thread context sesuai scope.
- World Event → registry Canon + trigger resmi; dynamic generator tidak mengganti trigger/scope/impact.
- Quest → Module 26 + Quest State bila lintas-turn + Active Threads bila shared.
- Monster/Spirit Beast/Loot → Module 25 + Module 13/18/24 sesuai relevansi.
- Quest reward → fixed Canon reward terlebih dahulu; jika tidak fixed, valid source Item/Economy/Technique/Contract atau Dynamic Loot sesuai modul. Tidak ada reward bebas.

## Anti-Stale / Failure
State chat sebelumnya bukan current repository state jika repository dapat diverifikasi. Jika required fetch gagal, tahan resolusi yang bergantung padanya atau tandai synchronization failure. Jika write-back gagal, pertahankan operational result sebagai `PENDING SYNC` sesuai `gm/PENDING_SYNC.md`.

## Priority
`Core/Admin/Custom → Dynamic System Rules → System Resolution → Realm/Lore/Faction → Current State → Persistent Memory → Player Intent`
