# TianDao-World

## World Bible Index

> Struktur resmi repository TianDao-World. Semua modul dunia dan sistem dirujuk melalui indeks ini.
> `INDEX.md` adalah router utama. Setiap Player Message wajib memulai dengan fresh fetch INDEX sebelum state/intent diproses.

## Core
- `core/00_CORE_RULES.md`
- `core/01_GAME_LOOP.md`
- `core/02_TIME_SYSTEM.md`
- `core/03_ACTION_SYSTEM.md`
- `core/04_ANTI_CHEAT.md`
- `core/05_SAVE_INTEGRITY.md`
- `core/06_ID_AND_SAVE_SYSTEM.md`
- `core/07_DATA_COMPLETENESS.md` — status data, unresolved state, placeholder, dan audit completeness

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
- `systems/27_MODULE_ROUTER.md` — Trigger → Module routing, modular fetch, bootstrap, fixed Bestiary boundary, and individual organization-file resolution
- `systems/28_ORGANIZATION_PERSISTENCE.md` — Persistent organization identity/state, membership, rank, contract, access, and cross-entity save rules
- `systems/29_NPC_PERSISTENCE.md` — Persistent NPC identity/state, knowledge, autonomy, history, and NPC lifecycle validation
- `systems/30_EVENT_QUEST_PERSISTENCE.md` — Persistent Event/Quest identity, lifecycle, scope, reward provenance, and cross-turn state
- `systems/31_CRAFTING_FORGING.md` — Universal crafting/forging, material processing, recipe, qualification, tool/workspace, resolution, quality, provenance, and persistence
- `systems/32_ALCHEMY_PILLS.md` — Alchemy/Pill formula, alchemist qualification, furnace/process, failure, quality, effect provenance, and persistence
- `systems/33_FORMATION_ARRAYS.md` — Formation/Array blueprint, construction, activation, operation, disruption, repair, combat interaction, and persistence
- `systems/34_ARTIFACT_WEAPON_REFINEMENT.md` — Refinement of existing items/artifacts/weapons, quality/property/condition changes, failure, provenance, and persistence

## Bestiary
- `bestiary/00_BESTIARY_DATABASE.md` — Optional Admin Canon fixed Bestiary; does not limit dynamic creature generation

## Loot — Canon Database
- `loot/00_LOOT_TABLE_DATABASE.md` — Optional Admin Canon registry for fixed/exception loot tables; not a global loot catalog

## Characters
- `characters/players.md` — Player Registry / starting-data registry
- `characters/character_registry.md` — Character Registry
- `characters/beast_registry.md` — Spirit Beast Registry
- `characters/npc_registry.md` — Persistent NPC Registry; dynamic runtime NPC tetap tidak dibatasi oleh registry
- `characters/players/` — Individual Current Character State files
- `characters/beasts/` — Individual Current Spirit Beast State files
- `characters/npcs/` — Individual Current NPC State files bila NPC membutuhkan persistence
- `character_history/` — Persistent private story memory per Character ID
- `beast_history/` — Persistent private history per Beast ID
- `npc_history/` — Persistent NPC history bila continuity material memerlukannya

## Formation Persistence
- `formations/formation_registry.md` — Persistent Formation/Array registry
- `formations/` — Current persistent Formation State files
- `formations/cores/` — Current persistent Array Core State files
- `formation_history/` — Persistent Formation/Array Core history bila continuity material memerlukannya

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
- Individual organization files may be added under the relevant faction directory; when present, they provide granular detail after the registry database.
- `systems/28_ORGANIZATION_PERSISTENCE.md` governs stable organization identity/state and persistence; individual files are not automatically Global Canon beyond their stored content.

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
1. **Fresh `INDEX.md`** — router dan source load-order untuk turn tersebut.
2. Core rules, termasuk `core/07_DATA_COMPLETENESS.md` untuk status data.
3. Custom content dan event resmi yang relevan.
4. Current World Time sesuai hierarchy resmi.
5. Relevant realm/system modules, termasuk `systems/24_SPIRIT_BEASTS.md` bila Spirit Beast relevan, `systems/25_DYNAMIC_GENERATION.md` bila encounter/creature/loot generation relevan, `systems/26_DYNAMIC_NPC_EVENT_QUEST.md` bila NPC/event/quest generation atau resolution relevan, `systems/27_MODULE_ROUTER.md` untuk trigger routing, persistence modules bila entity persistence relevan, serta `systems/31_CRAFTING_FORGING.md`, `systems/32_ALCHEMY_PILLS.md`, `systems/33_FORMATION_ARRAYS.md`, atau `systems/34_ARTIFACT_WEAPON_REFINEMENT.md` sesuai trigger.
6. Faction databases dan individual organization files bila relevan.
7. City/NPC/lore yang relevan.
8. Shared persistent world state dan active story threads bila relevan.
9. Current character state yang sesuai dengan Character ID aktif.
10. Current Spirit Beast State dan Beast History yang relevan dengan action/encounter/relationship.
11. Current NPC State dan NPC History bila NPC persisten terlibat.
12. Character History milik Character ID aktif bila tersedia.
13. Current Formation/Array State dan Formation History bila Formation/Array persisten terlibat.
14. Current Quest State bila quest lintas turn relevan.
15. Player intent.

## Modular Fetch / Trigger Contract
- Setiap Player Message adalah turn baru dan wajib memulai dengan fresh fetch `INDEX.md` dari repository.
- Setelah INDEX berhasil, GM mendeteksi trigger dan fetch **REQUIRED modules only** sebelum validasi/resolusi. Optional modules hanya dimuat bila diperlukan.
- Trigger → Module registry berada di `systems/27_MODULE_ROUTER.md`.
- Jika `INDEX.md` gagal: `REPOSITORY FETCH FAILURE` dan hentikan resolusi.
- Jika modul REQUIRED gagal: `REPOSITORY MODULE FETCH FAILURE` dan tahan resolusi yang bergantung pada modul tersebut.
- Tidak boleh silent fallback ke INDEX/cache lama.

## Runtime Prompt Contract
- `gm/PLAYER_BOOT_PROMPT.md` digunakan sekali pada boot karakter/sesi baru untuk memuat World Bible, current state, dan memory yang relevan.
- `gm/ACTION_RUNTIME_PROMPT.md` digunakan pada setiap aksi gameplay berikutnya.
- **Setiap Player message adalah turn baru dan wajib memulai dengan fresh fetch/verification `INDEX.md` dari repository sebelum membaca/menilai state atau memproses intent. Tidak boleh memakai INDEX, state, atau hasil load dari turn sebelumnya sebagai pengganti fresh fetch.**
- **Jika tool fetch tersedia, panggilan fetch `INDEX.md` harus menjadi operasi repository pertama pada setiap turn. AI GM dilarang menghasilkan resolusi gameplay sebelum hasil fetch tersebut berhasil dibaca.**
- Setelah INDEX fresh berhasil dibaca, AI GM wajib mengikuti Load Order dan melakukan fetch ulang setiap sumber state yang diperlukan untuk turn tersebut.
- `systems/27_MODULE_ROUTER.md` menentukan trigger dan modul REQUIRED/OPTIONAL setelah INDEX fresh berhasil.
- `systems/28_ORGANIZATION_PERSISTENCE.md` wajib diproses bila organisasi, membership, rank, contract, access, atau perubahan state organisasi persisten terlibat.
- `systems/29_NPC_PERSISTENCE.md` wajib diproses bila NPC menjadi persisten/recurring atau terjadi perubahan NPC yang memerlukan continuity lintas turn.
- `systems/30_EVENT_QUEST_PERSISTENCE.md` wajib diproses bila Event/Quest menjadi persisten, lintas turn, material, atau reward/state-nya berubah.
- `systems/31_CRAFTING_FORGING.md` wajib diproses bila crafting, forging, smithing, material processing, recipe execution, atau pembuatan item baru menjadi relevan.
- `systems/32_ALCHEMY_PILLS.md` wajib diproses bila alchemy, pill refinement, formula alchemy, furnace process, atau produk alkimia menjadi relevan.
- `systems/33_FORMATION_ARRAYS.md` wajib diproses bila blueprint, construction, activation, operation, disruption, repair, atau combat interaction Formation/Array menjadi relevan.
- `systems/34_ARTIFACT_WEAPON_REFINEMENT.md` wajib diproses bila existing item/artifact/weapon diperbaiki, ditempa ulang, diperkuat, di-refine, di-upgrade, atau mengalami perubahan property/quality/condition melalui refinement.
- `bestiary/00_BESTIARY_DATABASE.md` adalah fixed Bestiary opsional; fixed entry diprioritaskan hanya bila source secara eksplisit tercakup dan tidak membatasi Dynamic Generation.
- Organisasi dapat menggunakan database registry + individual organization file; individual file menjadi detail utama bila tersedia.
- Setiap aksi yang menghasilkan perubahan material wajib melewati Save Pipeline.
- Setelah resolusi tervalidasi, AI GM wajib memperbarui Current Character State dan memory persisten yang relevan melalui integrasi repository yang tersedia; bila Spirit Beast terlibat, Current Beast State dan Beast History juga wajib diproses sesuai Module 24; bila NPC persisten atau Quest State berubah, entity state/history yang relevan juga wajib diproses sesuai Module 26 dan persistence modules.
- Perubahan hasil produksi pada Module 31–34 wajib mempertahankan provenance material/item, before → after, Origin, dan integrity lintas entity sesuai `gm/STATE_VALIDATOR.md` dan `gm/SAVE_PIPELINE.md`.
- Formation/Array persisten wajib mempertahankan `FORM-####`/`ARRAYCORE-####`, Current State, Registry, dan History sesuai Module 33.
- Kedua prompt wajib mengikuti Runtime Engine, Core Rules, Save Integrity, ID/Save System, dan seluruh sumber yang ditunjuk INDEX.
- `systems/23_GARDENING.md` wajib dimuat ketika berkebun, tanaman, kebun, pertumbuhan tanaman, atau hasil panen menjadi relevan terhadap aksi/runtime.
- `systems/24_SPIRIT_BEASTS.md` wajib dimuat ketika Spirit Beast, taming, ownership, contract, Beast combat, Beast growth/evolution, Beast state, atau Beast history menjadi relevan terhadap aksi/runtime.
- `systems/25_DYNAMIC_GENERATION.md` wajib dimuat ketika dynamic encounter, Monster generation, Spirit Beast generation, Threat/Tier generation, loot generation, atau loot resolution tanpa fixed table menjadi relevan terhadap aksi/runtime.
- `systems/26_DYNAMIC_NPC_EVENT_QUEST.md` wajib dimuat ketika dynamic NPC generation, local event generation/resolution, quest generation/resolution, persistent NPC, persistent quest, atau NPC/Event/Quest relationship menjadi relevan terhadap aksi/runtime.
- `systems/27_MODULE_ROUTER.md` wajib digunakan untuk menentukan modul REQUIRED/OPTIONAL setelah INDEX fresh berhasil.
- `loot/00_LOOT_TABLE_DATABASE.md` dimuat bila fixed loot table, unique reward, atau content table tertentu perlu diperiksa; registry tersebut tidak membatasi dynamic loot.
- `gm/PENDING_SYNC.md` wajib digunakan ketika write-back repository tidak tersedia atau gagal; pending changes bukan Canon tersinkron sampai diverifikasi dan ditulis oleh Admin.
- `core/07_DATA_COMPLETENESS.md` wajib digunakan ketika field data belum lengkap, placeholder muncul, atau audit menemukan status unresolved. Runtime memakai status `NOT-INSTANTIATED`, `NOT-ESTABLISHED`, atau `RESOLUTION-BLOCKED` sesuai konteks; tanda tanya bukan placeholder repository.
