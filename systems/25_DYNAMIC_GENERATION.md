# 25 — DYNAMIC ENCOUNTER & GENERATION ENGINE

> Status: Admin Canon — Dynamic Generation Formula v1.0
> Tujuan: menyediakan formula generatif untuk encounter, Monster, Spirit Beast, dan Loot tanpa membuat TianDao World menjadi katalog tertutup.

## 0. PRINCIPLE
Admin menetapkan formula, batas, validasi, dan sumber input. GM/Qwen menentukan hasil konkret pada runtime. Generated content bukan Global Canon hanya karena muncul; menjadi fakta gameplay setelah resolusi sah, state/history/origin diterapkan bila relevan, dan write-back berhasil sesuai Save Pipeline.

Fixed database tetap sah untuk content yang memang ditetapkan Admin. Fixed content adalah pengecualian, bukan fondasi generasi dunia.

## 1. INPUT HIERARCHY
`Canon/Admin Data → Current State → World Time → Geography/Habitat → Active Event/Thread → Character Context → Runtime Roll → GM Narrative`

Jika input mekanis tidak tersedia dan tidak memiliki fallback resmi, gunakan status `UNRESOLVED` dan tahan resolusi numerik yang bergantung padanya.

## 2. ENCOUNTER PRESSURE
### Base Pressure
| Tekanan Ekosistem | Base Pressure |
|---|---:|
| Sangat rendah | 5 |
| Rendah | 20 |
| Sedang | 40 |
| Tinggi | 65 |
| Tidak ditentukan | UNRESOLVED |

Modifier relevan: waktu, musim, cuaca, kepadatan/aktivitas manusia, aktivitas Character, Active Event/World Thread, gangguan/jejak mangsa/sisa pertempuran; masing-masing -10 sampai +10 bila memang didukung konteks.

`Encounter Pressure = clamp(Base Pressure + Σ Modifier, 0, 95)`

`Roll = d100`; encounter terjadi jika `Roll ≤ Encounter Pressure`.

Jika pressure `UNRESOLVED`, jangan dipaksa menjadi angka.

## 3. ENCOUNTER COMPOSITION
Setelah encounter berhasil, tentukan category, species/archetype, jumlah, perilaku awal, posisi relatif bila relevan, lingkungan, Threat Score, Tier/Realm/Stage bila didukung, status Spirit Beast bila relevan, dan loot source bila nantinya diperoleh.

Tidak ada katalog species global. Generated species harus ekologis dan tidak bertentangan dengan Canon.

## 4. THREAT SCORE
### Area Threat Base
| Tekanan Ekosistem | Area Threat Base |
|---|---:|
| Sangat rendah | 10 |
| Rendah | 25 |
| Sedang | 50 |
| Tinggi | 75 |
| Tidak ditentukan | UNRESOLVED |

Threat modifiers yang sah: environmental hazard 0–10, active event/anomaly 0–15, predator/prey disturbance 0–10, human conflict/activity 0–10, rare habitat condition 0–10.

`Threat Score = clamp(Area Threat Base + Σ Threat Modifier, 0, 100)`

| Threat Score | Tier Ceiling |
|---:|---|
| 0–19 | Tier 1 |
| 20–39 | Tier 2 |
| 40–59 | Tier 3 |
| 60–79 | Tier 4 |
| 80–94 | Tier 5 |
| 95–100 | Tier 6 |

Tier ceiling bukan kewajiban dan Tier ≠ Realm. Event/World Canon/Admin dapat memberi override resmi.

## 5. CREATURE GENERATION
Input: `Region + Habitat + Threat Band + Environment + World Time + Season + Weather + Food/Resource Pressure + Human Activity + Active Event + Creature Archetype`.

Generated creature dapat memiliki species, physical/ecological traits, temperament, intelligence, behavior, aggression, weakness, dan kemampuan yang valid. Teknik kultivasi, bloodline langka, unique ability, dan loot bernilai tinggi tidak boleh diberikan hanya karena nama creature terdengar langka.

## 6. SPIRIT BEAST GENERATION
`Habitat + Spiritual Environment + Creature Archetype + Intelligence + Temperament + Growth Potential + Spiritual Affinity + Threat/Tier → Spirit Beast Candidate`

Candidate mengikuti Module 24. Jika menjadi persistent Beast, buat BEAST_ID global-unique, State, History, dan Origin. Dynamic generation tidak otomatis memberi taming, ownership, contract, loyalty/bond, rare bloodline, technique/ability khusus, atau evolution.

## 7. LOOT GENERATION
### Eligibility
`Loot Eligible = valid source + valid acquisition method + resolution succeeded`

### Loot Potential
Untuk creature/monster/Spirit Beast:
`Loot Potential = Source Tier Score + Habitat Score + Harvest/Defeat Method + Condition + Special Event`

Komponen dinormalisasi 0–20. Source Tier Score: Tier 1=2, Tier 2=5, Tier 3=8, Tier 4=11, Tier 5=15, Tier 6=18. Tier di atas 6 memerlukan override resmi.

`Loot Potential = clamp(Σ components, 0, 100)`

| Loot Potential | Band |
|---:|---|
| 0–19 | Common |
| 20–39 | Uncommon |
| 40–59 | Rare |
| 60–79 | Very Rare |
| 80–94 | Exceptional |
| 95–100 | Exceptional+ |

`Quantity = 1 + floor(Loot Potential / 25)` untuk creature normal, sehingga normalnya 1–5. Source khusus mengikuti rule khusus yang sah.

Loot Band adalah ceiling/range, bukan jaminan. Material tubuh hanya bila biologis/logis; resource habitat hanya bila tersedia; equipment/currency/unique item hanya bila acquisition source mendukungnya.

## 8. FIXED TABLE OVERRIDE
Prioritas:
`Fixed Canon/Event/Mission Table → Dynamic Loot Formula → RESOLUTION-BLOCKED`

Fixed table hanya berlaku pada source yang secara eksplisit dicakup.

## 9. ANTI-CATALOG
Hasil runtime tidak menjadi daftar global. Species/monster/beast/loot yang pernah muncul tidak membatasi kemungkinan hasil berikutnya.

## 10. ANTI-SCALING
Character Realm tidak otomatis menaikkan Tier, loot, rarity, reward, difficulty, atau quality. Character Context hanya dapat memengaruhi encounter, perilaku, perhatian makhluk, route, dan konsekuensi sesuai konteks.

## 11. VALIDATION GATE
1. region/habitat valid;
2. pressure memiliki source;
3. threat memiliki source;
4. Tier mematuhi ceiling/override;
5. Tier ≠ Realm;
6. creature tidak melanggar Canon;
7. ability/technique memiliki dasar;
8. Spirit Beast mengikuti Module 24;
9. BEAST_ID unique bila persistent;
10. loot hanya setelah acquisition valid;
11. quantity/quality mengikuti formula/table;
12. ownership memiliki Origin;
13. material change memiliki Origin Log;
14. State Validator dan Save Pipeline lulus;
15. write-back diverifikasi sebelum status synchronized.

## 12. RUNTIME PIPELINE
`WORLD CONTEXT → HABITAT/REGION → ENCOUNTER PRESSURE → d100 → ENCOUNTER COMPOSITION → THREAT SCORE → CREATURE GENERATION → COMBAT/INTERACTION → LOOT ELIGIBILITY → LOOT POTENTIAL → LOOT GENERATION → SPIRIT BEAST LIFECYCLE → VALIDATION → ORIGIN/HISTORY → SAVE → WRITE-BACK VERIFY`

Untuk persistent Spirit Beast, load existing Beast State/History terlebih dahulu; generator tidak boleh membuat duplicate entity.

## 13. FORMULA SUMMARY
`Pressure = clamp(BasePressure + ΣEncounterModifiers, 0, 95)`

`ThreatScore = clamp(AreaThreatBase + ΣThreatModifiers, 0, 100)`

`LootPotential = clamp(SourceTierScore + HabitatScore + HarvestMethod + Condition + SpecialEvent, 0, 100)`

`Quantity = 1 + floor(LootPotential / 25)` untuk creature normal.

Semua formula adalah Admin Canon v1.0 dan hanya dapat diubah melalui perubahan Canon terdokumentasi.


## DATA COMPLETENESS GATE
Dynamic generation tidak boleh digunakan untuk menutup field yang kosong. Setiap generated field wajib memiliki input, formula, trigger, dan batas yang ditetapkan Admin. Jika input wajib tidak tersedia, gunakan UNRESOLVED atau RESOLUTION-BLOCKED sesuai core/07_DATA_COMPLETENESS.md. Generated result tetap RUNTIME-GENERATED dan tidak menjadi Canon hanya karena muncul atau dipersistenkan.


## 12. DYNAMIC REFINEMENT BOUNDARY
Dynamic Refinement adalah bounded runtime resolution untuk **existing Item** yang valid. Module 25 tidak menciptakan properti material, refinement method, atau efek upgrade baru; Module 34 tetap menjadi source untuk proses refinement existing item.

### 12.1 Canon Boundary
Canonical chain:
`Existing Item → Material Source & Properties → Refinement Method → Compatibility Validation → Dynamic Bounded Resolution → Before/After → Origin → Save`

Source authority:
- Existing Item identity/state/property/quality/condition → Module 14.
- Material identity dan refinement-relevant properties → material/item source Canon yang terverifikasi.
- Refinement method, qualification, process, allowed change, dan failure mechanism → Module 34 atau source method yang sah.
- Dynamic selection within Admin-defined bounds → Module 25.
- Routing/dependency → Modules 27 + 35.
- State validation → State Validator.
- Persistence/transaction → Save Pipeline.

### 12.2 Required Inputs
Material properties used by this pipeline must conform to **Module 14 §4A — Material Refinement Property Schema**. Module 25 may select a concrete runtime result only after those properties and their sources have passed Module 34 validation.

Dynamic Refinement hanya boleh berjalan bila input material berikut tersedia dan tervalidasi:
1. Existing Item ID dan Current Item State.
2. Material ID, quantity, dan valid Origin.
3. Material properties yang **secara eksplisit** relevan terhadap refinement.
4. Refinement Method/Procedure dengan source dan Method Record yang lolos Module 34 §11A Refinement Method Schema.
5. Compatibility rule atau method-defined compatibility.
6. Refiner qualification bila diwajibkan.
7. Tool/workspace bila diwajibkan.
8. Cost dan process time bila diwajibkan.
9. Allowed property dimensions and bounds dari method/source.

Jika salah satu required input tidak memiliki source sah, hasilnya `RESOLUTION-BLOCKED`. Dynamic Generation tidak boleh mengisi input tersebut.

### 12.3 Material Property Boundary
Material tidak memperoleh refinement effect hanya dari nama, rarity, grade, harga, deskripsi, atau plausibility.
Refinement-relevant properties harus berasal dari source material yang sah dan terverifikasi.
Jika property yang dibutuhkan berstatus `UNRESOLVED`, Qwen tidak boleh menebak nilai atau efeknya.

### 12.4 Bounded Resolution Contract
Module 25 boleh menentukan **hasil konkret runtime** hanya di dalam ruang yang sudah ditentukan source:
- property dimension yang boleh berubah;
- direction/range/bounds perubahan;
- quality/condition ceiling;
- compatibility;
- success/partial/failure outcomes;
- material consumption;
- cost/time;
- failure consequences bila method mengizinkannya.

Module 25 **tidak boleh**:
- menciptakan property baru;
- menaikkan grade/tier/category tanpa mechanism source;
- memberi ability/effect/affinity/bloodline yang tidak disediakan source;
- mengubah ownership tanpa rule;
- menetapkan probabilitas tersembunyi jika source tidak menyediakan mekanismenya;
- memakai Character Realm sebagai automatic refinement multiplier.

### 12.5 Resolution States
Resolution dapat menghasilkan:
- `SUCCESS`
- `PARTIAL`
- `FAILURE_UNCHANGED`
- `FAILURE_DAMAGED`
- `FAILURE_DESTROYED`
- `RESOLUTION-BLOCKED`

Damage/destruction hanya valid bila method/source mengizinkannya. Result tidak boleh melampaui Admin/source ceiling.

### 12.5A. BOUNDED RESOLUTION FORMULA

Bounded Resolution adalah proses pemilihan hasil konkret runtime dari input yang **sudah tervalidasi**, bukan generator mekanik baru.

#### 12.5A.1 Canonical Resolution Function

`Existing Item State + Material Properties + Refinement Method + Compatibility + Qualification + Process Conditions → Bounded Resolution → Before/After`

Input resolver wajib dinormalisasi sebagai satu resolution context:
- `ITEM_STATE` — identity, category, condition, quality/property yang terverifikasi;
- `MATERIAL_PROPERTY_RECORDS` — material identity, quantity, origin, dan property yang tervalidasi;
- `METHOD_RECORD` — method source, requirements, allowed dimensions, bounds, outcome model, consumption/failure rules;
- `COMPATIBILITY_RESULT` — hasil Module 34;
- `QUALIFICATION_RESULT` — hasil pemeriksaan refiner terhadap requirement method;
- `PROCESS_CONDITIONS` — tool/workspace, cost, time, process steps, dan kondisi lain yang memang diwajibkan source.

Resolver tidak boleh menambahkan input mekanis baru hanya agar formula dapat menghasilkan output.

#### 12.5A.2 Resolution Gates

Urutan wajib:

`INPUT COMPLETENESS → ITEM GATE → MATERIAL GATE → METHOD GATE → COMPATIBILITY GATE → QUALIFICATION GATE → PROCESS/COST GATE → ALLOWED DIMENSION GATE → BOUND INTERSECTION → OUTCOME MODEL → RUNTIME SELECTION → BEFORE/AFTER`

1. **Input Completeness Gate** — semua required input memiliki source dan status yang sah.
2. **Item Gate** — existing item memenuhi target category/constraints.
3. **Material Gate** — material quantity, origin, properties, dan consumption rule yang diperlukan tervalidasi.
4. **Method Gate** — Method Record Module 34 §11A lengkap untuk resolution yang diminta.
5. **Compatibility Gate** — hanya `COMPATIBLE` yang boleh melanjutkan refinement.
6. **Qualification Gate** — refiner memenuhi qualification yang diwajibkan source.
7. **Process/Cost Gate** — tool/workspace, time, dan resource cost yang diwajibkan tersedia dan dapat diterapkan.
8. **Allowed Dimension Gate** — hanya dimension yang tercantum dalam method yang masuk ruang perubahan.
9. **Bound Intersection** — hasil kandidat wajib berada dalam irisan seluruh batas yang berlaku dari item/current state, material property source, dan method. Jika source tidak memberi bound yang diperlukan, resolusi diblokir; jangan menciptakan bound.
10. **Outcome Model** — gunakan mekanisme outcome yang dinyatakan source.
11. **Runtime Selection** — pilih satu hasil konkret hanya dari ruang hasil yang legal.
12. **Before/After** — hitung dan validasi state sebelum dan sesudah sebagai satu transaction.

#### 12.5A.3 Bound Intersection Rule

Untuk setiap dimension yang diizinkan:

`LEGAL_RESULT(d) = ItemConstraint(d) ∩ MaterialBound(d) ∩ MethodBound(d)`

Hanya constraint/bound yang benar-benar tersedia dari source yang boleh digunakan. Jika suatu dimension tidak memiliki bound yang diperlukan untuk menjaga hasil tetap sah, statusnya `UNRESOLVED` dan resolusi yang bergantung padanya menjadi `RESOLUTION-BLOCKED`.

Jika irisan menghasilkan ruang kosong, hasil bukan partial success yang dipaksakan. Gunakan status yang sesuai source; bila tidak ada mekanisme resmi untuk menyelesaikan konflik tersebut, gunakan `RESOLUTION-BLOCKED`.

#### 12.5A.4 Outcome Selection

Outcome selection mengikuti `OUTCOME_MODEL` dari Method Record:
- deterministic requirement/process validation → hasil ditentukan oleh kondisi yang terpenuhi;
- source-defined check → jalankan check persis sesuai source;
- source-defined Success/Partial/Failure → gunakan mekanisme dan batas source.

Jika source mendefinisikan roll/probability, hanya mekanisme dan parameter source tersebut yang boleh dipakai. Jika source tidak mendefinisikannya, **jangan membuat d100, persentase, multiplier, bonus, atau modifier baru**.

Module 25 tidak boleh:
- mengubah current property menjadi bonus numerik tanpa bound/source;
- memilih angka dari rentang yang tidak memiliki source;
- menggunakan rarity, harga, nama, visual, Character Realm, atau narrative plausibility sebagai modifier;
- menganggap `SUCCESS` berarti semua dimension berubah;
- mengubah dimension yang tidak diizinkan method;
- mengubah category/grade/tier/ability/affinity/ownership tanpa mechanism source.

#### 12.5A.5 Resolution State Semantics

- `SUCCESS` — seluruh perubahan yang dipilih berada dalam bounds dan outcome source mengizinkannya.
- `PARTIAL` — hanya bila source mendefinisikan partial outcome; perubahan tetap berada dalam bounds.
- `FAILURE_UNCHANGED` — source mengizinkan failure tanpa state change.
- `FAILURE_DAMAGED` — hanya bila source mendefinisikan damage/defect.
- `FAILURE_DESTROYED` — hanya bila source secara eksplisit mengizinkan destruction.
- `RESOLUTION-BLOCKED` — required input/mechanism/bound tidak tersedia atau legal resolution tidak dapat dibuktikan.

Tidak ada implicit fallback dari `RESOLUTION-BLOCKED` menjadi failure atau success.

#### 12.5A.6 No Unsupported Numeric Resolution

Formula ini **tidak** menetapkan angka bonus, multiplier, probability, quality increment, durability increment, tier increment, atau material-to-effect mapping baru.

Jika source hanya memberi arah perubahan tanpa nilai/range/bound yang dapat dipakai, Qwen tidak boleh memilih angka sendiri. Result tetap `UNRESOLVED` / `RESOLUTION-BLOCKED` sesuai kebutuhan field.

### 12.6 Before/After Transaction Contract
Setiap successful/partial/allowed failure refinement harus dapat ditelusuri:
- BEFORE: Item State, material state, relevant resources.
- INPUT: Material ID/quantity, method, refiner, tool/workspace.
- RESOLUTION: compatibility, source bounds, selected outcome, consumed resources.
- AFTER: Item State, consumed Material State, resource/currency/time changes.
- PROVENANCE: Origin + History untuk entity yang berubah.

Dynamic result berstatus `RUNTIME-GENERATED` dan tidak menjadi Global Canon.

### 12.7 Anti-Improvisation Gate
Jika source hanya menyatakan bahwa material dapat digunakan untuk refinement tetapi tidak mendefinisikan property, dimension, bound, compatibility, atau result mechanism yang diperlukan, resolusi yang bergantung pada informasi tersebut wajib `RESOLUTION-BLOCKED`.
Narrative plausibility, Player request, prior chat memory, rarity, market value, atau nama material bukan fallback mekanis.

### 12.8 Boundary With Module 34
Module 34 menentukan **apa yang secara mekanis diperbolehkan** pada existing item.
Module 25 menentukan **hasil konkret runtime** hanya di dalam bounds yang sudah disediakan.
Dengan demikian:
`Module 34 = Refinement Process/Permission`
`Module 25 = Bounded Dynamic Resolution`
`Module 14 = Item State Authority`
`Module 27/35 = Routing/Dependency`

Tidak ada automatic upgrade di antara ketiganya.

## 2026-09-18 Anti-Cheat Resolution Hardening

### RNG Gate
Every random step in this module (including Encounter d100, random composition, random selection, or any future random outcome) must consume a verifiable RNG Source under core/04_ANTI_CHEAT.md.

Required runtime record:
ROLL_ID / RNG_SOURCE / PURPOSE / INPUT-SEED-CONTEXT / RESULT / WORLD_TIME / ENTITY-ID when applicable.

No GM-selected roll, reroll, result substitution, or post-outcome reroll is legal. If a verifiable RNG source is unavailable, the random-dependent resolution is RESOLUTION-BLOCKED.

### Modifier Registry Gate
The existing notation "Σ Modifier" is not permission to invent or stack modifiers.

A numeric modifier is executable only when a source explicitly defines:
- modifier category/identity;
- trigger condition;
- numeric value or bounded range;
- whether stacking is permitted;
- affected formula.

At most one modifier from the same category may apply unless the source explicitly permits stacking. Equivalent conditions may not be counted twice under different labels.

Until such a source record exists, an otherwise unsupported numeric modifier is ignored as a mechanical input; if the modifier is required for the requested resolution, the resolution is RESOLUTION-BLOCKED rather than guessed.

### Loot Score Source Gate
The existing Loot Potential formula names four score components beyond Source Tier Score:
Habitat Score / Harvest-Defeat Method / Condition / Special Event.

Those names are not executable numeric values by themselves.

Each component must have a source record defining its scoring rule. If a component is required but its score cannot be sourced, do not choose a number from 0–20. The affected Loot Potential resolution is RESOLUTION-BLOCKED unless a fixed table or other valid source independently determines the loot result.

Source Tier Score remains executable exactly as defined in this module.

### Deterministic Resolution Order
For every generated outcome:
SOURCE INPUTS → VALIDATED MODIFIERS → VERIFIED RNG (if formula is random) → RESULT → VALIDATION → NARRATIVE.

Narrative generation cannot influence a previously unresolved numeric input, roll, modifier, Tier, quantity, rarity, or loot result.
