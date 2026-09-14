# Module 29 — NPC Persistence

## Status
Admin Canon v1.0

## Purpose
Memastikan NPC penting/berulang memiliki continuity tanpa menjadikan semua NPC runtime sebagai katalog permanen.

## Identity
- `NPC_ID` format `NPC-####`, unik, stabil, tidak pernah dipakai ulang.
- Nama, faction, lokasi, rank, atau status tidak mengganti NPC_ID.

## Persistence Gate
NPC disimpan bila recurring/material atau mengalami perubahan yang berdampak pada continuity. NPC one-turn non-material boleh tetap runtime.

## State Schema
- NPC_ID
- Name/known identity
- Location
- Role/faction
- Realm/Stage bila bersumber
- Condition
- Knowledge boundary
- Temperament/attitude
- Agenda
- Relationships
- Current status
- Last verified world time

## Knowledge & Autonomy
NPC hanya mengetahui pengalaman dan informasi yang secara logis dapat diaksesnya. NPC boleh menolak, salah paham, berbohong, gagal, pergi, berubah sikap, atau bertindak sendiri sesuai state/agenda.

## History
`npc_history/NPC-####_HISTORY.md` digunakan bila continuity material memerlukannya. History hanya mencatat kejadian NPC tersebut.

## Validation
Persistent NPC wajib melewati Module 26, State Validator, entity isolation, Origin, dan Save Pipeline. Generated NPC tidak otomatis menjadi Global Canon.
