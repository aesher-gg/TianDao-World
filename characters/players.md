# Player Registry

Registry resmi Player yang terdaftar di TianDao-World.

> File ini adalah registry identitas dan pemetaan Player → Character. Bukan current save system.

## Registered Players

### PLAYER-0001
- **Player ID:** PLAYER-0001
- **Status:** Active
- **Character(s):** CHAR-0001
- **Character Name:** Ryxian
- **Character Registry:** `characters/character_registry.md`
- **Current State:** `characters/players/CHAR-0001.md`

## Registry Rules

- Player ID harus unik dan stabil.
- Nama/username Player bukan primary identifier.
- Current gameplay state tidak disimpan di file ini.
- Setiap Character memiliki Character ID unik dan state file terpisah.
- `players.md` digunakan untuk registry dan data awal yang diperlukan saat pembuatan/boot karakter baru.
- Setelah karakter aktif bermain, Current Character State menjadi sumber state operasional.
