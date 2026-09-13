# 18 — LOOT

## 1. Sumber
Loot berasal dari:
- monster/spirit beast;
- peti atau lokasi;
- musuh;
- event;
- reward misi;
- sumber resmi lainnya.

Sumber loot dapat menggunakan **Dynamic Loot Generation** atau fixed loot table yang secara eksplisit ditetapkan Admin/Canon.

## 2. Dynamic Loot Principle
TianDao World tidak memakai katalog drop global. Untuk source yang tidak memiliki fixed table, GM menghasilkan loot secara dinamis menggunakan `systems/25_DYNAMIC_GENERATION.md`.

Dynamic generation mempertimbangkan source, Tier, habitat, metode perolehan, condition, dan special event. Faktor tersebut menghasilkan batas kualitas potensial; tidak menjamin item tertentu atau rarity tertentu.

## 3. Validasi
Loot hanya diberikan setelah kondisi perolehan terpenuhi. GM tidak menjamin item langka.

Runtime:

`Valid Source → Valid Acquisition → Loot Potential → Loot Band → Dynamic Result → Item Validation → Origin`

## 4. Fixed Loot Table
Fixed loot table adalah pengecualian untuk content yang memang sengaja ditetapkan Admin/Canon, misalnya unique boss, named reward, quest/event reward, atau item unik.

Registry fixed table:
`loot/00_LOOT_TABLE_DATABASE.md`

Prioritas:

`Fixed Canon/Event/Mission Table → Dynamic Loot Formula → hasil belum ditentukan (???)`

Fixed table hanya berlaku pada source yang secara eksplisit dicakup. Ia tidak menjadi batas bagi species, monster, Spirit Beast, atau loot lain di dunia.

## 5. Dynamic Loot Formula
Formula canonical berada di `systems/25_DYNAMIC_GENERATION.md`.

`Loot Potential = clamp(Source Tier Score + Habitat Score + Harvest/Defeat Method + Condition + Special Event, 0, 100)`

`Loot Band = band(Loot Potential)`

`Quantity = 1 + floor(Loot Potential / 25)` untuk source creature normal.

Quantity formula tersebut tidak otomatis berlaku untuk chest, currency, reward bundle, event, atau source khusus yang memiliki rule berbeda.

## 6. Loot Selection Rules
GM memilih hasil yang sesuai dengan source:
- material tubuh hanya jika secara biologis/logis dapat diperoleh;
- resource habitat hanya jika benar-benar tersedia;
- equipment/item hanya jika metode acquisition mendukung;
- currency hanya jika source/context mendukung;
- unique/legendary item hanya jika Canon/Event/Admin mechanism mendukung.

Loot result tidak boleh memperoleh stat, effect, value, atau rarity mekanis yang tidak memiliki dasar valid.

## 7. No Automatic Guarantee
Tier, Realm, habitat, difficulty, atau nama species tidak otomatis menjamin loot tertentu.

Loot Band adalah ceiling/quality range generator, bukan jaminan bahwa setiap hasil mencapai band tersebut.

Tidak ada automatic rare drop, guaranteed material, atau guaranteed currency.

## 8. Kepemilikan
Loot yang berhasil diperoleh langsung menjadi bagian dari Item Origin Log dengan sumber dan timestamp. Item tidak masuk Inventory sebelum perolehan dan kepemilikannya tervalidasi.

## 9. Distribusi
Jika beberapa pihak berhak atas loot, pembagian mengikuti kepemilikan, kesepakatan, hukum faction, atau hasil konflik yang sah. GM tidak boleh menetapkan pembagian numerik tanpa dasar yang sah.

## 10. Origin & Anti-Duplikasi
Setiap loot yang benar-benar diperoleh harus dapat ditelusuri ke sumber, kondisi perolehan, waktu, dan perubahan kepemilikan melalui Item Origin Log.

Item unik/terbatas tidak dapat diduplikasi melalui klaim player, reload state, atau retcon.

Generated loot yang belum menjadi gameplay fact tidak boleh dianggap tersimpan di dunia.

## 11. Missing Data
Jika input yang diperlukan oleh formula tidak tersedia dan tidak ada rule fallback, GM menggunakan `???` untuk field tersebut atau menahan hasil mekanis yang tidak dapat divalidasi.

`???` bukan izin untuk mengarang angka.

## 12. Integration
Loot terhubung dengan Combat, Monsters, Events, Items, Economy, Organizations, Karma, Reputation, Save Integrity, dan Dynamic Generation Engine.

## 13. Prinsip Runtime

Tidak ada fallback numerik tersembunyi.

Namun, ketiadaan fixed loot table **bukan lagi larangan menghasilkan loot**. Source yang valid dapat menggunakan Dynamic Loot Formula. Fixed table hanya dipakai ketika memang tersedia dan berlaku.
