# NPC REGISTRY — TIANDAO-WORLD

> Registry identitas NPC persisten. Bukan katalog tertutup untuk NPC runtime.

## Fungsi
Registry ini hanya mencatat NPC yang sudah membutuhkan identity/persistence stabil. NPC lokal sementara yang tidak mengalami perubahan material tidak wajib masuk registry.

## ID Rules
- Format: `NPC-0001`.
- NPC_ID unik, stabil, dan tidak boleh dipakai ulang.
- Nama bukan primary identifier.
- Perubahan nama, lokasi, faction, hubungan, atau status tidak mengubah NPC_ID.
- NPC yang mati permanen tetap mempertahankan ID untuk histori dan tidak boleh direcycle.

## Current Registry
Belum ada NPC dynamic persisten yang ditetapkan melalui runtime.

NPC Canon yang sudah dikenal tetap bersumber dari `lore/NPC_DATABASE.md`; registry ini tidak menggantikan database Canon tersebut.

## Persistence Paths
- Current NPC State: `characters/npcs/<NPC_ID>.md`
- NPC History: `npc_history/<NPC_ID>_HISTORY.md` bila continuity material memerlukannya.

## Generated Content Rule
NPC generated bukan otomatis Global Canon. Persistence berarti identitas/state NPC dipertahankan untuk continuity; bukan berarti NPC menjadi lore global tanpa dasar Admin/Canon.
