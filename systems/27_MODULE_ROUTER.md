# 27 — DYNAMIC MODULE ROUTER

## Status
Admin Canon v1.1

## Purpose
Module Router menentukan modul World Bible mana yang **wajib** di-fetch untuk sebuah turn berdasarkan trigger yang benar-benar muncul. Tujuannya adalah mempertahankan Modular World Bible, mengurangi fetch yang tidak relevan, dan mencegah GM memproses aksi menggunakan aturan yang belum diverifikasi.

## 1. Prinsip
- `INDEX.md` selalu menjadi router utama dan wajib di-fetch ulang pada setiap Player Message.
- Setelah INDEX fresh berhasil, GM mendeteksi trigger dari Current State, World Time, lokasi, intent, dan konteks aktif.
- Modul **REQUIRED** wajib di-fetch sebelum validasi/resolusi.
- Modul **OPTIONAL** hanya di-fetch jika hasil resolusi membutuhkannya.
- Jangan fetch seluruh World Bible hanya untuk satu aksi.
- Jika modul wajib gagal di-fetch, resolusi yang bergantung padanya ditahan dan GM menggunakan failure mode resmi; tidak boleh mengarang.
- Modul yang tidak relevan tidak perlu di-fetch.

## 2. Mandatory Bootstrap
Urutan minimum setiap turn:

`FRESH INDEX → CORE/LOAD ORDER → CURRENT WORLD TIME → CURRENT CHARACTER STATE → RELEVANT PERSISTENT MEMORY → TRIGGER DETECTION → REQUIRED MODULE FETCH → VALIDATION → RESOLUTION`

Bootstrap karakter baru/sesi baru juga mengikuti `gm/PLAYER_BOOT_PROMPT.md` dan Load Order INDEX.

## 3. Trigger Registry

| Trigger | Modul Wajib | Modul Tambahan Bila Relevan |
|---|---|---|
| Semua turn | `INDEX.md`, Core Rules | World/State sesuai Load Order |
| World Time | `core/02_TIME_SYSTEM.md`, `lore/CALENDAR.md` | Event/Scheduled Event |
| Action umum | `core/03_ACTION_SYSTEM.md`, `core/04_ANTI_CHEAT.md` | Sistem spesifik aksi |
| HP/luka/pemulihan/satiety | `systems/11_VITALITY.md` | Combat/Item/Technique |
| Combat | `systems/12_COMBAT.md` | Monster/Item/Technique/Travel/Formation |
| Cultivation/Qi/Realm/Breakthrough | `systems/09_CULTIVATION.md` | Techniques/Law/Items |
| Technique/Jurus | `systems/15_TECHNIQUES.md` | Cultivation/Items/Law |
| Item/Equipment/Inventory | `systems/14_ITEMS.md` | Economy/Loot/Technique/Production |
| Economy/transaksi | `systems/10_ECONOMY.md` | Regional Economy/Faction |
| Travel/perjalanan | `systems/20_TRAVEL_ROUTES.md` | Region/World Map/Encounter |
| Monster/encounter | `systems/13_MONSTERS.md`, `systems/25_DYNAMIC_GENERATION.md` | Regional Ecosystem/Combat/Loot |
| Fixed Bestiary source | `bestiary/00_BESTIARY_DATABASE.md` | Monster/Dynamic Generation |
| Loot | `systems/18_LOOT.md`, `systems/25_DYNAMIC_GENERATION.md` | Items/Economy/Source module |
| Spirit Beast | `systems/24_SPIRIT_BEASTS.md` | Monster/Dynamic Generation/Combat/Loot |
| NPC/social encounter | `systems/26_DYNAMIC_NPC_EVENT_QUEST.md` | Faction/Lore/Reputation |
| Local Event | `systems/26_DYNAMIC_NPC_EVENT_QUEST.md` | World State/Active Threads/Faction |
| World Event | `events/world_events/00_WORLD_EVENT_REGISTRY.md` | Event-specific file |
| Scheduled Event | `events/scheduled_events/00_SCHEDULED_EVENT_REGISTRY.md` | Event-specific file |
| Quest | `systems/26_DYNAMIC_NPC_EVENT_QUEST.md` | Quest State/Faction/Loot/Economy |
| Gardening | `systems/23_GARDENING.md` | Economy/Items/Travel |
| Faction/organization | Relevant faction database or individual organization file | Region/Reputation/Economy/Techniques |
| Karma/Reputation consequence | `systems/16_KARMA.md`, `systems/17_REPUTATION.md` | Faction/Event |
| Crafting/Forging/Smithing | `systems/31_CRAFTING_FORGING.md` | Items/Economy/Techniques/Material source |
| Alchemy/Pill | `systems/32_ALCHEMY_PILLS.md` | Items/Techniques/Economy/Material source |
| Formation/Array | `systems/33_FORMATION_ARRAYS.md` | Items/Cultivation/Combat/Region/Event |
| Artifact/Weapon Refinement | `systems/34_ARTIFACT_WEAPON_REFINEMENT.md` | Items/Techniques/Economy/Crafting/Alchemy |

## 4. Production Module Routing
### Crafting / Forging
Use Module 31 when the action creates a new item, performs material processing, or executes a valid crafting/forging procedure.

### Alchemy / Pill
Use Module 32 when the action refines herb/material into a Pill or other alchemical product.

### Formation / Array
Use Module 33 when the action constructs, activates, operates, disrupts, repairs, or destroys a Formation/Array.

### Artifact / Weapon Refinement
Use Module 34 when an **existing item** is modified through repair/refinement/temper/upgrade or another valid refinement process.

### Boundary Rule
`New Item Production → Module 31`
`Alchemy Product → Module 32`
`Formation/Array Structure → Module 33`
`Existing Item Modification → Module 34`

When an action crosses modules, all affected REQUIRED modules must be fetched. Example: refining an existing weapon with an alchemical material may require Modules 34 + 32 + 14, while a Formation using a newly crafted Array Core may require Modules 31 + 33 + 14.

## 5. Individual Organization Resolution
TianDao-World mendukung dua lapisan data faction:
1. **Canon Database** untuk registry dan ringkasan global.
2. **Individual Organization File** untuk detail organisasi yang membutuhkan granularitas tinggi.

Jika individual file resmi tersedia untuk organisasi yang sedang disentuh aksi, file individual menjadi sumber detail utama setelah database registry. Jika belum tersedia, gunakan database resmi yang ada dan jangan mengarang detail yang tidak tercatat.

## 6. Fixed Bestiary Boundary
`bestiary/00_BESTIARY_DATABASE.md` adalah **optional Admin Canon fixed bestiary**.
- Entry di dalamnya adalah species/creature yang sengaja ditetapkan Admin sebagai fixed Canon.
- Fixed entry tidak membatasi species/archetype dinamis dari Module 25.
- Jika fixed entry secara eksplisit mencakup source encounter, gunakan data fixed tersebut sebelum dynamic generation.
- Jika tidak tercakup, gunakan Dynamic Generation.
- Fixed Bestiary tidak boleh digunakan untuk mengubah Tier menjadi Realm.

## 7. Production Boundary
- Production modules tidak menggantikan Module 14 Items.
- Material/item identity, ownership, condition, quality, equipment, inventory, dan provenance tetap mengikuti Module 14.
- Production result tidak menjadi Global Canon hanya karena berhasil dibuat runtime.
- Dynamic recipe/procedure/result bukan fixed Canon kecuali Admin menyimpannya sebagai Canon.
- Tidak ada automatic Realm scaling.
- Tidak ada hidden numeric modifier.

## 8. Failure Policy
Jika Required Module gagal:
`REPOSITORY MODULE FETCH FAILURE`

GM wajib:
- menyebut modul yang gagal;
- menahan resolusi yang membutuhkan modul tersebut;
- tidak memakai cache diam-diam sebagai pengganti fresh fetch;
- tidak mengarang isi modul.

Jika write-back gagal setelah resolusi valid, gunakan `gm/PENDING_SYNC.md`; state operasional tidak dianggap Repository Saved sampai write-back diverifikasi.

## 9. Runtime Contract
`FRESH INDEX → IDENTIFY TRIGGERS → FETCH REQUIRED MODULES ONLY → VALIDATE → RESOLVE → UPDATE/ORIGIN → SAVE → WRITE-BACK VERIFY → RESPONSE`

## 10. Anti-Catalog
Dynamic result tetap runtime content. Ia tidak menjadi fixed Canon, Bestiary, faction database, NPC registry, event registry, recipe/formula/formation registry, atau global lore hanya karena pernah muncul dalam gameplay.

Fixed Canon hanya ditambahkan melalui perubahan Admin yang sah dan diverifikasi.
