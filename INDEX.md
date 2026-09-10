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
- `realms/02_CENTRAL_PLAINS.md`
- `realms/03_AZURE_MOUNTAIN.md`
- `realms/04_SOUTHERN_DEMON_DOMAIN.md`
- `realms/05_EASTERN_SEA.md`
- `realms/06_NORTHERN_DESOLATE.md`
- `realms/07_WESTERN_SACRED_DESERT.md`

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

## Characters
- `characters/players.md` — Player Registry
- `characters/character_registry.md` — Character Registry
- `characters/players/` — Individual Current Character State files

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
3. Relevant realm/system modules.
4. Faction databases dan city/NPC databases bila relevan.
5. Lore yang relevan.
6. Current character state yang sesuai dengan Character ID aktif.
7. Player intent.

## Runtime Prompt Contract
- `gm/PLAYER_BOOT_PROMPT.md` digunakan sekali pada boot karakter/sesi baru untuk memuat World Bible dan current state.
- `gm/ACTION_RUNTIME_PROMPT.md` digunakan pada setiap aksi gameplay berikutnya.
- Kedua prompt wajib mengikuti Runtime Engine, Core Rules, Save Integrity, ID/Save System, dan seluruh sumber yang ditunjuk INDEX.
