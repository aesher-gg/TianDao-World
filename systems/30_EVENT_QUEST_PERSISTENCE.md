# Module 30 — Event & Quest Persistence

## Status
Admin Canon v1.0

## Purpose
Memberi lifecycle dan persistence yang konsisten untuk Event/Quest lintas-turn tanpa mengubah generated content menjadi Global Canon.

## Event Persistence
Persistent/material local event memakai `EVT-####` yang unik dan stabil.

Minimum state:
- ID, scope, location, start time
- trigger/source
- before state
- current changes
- affected entities
- next checkpoint
- completion condition
- status
- Origin

Local Event tidak boleh naik menjadi Regional/Global tanpa Canon/Admin trigger.

World Event dan Scheduled Event tetap mengikuti registry Canon masing-masing.

## Quest Persistence
Quest lintas-turn memakai `QST-####` dan `story/quests/QST-####.md`.

Lifecycle:
`Offered → Accepted → Active → Completed`
atau
`Declined / Failed / Abandoned / Expired`.

Minimum state:
- ID
- source/issuer bila ada
- objective/target/method
- risk/cost
- success/failure condition
- progress
- deadline bila bersumber
- reward provenance
- status
- Origin

## Reward Gate
`Fixed Canon/Event/Mission → Valid Item/Economy/Technique/Contract → Dynamic Loot → RESOLUTION-BLOCKED`

`RESOLUTION-BLOCKED` berarti reward belum dapat ditetapkan karena tidak ada source reward yang sah. Tidak ada reward bebas atau scaling otomatis berdasarkan Realm Character.

## Shared Scope
Quest/event hanya masuk `ACTIVE_THREADS`, `WORLD_STATE`, atau `STORY_TIMELINE` bila scope memang shared dan fakta sudah terkonfirmasi.

## Validation & Save
Setiap perubahan lintas-turn harus melewati Module 26, State Validator, before → after, Origin, Save Pipeline, dan write-back verification. Generated Event/Quest tetap generated meskipun dipersistenkan.

## Data Completeness
Gunakan `core/07_DATA_COMPLETENESS.md` untuk field yang belum tersedia. Jangan membuat issuer, reward, deadline, target, atau scope baru hanya untuk mengisi schema.


## DATA COMPLETENESS PERSISTENCE GATE
Persistensi tidak mengubah data yang belum terbukti menjadi fakta. Issuer, target, reward, deadline, scope, state, dan outcome wajib memiliki source/resolution. UNRESOLVED tidak boleh dipersistenkan sebagai nilai konkret; RESOLUTION-BLOCKED menahan perubahan yang bergantung padanya.
