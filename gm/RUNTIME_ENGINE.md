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
- **Cultivation Law tidak boleh menjadi `ACTIVE` melalui improvisasi runtime; Law Acquisition wajib menghasilkan Law Origin yang tervalidasi.**
- **Technique tidak boleh menjadi aktif hanya karena Law dimiliki; Technique Origin harus divalidasi secara terpisah.**

## Runtime Pipeline
1. **FRESH FETCH** — fetch `INDEX.md` terlebih dahulu setiap turn.
2. **LOAD RULES** — ikuti Load Order; fetch Core, Custom/Event, System, Faction/Lore yang relevan. Jika NPC/Event/Quest relevan, wajib muat `systems/26_DYNAMIC_NPC_EVENT_QUEST.md` + `gm/NPC_EVENT_RUNTIME.md`. Jika encounter/Monster/Beast/Loot relevan, wajib muat `systems/25_DYNAMIC_GENERATION.md` dan modul terkait. Jika Law/Technique diperoleh atau berubah, wajib muat `systems/09_CULTIVATION.md` + `systems/15_TECHNIQUES.md`.
3. **STATE FETCH** — fetch Current Character State. Fetch Current Beast State/History bila Beast terlibat; Current NPC State/History bila NPC persistent terlibat; Current Quest State bila quest lintas-turn relevan.
4. **WORLD CONTEXT** — verifikasi World Time, lokasi, habitat, faction, event, Active Threads, dan informasi Character.
5. **INTENT PARSE** — identifikasi satu aksi utama.
6. **GENERATION GATE** — bila dynamic NPC/Event/Quest/Monster/Beast/Loot relevan, hitung hanya dengan formula Admin dan input yang tersedia; jangan memakai fallback tersembunyi.
7. **LAW/TECHNIQUE ORIGIN GATE** — bila aksi memperoleh/mengubah Law: resolve `SOURCE → ACQUISITION METHOD → REQUIREMENTS → TRAINING/INSIGHT → RESOLUTION`; bentuk Law Origin; validasi. Bila aksi memperoleh/mengubah Technique: resolve sumber/proses teknik; bentuk Technique Origin; jika berbasis Law, verifikasi Law aktif + Law Origin.
8. **VALIDATE** — jalankan State Validator dan validator sistem terkait. Law/Technique yang gagal provenance tidak boleh diterapkan sebagai aktif.
9. **COST** — terapkan waktu/resource hanya dari aturan resmi.
10. **RESOLVE** — hasil dapat sukses, gagal, sebagian berhasil, atau konsekuensi.
11. **REACTION** — proses NPC, event, faction, creature, Beast, dan lingkungan secara otonom sesuai state/agenda/trigger.
12. **STATE APPLY** — terapkan hanya perubahan yang dihasilkan resolusi pada entity yang tepat. Untuk Law/Technique, apply hanya status yang telah lolos Origin Gate.
13. **ORIGIN** — catat `World Time / Entity ID / Action/Event / Cause / Resolution / Before / After / Source` untuk perubahan material. Untuk Law, Before/After wajib mencakup Law + Law Origin; untuk Technique wajib mencakup Technique + Technique Origin.
14. **INTEGRITY** — validasi entity ID, scope, ownership/provenance, time, resource, memory isolation, reward provenance, Law/Technique provenance, dan Canon consistency.
15. **MEMORY** — update Character/NPC/Quest/Event/Beast history atau shared state hanya sesuai scope.
16. **SAVE** — gunakan `gm/SAVE_PIPELINE.md` untuk seluruh entity yang berubah.
17. **WRITE-BACK VERIFY** — commit dan verifikasi setiap state yang ditulis; jika gagal gunakan `PENDING SYNC`, jangan klaim sinkron.
18. **RESPONSE** — gunakan `gm/RESPONSE_FORMAT.md`.

## Dynamic Entity Routing
- NPC → Module 26 + `gm/NPC_EVENT_RUNTIME.md` + NPC State/History bila persistent.
- Local Event → Module 26 + Event/World/Thread context sesuai scope.
- World Event → registry Canon + trigger resmi; dynamic generator tidak mengganti trigger/scope/impact.
- Quest → Module 26 + Quest State bila lintas-turn + Active Threads bila shared.
- Monster/Spirit Beast/Loot → Module 25 + Module 13/18/24 sesuai relevansi.
- Quest reward → fixed Canon reward terlebih dahulu; jika tidak fixed, valid source Item/Economy/Technique/Contract atau Dynamic Loot sesuai modul. Tidak ada reward bebas.
- Cultivation Law → Module 09 + Law Origin Gate + State Validator.
- Technique → Module 15 + Technique Origin Gate + State Validator.

## Law/Technique Failure Handling
Jika source, acquisition method, requirements, training/insight, atau resolution yang diwajibkan tidak dapat dibuktikan, hasil Law/Technique adalah **not active** dan tidak boleh ditulis ke Character State sebagai kemampuan aktif. `???` digunakan hanya untuk fakta yang memang belum tersedia; jangan mengubah `???` menjadi fakta dengan tebakan.

## Anti-Stale / Failure
State chat sebelumnya bukan current repository state jika repository dapat diverifikasi. Jika required fetch gagal, tahan resolusi yang bergantung padanya atau tandai synchronization failure. Jika write-back gagal, pertahankan operational result sebagai `PENDING SYNC` sesuai `gm/PENDING_SYNC.md`.

## Priority
`Core/Admin/Custom → Dynamic System Rules → System Resolution → Realm/Lore/Faction → Current State → Persistent Memory → Player Intent`
