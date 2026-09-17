# NPC REGISTRY — TIANDAO-WORLD

> Registry identitas NPC persisten. Bukan katalog tertutup untuk NPC runtime.

## Fungsi
Registry ini hanya mencatat NPC yang sudah membutuhkan identity/persistence stabil. NPC lokal sementara yang tidak mengalami perubahan material tidak wajib masuk registry.

## ID Rules
- Format NPC dapat berupa `NPC-0001` untuk ID generik atau `NPC-<NAMESPACE>-####` untuk namespace Canon/faction seperti `NPC-IMP-001` atau `NPC-REG-001`.
- NPC_ID unik, stabil, dan tidak boleh dipakai ulang.
- Nama bukan primary identifier.
- Perubahan nama, lokasi, faction, hubungan, atau status tidak mengubah NPC_ID.
- NPC yang mati permanen tetap mempertahankan ID untuk histori dan tidak boleh direcycle.

## Registry Resolution Priority
1. `lore/NPC_DATABASE.md` untuk NPC Canon yang sudah ditetapkan.
2. `characters/npc_registry.md` untuk identity/persistence registry NPC.
3. `characters/npcs/<NPC_ID>.md` untuk current persistent state bila tersedia.
4. `npc_history/<NPC_ID>_HISTORY.md` untuk continuity/history material bila tersedia.
5. `systems/26_DYNAMIC_NPC_EVENT_QUEST.md` dan `systems/29_NPC_PERSISTENCE.md` untuk generation, persistence, validation, dan lifecycle rules.

## Current Registry
Belum ada NPC dynamic persisten yang ditetapkan melalui runtime.

NPC Canon yang sudah dikenal tetap bersumber dari `lore/NPC_DATABASE.md`; registry ini tidak menggantikan database Canon tersebut.

## Persistence Paths
- Current NPC State: `characters/npcs/<NPC_ID>.md`
- NPC History: `npc_history/<NPC_ID>_HISTORY.md` bila continuity material memerlukannya.

## Persistence Gate
NPC runtime menjadi persistent/registered hanya bila continuity lintas turn atau perubahan material membutuhkan identity stabil. Saat persistence dibuat, wajib:
- menetapkan NPC_ID baru yang unik;
- membuat current state sesuai Module 29;
- membuat/update history bila diperlukan;
- mencatat Origin/Source yang valid;
- melewati Save Pipeline;
- melakukan write-back dan verification.

NPC runtime yang tidak memenuhi persistence gate tetap bersifat lokal/sementara dan tidak otomatis masuk registry.

## Knowledge & Autonomy
- Pengetahuan NPC dibatasi oleh pengalaman, akses informasi, peran, dan event yang benar-benar dialami.
- NPC tidak otomatis mengetahui informasi Player/Character yang tidak memiliki sumber in-world.
- NPC memiliki kondisi, agenda, relasi, dan keputusan sendiri sesuai data yang tersedia.

## Generated Content Rule
NPC generated bukan otomatis Global Canon. Persistence berarti identitas/state NPC dipertahankan untuk continuity; bukan berarti NPC menjadi lore global tanpa dasar Admin/Canon.

## Integrity
- Jangan menduplikasi NPC_ID.
- Jangan recycle NPC_ID.
- Jangan mengubah identity stabil hanya karena nama/lokasi/faction berubah.
- Jangan membuat NPC persisten hanya untuk mengisi registry.
- Jika required source untuk NPC resolution gagal, tahan resolusi dan gunakan failure mode repository/module yang berlaku; jangan fallback diam-diam.
