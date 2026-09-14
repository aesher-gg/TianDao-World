# 00 — FIXED BESTIARY DATABASE

## Status
Admin Canon v1.1 — Optional Fixed Bestiary

## Purpose
Registry untuk makhluk yang sengaja ditetapkan Admin sebagai fixed Canon. Database ini melengkapi, bukan menggantikan, Dynamic Monster/Spirit Beast Generation pada `systems/25_DYNAMIC_GENERATION.md`.

## Boundary
- Hanya creature yang tercatat di file ini yang dianggap fixed Bestiary Canon.
- Tidak tercatat bukan berarti tidak dapat ada.
- Species/archetype baru tetap dapat dihasilkan melalui Dynamic Generation jika validation gate terpenuhi.
- Fixed entry diprioritaskan ketika encounter/source secara eksplisit tercakup.
- Dynamic Generation digunakan ketika tidak ada fixed entry yang berlaku.
- Tier dan Realm tetap atribut terpisah.
- Fixed Bestiary tidak memberikan automatic encounter, taming, ownership, ability, loot, atau reward.

## Fixed Entry Schema
Setiap entry fixed Canon harus memuat bila relevan:
- `CREATURE_ID` unik/stabil bila persistence diperlukan.
- Nama/species.
- Region/habitat.
- Tier/Threat boundary.
- Perilaku/ecology.
- Kemampuan Canon dan batas penggunaannya.
- Kelemahan bila Canon.
- Spirit Beast capability bila ditetapkan.
- Loot source/table bila fixed.
- Origin/Canon source.
- Persistence rule bila creature recurring/material.

## Current Fixed Entries
Belum ada entry fixed creature yang ditetapkan Admin.

`???` bukan entry creature; ini berarti belum ada fixed entry.

## Resolution & Validation
Jika fixed entry berlaku, GM mengambil data entry sebagai source fixed dan tetap menjalankan validation. Jika tidak berlaku, gunakan Dynamic Generation. Fixed entry tidak boleh digunakan untuk memberikan atribut yang tidak tercatat.

## Priority
`Fixed Canon Bestiary → Fixed Event/Mission Source → Dynamic Generation → ???`

## Anti-Catalog
Creature hasil Dynamic Generation tidak otomatis masuk database. Penambahan fixed creature harus melalui perubahan Admin Canon dan write-back terverifikasi.
