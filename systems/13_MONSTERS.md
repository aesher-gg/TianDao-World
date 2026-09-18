# 13 — MONSTERS

## 1. Dynamic Encounter Principle
Monster dan Spirit Beast **tidak berasal dari katalog tertutup**. Encounter dibuat secara dinamis oleh GM menggunakan `systems/25_DYNAMIC_GENERATION.md`, World Bible, habitat/region, world time, event, dan current context.

Canon/Custom database tetap dapat menetapkan creature tertentu bila memang diperlukan, tetapi database fixed bukan batas jumlah species di dunia.

Spirit Beast adalah subset khusus makhluk yang dapat memiliki persistent identity dan lifecycle melalui `systems/24_SPIRIT_BEASTS.md`. Tidak setiap monster otomatis merupakan Spirit Beast.

## 2. Encounter Resolution
Runtime mengikuti:

`Region/Habitat → Encounter Pressure → d100 Roll → Encounter Composition → Threat Score → Creature Generation`

Encounter Pressure dan Threat Score dihitung menurut `systems/25_DYNAMIC_GENERATION.md`.

GM boleh menghasilkan species/archetype baru selama hasil tersebut:
- sesuai habitat dan ekologi;
- tidak bertentangan dengan Canon/Custom;
- tidak melewati Threat/Tier ceiling tanpa override resmi;
- tidak memperoleh ability, technique, bloodline, atau loot khusus secara gratis;
- melewati validation sebelum menjadi gameplay fact.

## 3. Data Encounter
Encounter dapat memuat:
- identitas/species atau generated archetype;
- tier dan realm bila berlaku;
- lokasi/habitat;
- perilaku;
- agresivitas;
- kemampuan yang valid;
- kelemahan jika diketahui karakter;
- loot source/resolution bila loot kemudian diperoleh.

Jika encounter melibatkan Spirit Beast yang telah memiliki BEAST_ID, runtime wajib menggunakan Current Beast State/Beast History yang sesuai dan tidak membuat entity baru dengan identitas berbeda.

## 4. AI Makhluk
Monster bertindak berdasarkan naluri, habitat, kondisi, generated traits, dan context. Spirit Beast juga mempertahankan otonomi sesuai intelligence, temperament, relationship, taming, ownership, contract, condition, dan aturan Module 24.

Mereka tidak otomatis menyerang, jinak, setia, memiliki, atau kalah.

## 5. Tier vs Realm
Tier makhluk dan realm adalah atribut terpisah kecuali modul resmi menyatakan hubungan. Jangan mengubah tier menjadi realm secara otomatis. Spirit Beast mengikuti aturan yang sama; realm/stage hanya berlaku bila didukung species/system/context.

Dynamic Tier ceiling ditentukan oleh Threat Score, bukan oleh Realm Character. Character Realm tidak otomatis menaikkan Tier encounter.

## 6. Loot Integration
Loot dihasilkan setelah acquisition/combat/harvest yang sah dan mengikuti `systems/18_LOOT.md` serta Dynamic Loot Formula di `systems/25_DYNAMIC_GENERATION.md`.

Fixed loot table hanya mengoverride formula untuk source yang secara eksplisit dicakup table. Tidak ada global drop catalog yang membatasi monster dunia.

Spirit Beast yang dimiliki/berkontrak tidak diperlakukan sebagai loot/item.

## 7. Integration
Monster memakai Combat, Vitality, Items, Loot, Geography, Time, Travel, Events, dan Reputation/Karma jika perilaku atau konsekuensinya melibatkan pihak lain.

Dynamic generation memakai `systems/25_DYNAMIC_GENERATION.md`.

Spirit Beast memakai modul-modul tersebut bila relevan dan menggunakan `systems/24_SPIRIT_BEASTS.md` untuk relationship, taming, ownership, contract, growth/evolution, lifecycle, state, history, dan save integration.

## 8. MONSTER INDIVIDUAL PERSISTENCE GATE
Monster encounter biasa tidak menjadi persistent entity. Namun, bila satu individu Monster menjadi **recurring/material** dan continuity lintas turn memengaruhi resolusi, runtime wajib menginstansiasinya sebagai entity terpisah.

### Persistence classes
- **ENCOUNTER-ONLY:** hasil encounter selesai tanpa kebutuhan continuity → tidak membuat ID/state/history.
- **MATERIAL-RECURRING:** individu yang kembali muncul, memiliki kondisi/lokasi/riwayat yang memengaruhi turn berikutnya, menjadi target quest/event material, atau memiliki konsekuensi individual yang harus dilacak → wajib memiliki `MONSTER_ID` stabil.
- **DECEASED/ARCHIVED:** individu yang mati permanen/diarsipkan mempertahankan record historis; `MONSTER_ID` tidak boleh dipakai ulang.

Canonical persistence paths:
- `characters/monster_registry.md` — registry mapping `MONSTER_ID` → Current Monster State/History.
- `characters/monsters/<MONSTER_ID>.md` — current state individual Monster.
- `monster_history/<MONSTER_ID>_HISTORY.md` — append-oriented history.

Minimum persistent Monster State:
`MONSTER_ID / Species-or-Archetype / Classification / Tier / Realm-or-UNRESOLVED / Current Location / Habitat / HP / Condition / Temperament / Behavior / Status / Origin / Last World Time`.

`MONSTER_ID` adalah identity individu, bukan species ID. Species dapat tetap `RUNTIME-GENERATED` dan tidak menjadi Global Canon hanya karena individu dipersistenkan.

Persistence tidak berarti ownership, taming, loyalty, contract, atau loot. Monster tetap independen. Loot hanya diproses melalui Module 18/25 setelah acquisition yang sah.

### Monster persistence transaction
Jika encounter/action mengubah Monster persistent:
`LOAD MONSTER STATE/HISTORY → VALIDATE → RESOLVE → BEFORE/AFTER → ORIGIN → MONSTER HISTORY → SAVE → WRITE-BACK VERIFY`.

Jika satu action mengubah Character + Monster + Item/Loot + Event/World consequence, setiap entity yang berubah harus memiliki before→after dan Origin sendiri. Jangan menyimpan Character saja.

Generated Monster yang belum membutuhkan continuity tetap `RUNTIME-GENERATED` dan tidak dibuat persistent hanya untuk mengisi database.
