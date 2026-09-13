# Runtime Save Pipeline

## Tujuan
Menjamin current state dan persistent memory adalah hasil transisi sah, termasuk transaksi multi-entity NPC → Event → Quest → Reward dan dynamic Monster/Beast/Loot.

## Save Sequence
1. Ambil current state terakhir yang terverifikasi untuk Character dan setiap entity yang terlibat.
2. Muat relevant History, World State, Active Threads, Timeline, Event data, dan Quest State.
3. Terapkan hanya hasil resolusi yang telah lolos validation.
4. Hitung before → after untuk semua field material pada semua entity yang berubah.
5. Tambahkan Origin Log: `World Time / Entity ID / Action/Event / Cause / Resolution / Before → After / Source`.
6. Jalankan State Validator.
7. Jika FAIL, jangan overwrite state terverifikasi dan jangan menulis memory sebagai fakta baru.
8. Jika PASS, tetapkan Current State baru untuk setiap entity yang berubah.
9. Update Character History untuk pengalaman Character.
10. Update NPC State/History untuk perubahan NPC persistent.
11. Update Quest State untuk quest lintas-turn dan Active Threads bila scope shared.
12. Update Event state/log dan World State/Timeline/Active Threads hanya bila scope mengharuskannya.
13. Update Beast State/History bila Beast terlibat.
14. Simpan reward yang benar-benar diperoleh: item/currency/technique/contract harus berasal dari source yang valid dan dicatat provenance-nya.
15. Commit/write-back seluruh file terkait melalui integrasi repository resmi.
16. Verifikasi setiap write-back sebelum menyatakan save tersinkron.

## Entity Save Rules
### NPC
Generated NPC yang tidak material tidak perlu disimpan. NPC recurring/material memakai NPC_ID stabil, Current NPC State, dan History bila diperlukan. Generated NPC tidak otomatis menjadi Global Canon.

### Event
One-turn local event dapat tetap runtime. Local event lintas-turn/material memakai EVT_ID dan state/log. World Event/Scheduled Event memakai ID dan trigger Canon resmi.

### Quest
Quest lintas-turn memakai QST_ID dan `story/quests/<QUEST_ID>.md`. Status/progress/objective/failure/completion/reward/expiry harus dapat ditelusuri. Quest gagal tidak memberi reward otomatis.

### Reward
Prioritas provenance: `Fixed Canon/Event/Mission Reward → Valid Item/Economy/Technique/Contract Source → Dynamic Loot Formula → ???`. Tidak ada reward bebas, breakthrough gratis, atau reward scaling otomatis dari Realm Character.

### Multi-Entity Transaction
Jika satu aksi mengubah Character + NPC + Event + Quest + Reward, setiap entity mendapat before → after dan Origin yang sesuai. Jangan menyimpan perubahan Character saja lalu menganggap NPC/Quest/Event ikut tersimpan.

## Memory Scope
- Character History = pengalaman Character.
- NPC History = kejadian NPC.
- Quest State/History = lifecycle quest.
- Event/World State = fakta shared sesuai scope.
- Beast History = kejadian Beast.
Jangan menyalin seluruh state ke semua memory.

## Anti-Retcon / Recovery
Tidak boleh memundurkan waktu, menghapus konsekuensi, atau menciptakan aset/memory tanpa source. Jika konflik, gunakan snapshot/Origin/History terakhir yang dapat dibuktikan. Jika write-back gagal, tandai `PENDING SYNC` dan jangan klaim sinkronisasi.
