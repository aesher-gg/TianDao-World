# Runtime Save Pipeline

## Tujuan
Menjamin current state dan persistent memory adalah hasil transisi sah, termasuk transaksi multi-entity NPC → Event → Quest → Reward, dynamic Monster/Beast/Loot, perubahan faction/organization, dan production transaction Crafting/Alchemy/Formation/Refinement.

## Save Gate
`Fresh INDEX → Required Modules → Current State → Resolve → Validate → Before/After → Origin → Entity Save → Cross-Entity Integrity → Write-Back → Fetch Verify`

Tidak ada status `Repository Saved` sebelum write-back berhasil dan setiap file yang berubah telah diverifikasi.

## Save Sequence
1. Ambil current state terakhir yang terverifikasi untuk Character dan setiap entity.
2. Muat relevant History, World State, Active Threads, Timeline, Event data, Quest State, organization state, dan production entity state bila relevan.
3. Terapkan hanya hasil resolusi yang lolos validation.
4. Hitung before → after untuk semua field material pada semua entity.
5. Tambahkan Origin Log: `World Time / Entity ID / Action/Event / Cause / Resolution / Before → After / Source`.
6. Jalankan State Validator.
7. Jika FAIL, jangan overwrite state terverifikasi.
8. Jika PASS, tetapkan Current State baru untuk setiap entity.
9. Update Character History untuk pengalaman Character.
10. Update NPC State/History untuk NPC persistent.
11. Update Quest State dan Active Threads bila lintas-turn/shared.
12. Update Event state/log dan World State/Timeline/Active Threads sesuai scope.
13. Update Beast State/History bila Beast terlibat.
14. Update organization/faction state hanya jika ada perubahan Canon/state yang sah dan file individual/database yang relevan memang terdampak.
15. Untuk production, persist semua entity yang benar-benar berubah: existing/new Item State, consumed Material state, Formation state, Array Core state, tool/workspace state bila persistent, dan resource/currency state yang terdampak.
16. Pastikan production provenance chain tetap utuh: input Origin → process/resolution → result Origin. Jangan menghapus Origin sebelumnya pada existing item refinement.
17. Simpan reward yang benar-benar diperoleh dengan provenance valid.
18. Commit/write-back seluruh file terkait melalui integrasi repository resmi.
19. Fetch ulang setiap file yang ditulis dan cocokkan content/state setelah commit.
20. Hanya setelah verifikasi sukses, tandai Repository Saved.

## Entity Save Rules
### NPC
Generated NPC yang tidak material tidak perlu disimpan. NPC recurring/material memakai NPC_ID stabil, Current NPC State, dan History bila diperlukan.

### Event
One-turn local event dapat tetap runtime. Local event lintas-turn/material memakai EVT_ID dan state/log. World/Scheduled Event memakai ID dan trigger Canon resmi.

### Quest
Quest lintas-turn memakai QST_ID dan `story/quests/<QUEST_ID>.md`. Status/progress/objective/failure/completion/reward/expiry harus dapat ditelusuri.

### Organization
Organization membership, rank, contract, access, internal state, atau material relationship hanya disimpan jika resolusi sah menghasilkan perubahan. Individual organization file tidak menggantikan registry.

### Production — Crafting / Forging
Module 31 menghasilkan item baru atau processed material yang menjadi item. Save wajib mencatat consumed materials, new Item State, Item Origin, Character/resource changes, dan History yang relevan.

### Production — Alchemy / Pills
Module 32 menghasilkan Pill/Alchemy Product. Save wajib mencatat consumed herb/material, process result, Item State, Item Origin, dan resource changes yang benar-benar terjadi.

### Production — Formation / Array
Module 33 dapat menciptakan atau mengubah Formation/Array dan Array Core state. Save wajib mencatat identity/state, consumed materials, location/shared state bila terdampak, Origin, dan History bila persisten.

### Production — Artifact / Weapon Refinement
Module 34 memodifikasi existing Item State. Save wajib mempertahankan identity dan prior Origin, lalu menambahkan Origin/History untuk refinement. Quality/property/condition/category changes hanya disimpan jika resolution valid.

### Production Cross-Entity Transaction
Jika satu aksi mengubah Character + Item + Material + Formation/Array Core + tool/workspace atau entity lain, setiap entity mendapat before → after dan Origin. Jangan menyimpan Character saja lalu menganggap entity lain ikut tersimpan.

### Reward
Prioritas provenance: `Fixed Canon/Event/Mission Reward → Valid Item/Economy/Technique/Contract Source → Dynamic Loot Formula → RESOLUTION-BLOCKED`. Tidak ada reward bebas, breakthrough gratis, atau Realm scaling otomatis.

## Multi-Entity Transaction
Jika satu aksi mengubah Character + NPC + Event + Quest + Reward, setiap entity mendapat before → after dan Origin. Jangan menyimpan Character saja lalu menganggap entity lain ikut tersimpan.

## Memory Scope
- Character History = pengalaman Character.
- NPC History = kejadian NPC.
- Quest State/History = lifecycle quest.
- Event/World State = fakta shared sesuai scope.
- Beast History = kejadian Beast.
- Organization file/database = fakta organisasi yang memang Canon/state dan tidak tercampur dengan memory Character.
- Production entity History = perubahan material pada Item/Formation/Array Core atau entity produksi lain sesuai scope.

## Recovery
Tidak boleh memundurkan waktu, menghapus konsekuensi, atau menciptakan aset/memory tanpa source. Jika write-back gagal atau verifikasi gagal, tandai `PENDING SYNC`; perubahan belum menjadi Repository Saved.
