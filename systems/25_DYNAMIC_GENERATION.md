# 25 — DYNAMIC ENCOUNTER & GENERATION ENGINE

> Status: Admin Canon — Dynamic Generation Formula v1.0
> Tujuan: menyediakan formula generatif untuk encounter, Monster, Spirit Beast, dan Loot tanpa membuat TianDao World menjadi katalog spesies/item tertutup.

## 0. PRINCIPLE

TianDao World menggunakan **open-world procedural generation**.

Admin menetapkan formula, batas, validasi, dan sumber input. GM/Qwen menentukan hasil konkret pada runtime: spesies, varian, perilaku, encounter, Beast identity, dan loot yang benar-benar muncul.

Generated content **bukan Global Canon** hanya karena muncul. Ia menjadi fakta gameplay setelah resolution sah, state/history/origin diterapkan bila relevan, dan write-back berhasil sesuai Save Pipeline.

Database spesifik tetap boleh digunakan untuk content yang memang sengaja fixed: unique boss, named creature, quest reward, event reward, unique item, atau content lain yang secara eksplisit ditetapkan Admin. Database fixed adalah pengecualian, bukan fondasi generasi dunia.

---

## 1. INPUT HIERARCHY

Formula hanya menggunakan input yang tersedia dan tervalidasi.

Prioritas:

`Canon/Admin Data → Current State → World Time → Geography/Habitat → Active Event/Thread → Character Context → Runtime Roll → GM Narrative`

Jika input mekanis tidak tersedia dan formula tidak mendefinisikan fallback, nilai tersebut adalah `???` dan GM tidak boleh mengarang angka pengganti.

---

## 2. ENCOUNTER PRESSURE

Encounter Pressure adalah peluang dasar bahwa encounter liar yang relevan dapat terjadi pada satu opportunity/check runtime.

### 2.1 Base Pressure

| Tekanan Ekosistem | Base Pressure |
|---|---:|
| Sangat rendah | 5 |
| Rendah | 20 |
| Sedang | 40 |
| Tinggi | 65 |
| Tidak ditentukan | `???` |

Nilai di atas adalah **Admin Canon mapping** untuk mengubah label ekologis menjadi input formula. Ini bukan jaminan encounter.

### 2.2 Modifiers

Setiap modifier berikut bernilai antara -10 sampai +10 dan hanya digunakan bila kondisi tersebut benar-benar relevan:

- Waktu aktif makhluk: -10 sampai +10
- Musim: -10 sampai +10
- Cuaca: -10 sampai +10
- Kepadatan/aktivitas manusia: -10 sampai +10
- Aktivitas Character/kelompok: -10 sampai +10
- Active Event/World Thread: -10 sampai +10
- Gangguan baru/jejak mangsa/sisa pertempuran: -10 sampai +10

GM memilih nilai dalam rentang tersebut berdasarkan keadaan naratif yang telah diketahui; tidak boleh menciptakan modifier hanya untuk memaksa encounter.

### 2.3 Formula

`Encounter Pressure = clamp(Base Pressure + Σ Modifier, 0, 95)`

Kemudian:

`Roll = d100`

`Encounter terjadi jika Roll ≤ Encounter Pressure`.

Satu roll tidak menjamin jumlah makhluk tertentu. Jumlah dan komposisi ditentukan pada tahap Encounter Composition dan harus tetap masuk akal terhadap habitat, threat, dan context.

Jika pressure = `???`, encounter tidak boleh dipaksakan melalui angka.

---

## 3. ENCOUNTER COMPOSITION

Setelah encounter berhasil, GM menentukan:

1. creature category;
2. species/archetype;
3. jumlah;
4. perilaku awal;
5. posisi/jarak relatif bila relevan;
6. kondisi lingkungan;
7. Threat Score;
8. Tier/Realm/Stage hanya bila supported;
9. apakah creature merupakan Spirit Beast-capable/Spirit Beast actual;
10. loot source bila nanti relevan.

Tidak ada tabel global yang membatasi species. Species dapat berupa spesies baru yang masuk akal terhadap habitat dan tidak bertentangan dengan Canon.

---

## 4. THREAT SCORE

Threat Score menentukan **kelas ancaman encounter**, bukan identitas spesies dan bukan Realm otomatis.

### 4.1 Area Threat Base

| Tekanan Ekosistem | Area Threat Base |
|---|---:|
| Sangat rendah | 10 |
| Rendah | 25 |
| Sedang | 50 |
| Tinggi | 75 |
| Tidak ditentukan | `???` |

### 4.2 Threat Modifiers

- Environmental hazard: 0–10
- Active event/anomaly: 0–15
- Predator/prey disturbance: 0–10
- Human conflict/activity: 0–10
- Rare habitat condition: 0–10

Modifier hanya ditambahkan bila terdapat alasan yang terlihat/tervalidasi. Active Event/Canon dapat melampaui rentang normal hanya jika sumber tersebut memang mendefinisikan override.

`Threat Score = clamp(Area Threat Base + Σ Threat Modifier, 0, 100)`

### 4.3 Dynamic Tier Band

Threat Score memetakan **maksimum Tier encounter normal**:

| Threat Score | Normal Tier Ceiling |
|---:|---|
| 0–19 | Tier 1 |
| 20–39 | Tier 2 |
| 40–59 | Tier 3 |
| 60–79 | Tier 4 |
| 80–94 | Tier 5 |
| 95–100 | Tier 6 |

GM tidak harus menghasilkan Tier maksimum. Hasil aktual boleh berada di bawah ceiling.

**Tier 6 bukan batas absolut dunia.** Event/World Canon/Admin override dapat membuka threat di atas rentang normal. Tanpa override, GM tidak boleh melampaui ceiling.

### 4.4 Tier ≠ Realm

Tier makhluk tidak dikonversi menjadi Realm.

Jika creature generated tidak memiliki dasar untuk cultivation realm/stage, field tersebut tetap `???` atau `N/A` sesuai apakah atributnya memang berlaku untuk species tersebut.

---

## 5. CREATURE GENERATION

Generator creature memakai kombinasi input, bukan katalog tetap:

`Region + Habitat + Threat Band + Environment + World Time + Season + Weather + Food/Resource Pressure + Human Activity + Active Event + Creature Archetype`

GM kemudian menentukan:

- Species Name;
- Classification;
- physical/ecological traits;
- temperament;
- intelligence;
- behavior;
- aggression;
- abilities/techniques **hanya jika valid secara internal atau berasal dari generated design yang tidak melanggar system**;
- weaknesses bila masuk akal dan dapat diketahui karakter;
- Tier dari Threat Band;
- Realm/Stage hanya bila system/species logic mendukung.

Generated creature tidak boleh otomatis memiliki teknik kultivasi, bloodline langka, unique ability, atau loot bernilai tinggi hanya karena namanya terdengar langka.

---

## 6. SPIRIT BEAST GENERATION

Spirit Beast adalah jalur generasi khusus dari creature generation, lalu mengikuti seluruh lifecycle Module 24.

Formula konseptual:

`Habitat + Spiritual Environment + Creature Archetype + Intelligence + Temperament + Growth Potential + Spiritual Affinity + Threat/Tier → Spirit Beast Candidate`

GM menentukan apakah candidate memang memenuhi definisi Spirit Beast. Tidak semua creature harus Spirit Beast.

### 6.1 Generated Beast Identity

Jika candidate menjadi persistent Spirit Beast:

- buat `BEAST_ID` baru yang global-unique;
- buat Current Beast State;
- buat Beast History;
- catat Origin;
- jangan gunakan BEAST_ID untuk creature lain;
- generated Beast tidak menjadi global species Canon.

Nama, species, traits, temperament, dan growth potential dapat berbeda antar individu dari archetype yang sama.

### 6.2 Tier, Realm, Growth

- Tier ditentukan oleh Threat/Tier resolution.
- Realm hanya bila didukung.
- Growth tidak otomatis = Evolution.
- Evolution hanya melalui mechanism/requirement Module 24.
- Tidak ada automatic taming, ownership, contract, loyalty, atau bond.

---

## 7. LOOT GENERATION

Loot tidak lagi bergantung pada katalog drop global. Loot dapat dihasilkan secara dinamis setelah sumber loot sah.

### 7.1 Loot Eligibility

`Loot Eligible = valid source + valid acquisition method + resolution succeeded`

Sumber dapat berupa creature, lokasi, chest, enemy, event, mission, atau sumber resmi lain.

### 7.2 Loot Potential Score

Untuk sumber creature/monster/Spirit Beast:

`Loot Potential = Source Tier Score + Habitat Score + Harvest/Defeat Method + Condition + Special Event`

Masing-masing komponen dinormalisasi 0–20.

- Source Tier Score: Tier 1 = 2, Tier 2 = 5, Tier 3 = 8, Tier 4 = 11, Tier 5 = 15, Tier 6 = 18. Tier di atas 6 menggunakan nilai resmi/override; tanpa override gunakan `???`.
- Habitat Score: 0–20 berdasarkan kelangkaan sumber daya habitat yang benar-benar tercatat/terlihat.
- Harvest/Defeat Method: 0–20 berdasarkan apakah source berhasil dipanen/diperoleh secara utuh, rusak, terbakar, tercemar, atau metode lain yang relevan. GM tidak boleh mengubah deskripsi kualitatif menjadi angka tanpa memilih nilai dari rentang Admin ini berdasarkan hasil aktual.
- Condition: 0–20 berdasarkan kondisi source saat diperoleh.
- Special Event: 0–20 hanya jika event/condition resmi atau runtime yang sah memang memberikan pengaruh.

`Loot Potential = clamp(Σ components, 0, 100)`

Loot Potential menentukan kualitas potensial, bukan menjamin drop.

### 7.3 Loot Band

| Loot Potential | Band |
|---:|---|
| 0–19 | Common |
| 20–39 | Uncommon |
| 40–59 | Rare |
| 60–79 | Very Rare |
| 80–94 | Exceptional |
| 95–100 | Exceptional+ |

Band hanya batas generatif. GM tetap harus memastikan item masuk akal terhadap source dan Item System.

### 7.4 Quantity

Jumlah item yang dihasilkan secara dinamis memakai:

`Quantity = 1 + floor(Loot Potential / 25)`

sehingga rentang normal adalah 1–5 unit.

**Pengecualian:** material massal, currency, reward bundle, chest, event, atau source lain dapat memiliki quantity formula sendiri bila Admin/system mendefinisikannya. Jangan mengaplikasikan quantity creature biasa ke sumber yang berbeda.

### 7.5 Loot Type Selection

GM memilih jenis hasil berdasarkan source, bukan tabel global:

- material tubuh hanya jika creature secara biologis/logis memiliki material yang dapat diambil;
- resource habitat hanya jika benar-benar tersedia;
- equipment/item hanya jika source acquisition method mendukung;
- currency hanya jika source/context mendukung;
- unique/legendary item hanya jika Canon/Event/Admin mechanism mendukung.

Loot harus tetap konsisten dengan `systems/14_ITEMS.md`.

### 7.6 Rarity Anti-Guarantee

Loot Band **tidak berarti semua unit loot memiliki rarity tersebut**. Band adalah ceiling/quality range generator.

GM boleh menghasilkan hasil di bawah ceiling. Tidak ada automatic rare drop.

Jika Item ID/definition diperlukan oleh Item System dan belum tersedia, GM tidak boleh menciptakan efek/stat/value mekanis secara diam-diam. Gunakan item generated dengan definisi minimal yang valid, atau `???` untuk field yang belum dapat ditentukan.

---

## 8. FIXED TABLE OVERRIDE

Loot table spesifik tetap sah bila sengaja dibuat Admin untuk content fixed.

Prioritas:

`Fixed Canon/Event/Mission Table → Dynamic Loot Formula → ???`

Fixed table mengoverride formula hanya untuk source yang secara eksplisit dicakup table tersebut.

`loot/00_LOOT_TABLE_DATABASE.md` adalah registry optional untuk fixed table, bukan batas dunia dan bukan sumber wajib bagi setiap encounter.

---

## 9. ANTI-CATALOG RULE

Generator dilarang mengubah hasil runtime menjadi daftar global hanya karena hasil tersebut pernah muncul.

Contoh:

- Beast baru → bukan berarti hanya ada satu species tersebut di dunia.
- Monster baru → bukan berarti species itu satu-satunya species habitat.
- Loot baru → bukan berarti semua monster jenis itu selalu menjatuhkan item tersebut.

Setiap encounter dihitung dari context runtime.

---

## 10. ANTI-SCALING / ANTI-PLAYER-FOLLOWING

Generator tidak boleh menyesuaikan monster atau loot secara otomatis hanya agar cocok dengan Realm Character.

Character Context boleh memengaruhi:
- kemungkinan bertemu;
- perhatian makhluk;
- perilaku;
- pemilihan route/area;
- konsekuensi encounter;
- apakah Character mampu melihat/mengenali ancaman.

Tetapi Character Realm tidak otomatis menaikkan Tier, loot rarity, atau reward.

---

## 11. VALIDATION GATE

Sebelum hasil generator diterapkan:

1. habitat/region valid;
2. encounter pressure memiliki source;
3. threat score memiliki source input;
4. Tier tidak melewati ceiling tanpa override;
5. Tier ≠ Realm;
6. generated creature tidak melanggar Canon;
7. ability/technique memiliki dasar yang valid;
8. Spirit Beast mengikuti Module 24;
9. BEAST_ID unique jika persistent;
10. loot hanya setelah acquisition valid;
11. loot quantity/quality mengikuti formula atau fixed table yang berlaku;
12. item ownership memiliki Origin;
13. material changes memiliki Origin Log;
14. state/history/save pipeline lulus validator;
15. write-back diverifikasi sebelum disebut synchronized.

Jika gate gagal, hasil mekanis yang gagal validasi tidak diterapkan.

---

## 12. RUNTIME PIPELINE

```text
WORLD CONTEXT
→ HABITAT/REGION
→ ENCOUNTER PRESSURE
→ d100 ENCOUNTER ROLL
→ ENCOUNTER COMPOSITION
→ THREAT SCORE
→ CREATURE GENERATION
→ COMBAT/INTERACTION
→ LOOT ELIGIBILITY
→ LOOT POTENTIAL
→ LOOT GENERATION
→ SPIRIT BEAST LIFECYCLE (jika relevan)
→ VALIDATION
→ ORIGIN/HISTORY
→ SAVE
→ WRITE-BACK VERIFY
```

Untuk Spirit Beast yang sudah persistent, LOAD EXISTING BEAST STATE/HISTORY terlebih dahulu; generator tidak boleh membuat duplicate entity.

---

## 13. FORMULA SUMMARY

### Encounter
`Pressure = clamp(BasePressure + ΣEncounterModifiers, 0, 95)`

`Encounter = d100 ≤ Pressure`

### Threat
`ThreatScore = clamp(AreaThreatBase + ΣThreatModifiers, 0, 100)`

`TierCeiling = band(ThreatScore)`

### Spirit Beast
`Habitat + SpiritualEnvironment + Archetype + Intelligence + Temperament + GrowthPotential + Affinity + Threat → Candidate`

### Loot
`LootPotential = clamp(SourceTierScore + HabitatScore + HarvestMethod + Condition + SpecialEvent, 0, 100)`

`LootBand = band(LootPotential)`

`Quantity = 1 + floor(LootPotential / 25)`

Semua formula di atas adalah Admin Canon v1.0 dan dapat diperbarui oleh Admin melalui perubahan Canon yang terdokumentasi.
