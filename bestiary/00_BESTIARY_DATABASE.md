# 00 — FIXED BESTIARY DATABASE

## Status
Admin Canon v1.0 — Optional Fixed Bestiary

## Purpose
Registry untuk makhluk yang sengaja ditetapkan Admin sebagai **fixed Canon**. Database ini melengkapi, bukan menggantikan, Dynamic Monster/Spirit Beast Generation pada `systems/25_DYNAMIC_GENERATION.md`.

## 1. Boundary
- Hanya creature yang tercatat di file ini yang dianggap fixed Bestiary Canon.
- Tidak tercatat di sini **bukan berarti tidak dapat ada**. Species/archetype baru tetap dapat dihasilkan melalui Dynamic Generation jika validation gate terpenuhi.
- Fixed entry diprioritaskan ketika encounter/source secara eksplisit tercakup oleh entry ini.
- Dynamic Generation digunakan ketika tidak ada fixed entry yang berlaku.
- Tier dan Realm tetap atribut terpisah.
- Fixed Bestiary tidak memberikan automatic encounter, taming, ownership, ability, loot, atau reward.

## 2. Fixed Entry Schema
Setiap entry fixed Canon sebaiknya memuat:
- `CREATURE_ID` — unik dan stabil jika entity persistence diperlukan.
- Nama/species.
- Region/habitat.
- Tier/Threat boundary yang ditetapkan Admin.
- Perilaku/ecology.
- Kemampuan yang benar-benar Canon.
- Kelemahan bila Canon.
- Spirit Beast capability bila ditetapkan.
- Loot source/table bila fixed loot memang ditetapkan.
- Origin/Canon source.

## 3. Current Fixed Entries
Belum ada entry fixed creature yang ditetapkan pada registry ini.

`???` bukan entry creature; ini hanya berarti belum ada fixed entry yang ditetapkan Admin.

## 4. Priority
Jika sumber creature memiliki fixed table yang eksplisit:

`Fixed Canon Bestiary → Fixed Event/Mission Source → Dynamic Generation → ???`

Jika fixed Bestiary tidak mencakup situasi tersebut:

`Dynamic Generation → validation → runtime result`

## 5. Anti-Catalog
Creature yang muncul melalui Dynamic Generation tidak otomatis ditambahkan ke database ini. Penambahan fixed creature harus dilakukan melalui perubahan Admin Canon dan write-back terverifikasi.
