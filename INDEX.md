# TianDao-World

## World Bible Index

> Struktur resmi repository TianDao-World. Semua modul dunia dan sistem dirujuk melalui indeks ini.

## Core
- `core/00_CORE_RULES.md`
- `core/01_GAME_LOOP.md`
- `core/02_TIME_SYSTEM.md`
- `core/03_ACTION_SYSTEM.md`
- `core/04_ANTI_CHEAT.md`
- `core/05_SAVE_INTEGRITY.md`
- `core/06_ID_AND_SAVE_SYSTEM.md`

## Realms
- `realms/01_WORLD_MAP.md`
- `realms/02_CANGYUAN_PLAINS.md`
- `realms/03_QINGLUAN_MOUNTAINS.md`
- `realms/04_SOUTHERN_YAOHUANG_DOMAIN.md`
- `realms/05_DONGMING_SEA.md`
- `realms/06_BEIMING_SNOWLANDS.md`
- `realms/07_JINYAN_DESERT.md`

## Systems
- `systems/08_ORGANIZATIONS.md`
- `systems/09_CULTIVATION.md`
- `systems/10_ECONOMY.md`
- `systems/11_VITALITY.md`
- `systems/12_COMBAT.md`
- `systems/13_MONSTERS.md`
- `systems/14_ITEMS.md`
- `systems/15_TECHNIQUES.md`
- `systems/16_KARMA.md`
- `systems/17_REPUTATION.md`
- `systems/18_LOOT.md`
- `systems/19_REGIONAL_MONSTER_ECOSYSTEM.md`
- `systems/20_TRAVEL_ROUTES.md`
- `systems/21_REGIONAL_ECONOMY.md`
- `systems/22_REGIONAL_FACTION_RELATIONS.md`
- `systems/23_GARDENING.md` — Gardening, crop growth, numeric garden/crop status
- `systems/24_SPIRIT_BEASTS.md` — Spirit Beast identity, state, relationship, taming, ownership, contract, growth/evolution, combat, and persistence
- `systems/25_DYNAMIC_GENERATION.md` — Admin formulas for dynamic encounter, Monster/Spirit Beast generation, Threat/Tier ceiling, and Loot generation
- `systems/26_DYNAMIC_NPC_EVENT_QUEST.md` — Admin formulas for dynamic NPC, local Event, and Quest generation, persistence, validation, and anti-railing

## Loot — Canon Database
- `loot/00_LOOT_TABLE_DATABASE.md` — Optional Admin Canon registry for fixed/exception loot tables; not a global loot catalog

## Characters
- `characters/players.md` — Player Registry
- `characters/character_registry.md` — Character Registry
- `characters/beast_registry.md` — Spirit Beast Registry
- `characters/npc_registry.md` — Persistent NPC Registry; dynamic runtime NPC tetap tidak dibatasi oleh registry
- `characters/players/` — Individual Current Character State files
- `characters/beasts/` — Individual Current Spirit Beast State files
- `characters/npcs/` — Individual Current NPC State files bila NPC membutuhkan persistence
- `character_history/` — Persistent private story memory per Character ID
- `beast_history/` — Persistent private history per Beast ID
- `npc_history/` — Persistent NPC history bila continuity material memerlukannya

## Persistent Story Memory
- `story/WORLD_STATE.md` — shared world facts with ongoing consequences
- `story/ACTIVE_THREADS.md` — unresolved quests, conflicts, promises, contracts, and other active threads
- `story/STORY_TIMELINE.md` — compact chronological index of major resolved events
- `story/quests/` — Current Quest State untuk quest lintas turn yang membutuhkan persistence

## Audits
- `audits/2026-09-10_WORLD_AUDIT.md` — repository/runtime integrity audit

## Factions — Canon Databases
- `factions/sects/00_SECT_DATABASE.md`
- `factions/dojos/00_DOJO_DATABASE.md`
- `factions/imperial/00_IMPERIAL_DATABASE.md`
- `factions/criminal/00_CRIMINAL_DATABASE.md`
- `factions/organizations/00_ORGANIZATION_DATABASE.md`
- `factions/regional/00_REGIONAL_FACTION_DATABASE.md`

## Events
- `events/39_CUSTOM_EVENTS.md`
- `events/world_events/00_WORLD_EVENT_REGISTRY.md`
- `events/scheduled_events/00_SCHEDULED_EVENT_REGISTRY.md`
- `events/world_events/`
- `events/scheduled_events/`

## Custom Content
- `custom/40_CUSTOM_LAWS.md`
- `custom/41_CUSTOM_SECTS.md`
- `custom/42_CUSTOM_TECHNIQUES.md`

## Lore
- `lore/CITY_VILLAGE_DATABASE.md`
- `lore/NPC_DATABASE.md`
- `lore/HISTORY.md`
- `lore/CALENDAR.md`
- `lore/RELIGIONS.md`
- `lore/LEGENDS.md`

## AI Game Master
- `gm/GM_PROMPT.md`
- `gm/PLAYER_BOOT_PROMPT.md`
- `gm/ACTION_RUNTIME_PROMPT.md`
- `gm/PENDING_SYNC.md` — mandatory fallback/procedure when repository write-back is unavailable or fails
- `gm/RESPONSE_FORMAT.md`
- `gm/CHECKLIST.md`
- `gm/VALIDATION_RULES.md`
- `gm/YELLOW_AUDIT.md`
- `gm/RUNTIME_ENGINE.md`
- `gm/STATE_VALIDATOR.md`
- `gm/ACTION_RESOLVER.md`
- `gm/NPC_EVENT_RUNTIME.md`
- `gm/SAVE_PIPELINE.md`

## Load Order
1. Core rules.
2. Custom content dan event resmi.
3. Relevant realm/system modules, termasuk `systems/24_SPIRIT_BEASTS.md` bila Spirit Beast relevan, `systems/25_DYNAMIC_GENERATION.md` bila encounter/creature/loot generation relevan, dan `systems/26_DYNAMIC_NPC_EVENT_QUEST.md` bila NPC/event/quest generation atau resolution relevan.
4. Faction databases dan city/NPC databases bila relevan.
5. Lore yang relevan.
6. Shared persistent world state dan active story threads bila relevan.
7. Current character state yang sesuai dengan Character ID aktif.
8. Current Spirit Beast State dan Beast History yang relevan dengan action/encounter/relationship.
9. Current NPC State dan NPC History bila NPC persisten terlibat.
10. Character History milik Character ID aktif bila tersedia.
11. Current Quest State bila quest lintas turn relevan.
12. Player intent.

## Runtime Prompt Contract
- `gm/PLAYER_BOOT_PROMPT.md` digunakan sekali pada boot karakter/sesi baru untuk memuat World Bible, current state, dan memory yang relevan.
- `gm/ACTION_RUNTIME_PROMPT.md` digunakan pada setiap aksi gameplay berikutnya.
- **Setiap Player message adalah turn baru dan wajib memulai dengan fresh fetch/verification `INDEX.md` dari repository sebelum membaca/menilai state atau memproses intent. Tidak boleh memakai INDEX, state, atau hasil load dari turn sebelumnya sebagai pengganti fresh fetch.**
- **Jika tool fetch tersedia, panggilan fetch `INDEX.md` harus menjadi operasi repository pertama pada setiap turn. AI GM dilarang menghasilkan resolusi gameplay sebelum hasil fetch tersebut berhasil dibaca.**
- Setelah INDEX fresh berhasil dibaca, AI GM wajib mengikuti Load Order dan melakukan fetch ulang setiap sumber state yang diperlukan untuk turn tersebut.
- Jika fresh fetch `INDEX.md` gagal, AI GM wajib menyatakan repository fetch failure dan tidak boleh berpura-pura telah melakukan fresh verification.
- Setiap aksi yang menghasilkan perubahan material wajib melewati Save Pipeline.
- Setelah resolusi tervalidasi, AI GM wajib memperbarui Current Character State dan memory persisten yang relevan melalui integrasi repository yang tersedia; bila Spirit Beast terlibat, Current Beast State dan Beast History juga wajib diproses sesuai Module 24; bila NPC persisten atau Quest State berubah, entity state/history yang relevan juga wajib diproses sesuai Module 26.
- Kedua prompt wajib mengikuti Runtime Engine, Core Rules, Save Integrity, ID/Save System, dan seluruh sumber yang ditunjuk INDEX.
- `systems/23_GARDENING.md` wajib dimuat ketika berkebun, tanaman, kebun, pertumbuhan tanaman, atau hasil panen menjadi relevan terhadap aksi/runtime.
- `systems/24_SPIRIT_BEASTS.md` wajib dimuat ketika Spirit Beast, taming, ownership, contract, Beast combat, Beast growth/evolution, Beast state, atau Beast history menjadi relevan terhadap aksi/runtime.
- `systems/25_DYNAMIC_GENERATION.md` wajib dimuat ketika dynamic encounter, Monster generation, Spirit Beast generation, Threat/Tier generation, loot generation, atau loot resolution tanpa fixed table menjadi relevan terhadap aksi/runtime.
- `systems/26_DYNAMIC_NPC_EVENT_QUEST.md` wajib dimuat ketika dynamic NPC generation, local event generation/resolution, quest generation/resolution, persistent NPC, persistent quest, atau NPC/Event/Quest relationship menjadi relevan terhadap aksi/runtime.
- `loot/00_LOOT_TABLE_DATABASE.md` dimuat bila fixed loot table, unique reward, atau content table tertentu perlu diperiksa; registry tersebut tidak membatasi dynamic loot.
- `gm/PENDING_SYNC.md` wajib digunakan ketika write-back repository tidak tersedia atau gagal; pending changes bukan Canon tersinkron sampai diverifikasi dan ditulis oleh Admin.
