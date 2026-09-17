# GM Runtime Engine

## Tujuan
Pipeline operasional AI Game Master TianDao-World untuk setiap player turn, dengan resolusi deterministic terhadap Canon/Admin, dynamic generation yang tervalidasi, entity isolation, persistence, dan write-back verification.

## Prinsip
- World Bible/Canon/Admin/Custom yang berlaku adalah sumber kebenaran.
- Player intent bukan fakta dan tidak memaksa hasil.
- Status data yang belum tersedia menggunakan token resmi `UNRESOLVED`, bukan asumsi atau angka pengganti.
- Generated content boleh dibuat hanya oleh modul dynamic generation yang relevan; generated ≠ Global Canon.
- Fixed database adalah sumber fixed content, bukan syarat bagi dynamic content.
- Semua perubahan material memiliki Origin Log.
- Cultivation Law tidak boleh menjadi `ACTIVE` melalui improvisasi runtime; Law Acquisition wajib menghasilkan Law Origin yang tervalidasi.
- Technique tidak boleh menjadi aktif hanya karena Law dimiliki; Technique Origin harus divalidasi secara terpisah.

## Modular Router Gate
Setelah `INDEX.md` berhasil di-fetch, engine wajib menjalankan `systems/27_MODULE_ROUTER.md` sebelum resolusi.
1. Deteksi trigger dari intent + context.
2. Tentukan modul REQUIRED dan OPTIONAL.
3. Fetch seluruh REQUIRED module sebelum validation/resolution.
4. Jika REQUIRED module gagal, tahan resolusi yang bergantung padanya.
5. Jangan memuat seluruh World Bible tanpa kebutuhan runtime.

## Runtime Pipeline
1. **FRESH FETCH** — fetch `INDEX.md` terlebih dahulu setiap turn.
2. **LOAD RULES** — ikuti Load Order dan Module Router; fetch Core, Custom/Event, System, Faction/Lore yang relevan.
3. **STATE FETCH** — fetch Current Character State. Fetch Current Beast/NPC/Quest State dan History bila entity persistent relevan.
4. **WORLD CONTEXT** — verifikasi World Time, lokasi, habitat, faction, event, Active Threads, dan Character information.
5. **TRIGGER ROUTING** — jalankan Module 27 dan pastikan REQUIRED modules tersedia.
6. **INTENT PARSE** — identifikasi satu aksi utama.
7. **GENERATION GATE** — dynamic NPC/Event/Quest/Monster/Beast/Loot hanya memakai formula Admin dan input tersedia.
8. **LAW/TECHNIQUE ORIGIN GATE** — validasi source, acquisition, requirements, training/insight, resolution, dan provenance.
9. **VALIDATE** — jalankan State Validator dan validator sistem terkait.
10. **COST** — terapkan waktu/resource hanya dari aturan resmi.
11. **RESOLVE** — hasil dapat sukses, gagal, sebagian berhasil, atau konsekuensi.
12. **REACTION** — proses NPC, event, faction, creature, Beast, dan lingkungan sesuai state/agenda/trigger.
13. **STATE APPLY** — terapkan hanya perubahan yang dihasilkan resolusi pada entity yang tepat.
14. **ORIGIN** — catat `World Time / Entity ID / Action/Event / Cause / Resolution / Before / After / Source`.
15. **INTEGRITY** — validasi ID, scope, ownership/provenance, time, resource, memory isolation, reward provenance, dan Canon consistency.
16. **MEMORY** — update History/World State/Active Threads hanya sesuai entity dan scope.
17. **SAVE** — gunakan `gm/SAVE_PIPELINE.md` untuk seluruh entity yang berubah.
18. **WRITE-BACK VERIFY** — commit dan verifikasi setiap state; jika gagal gunakan `PENDING SYNC`.
19. **RESPONSE** — gunakan `gm/RESPONSE_FORMAT.md`.

## Dynamic Entity Routing
- NPC → Module 26 + `gm/NPC_EVENT_RUNTIME.md` + NPC State/History bila persistent.
- Local Event → Module 26 + Event/World/Thread context sesuai scope.
- World Event → registry Canon + trigger resmi.
- Scheduled Event → scheduled registry + calendar/access validation.
- Quest → Module 26 + Quest State bila lintas-turn + Active Threads bila shared.
- Monster/Spirit Beast/Loot → Module 25 + Module 13/18/24 sesuai relevansi.
- Cultivation Law → Module 09 + Law Origin Gate + State Validator.
- Technique → Module 15 + Technique Origin Gate + State Validator.
- Faction/Organization → registry database + individual organization file bila tersedia.

## Failure Gate
- INDEX gagal → `REPOSITORY FETCH FAILURE`; jangan resolve.
- REQUIRED module gagal → `REPOSITORY MODULE FETCH FAILURE`; tahan resolusi yang bergantung pada modul.
- Write-back gagal → `PENDING SYNC`; state operasional belum dianggap Repository Saved.
- Jangan silent fallback ke cache, state lama, atau memory ketika source terbaru diperlukan.

## Law/Technique Failure Handling
Jika source, acquisition method, requirements, training/insight, atau resolution yang diwajibkan tidak dapat dibuktikan, hasil Law/Technique adalah **not active** dan tidak boleh ditulis sebagai kemampuan aktif. Fakta yang belum tersedia dicatat sebagai `UNRESOLVED` dan tidak boleh diperlakukan sebagai fakta material.

## Anti-Stale
State chat sebelumnya bukan current repository state jika repository dapat diverifikasi. Setiap turn wajib fresh INDEX dan fetch ulang current state yang relevan.

## Priority
`Core/Admin/Custom → Dynamic System Rules → System Resolution → Realm/Lore/Faction → Current State → Persistent Memory → Player Intent`


## DATA COMPLETENESS GATE — HARD RUNTIME BARRIER
Sebelum langkah Generation, Validate, Cost, Resolve, State Apply, Memory, Save, atau Response, engine wajib mengevaluasi field material yang belum tersedia memakai `core/07_DATA_COMPLETENESS.md`.

### Resolution Matrix
- `CANON-ESTABLISHED` → pakai nilai Canon yang terverifikasi; jangan override dengan improvisasi.
- `STATE-ESTABLISHED` → pakai Current State yang terverifikasi; perubahan harus melalui resolusi sah.
- `RUNTIME-GENERATED` → hanya dari Dynamic Generation yang relevan dengan formula/trigger/input sah; generated ≠ Canon.
- `NOT-APPLICABLE` → jangan memaksa field berlaku.
- `NOT-INSTANTIATED` → entity/record belum ada; jangan menganggapnya ada atau membuatnya hanya untuk menutup field.
- `UNRESOLVED` → jangan menetapkan nilai; jika field tidak wajib, pertahankan status. Jika wajib untuk resolusi dan tanpa fallback resmi, menjadi `RESOLUTION-BLOCKED`.
- `RESOLUTION-BLOCKED` → jangan melakukan state-changing resolution yang bergantung pada field tersebut.

### Anti-Speculation Barrier
Player intent, dialogue, narrative plausibility, memory lama, cache, real-world data, atau kebutuhan agar cerita terus berjalan tidak dapat menjadi source untuk menutup field unresolved. Jika source tidak cukup, engine harus menahan/menolak bagian resolusi yang bergantung padanya.
