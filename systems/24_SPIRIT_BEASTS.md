# 24 — SPIRIT BEAST SYSTEM

> Module: 24 — Spirit Beast System  
> Version: 1.0  
> Status: Canon System Specification

## 0. SYSTEM PRINCIPLE

Spirit Beast adalah makhluk hidup independen yang dapat memiliki hubungan dengan Character, dijinakkan, menjadi companion, dimiliki melalui mekanisme yang sah, atau terikat kontrak apabila mekanisme tersebut tersedia secara resmi.

Spirit Beast bukan Item, Equipment, atau Inventory object. Spirit Beast memiliki state, identitas, kebutuhan, perilaku, lifecycle, dan konsekuensi sendiri.

`13_MONSTERS.md` tetap menjadi sumber utama untuk ecology, encounter, species, habitat, behavior, dan creature classification. Module 24 mengatur lifecycle dan relationship mechanics Spirit Beast.

## 1. CORE RULES

- Tidak ada free Beast. Setiap Beast harus memiliki sumber dan sebab yang valid.
- Sumber dapat berupa official/custom database, encounter, event, breeding, gift, purchase, rescue, taming, contract, evolution, bloodline, atau mekanisme resmi lain.
- Data yang tidak diketahui tetap `???`; GM tidak boleh menebak.
- Beast tetap independen dan dapat menolak, takut, melarikan diri, menyerang, terluka, sakit, kehilangan trust, berkembang, atau mati sesuai kondisi dan sistem.
- Status companion/owned tidak memberikan plot armor.
- Tier dan Realm adalah atribut terpisah. Tidak semua Spirit Beast wajib memiliki Realm.

## 2. BEAST_ID

Setiap Spirit Beast persistent memiliki `BEAST_ID` global.

Format standar:

```text
BEAST-0001
BEAST-0002
BEAST-0003
```

Rules:
- unique;
- stable;
- permanent;
- tidak bergantung pada nama atau owner;
- tidak berubah karena rename, taming, ownership transfer, contract, atau evolution;
- tidak pernah digunakan ulang setelah permanent death/archive.

## 3. RELATIONSHIP MODEL — MODEL B

Relationship dengan Character berbeda dari Ownership.

Character dapat memiliki hubungan dengan Beast sebelum Beast jinak atau dimiliki.

Contoh valid:

```text
Relationship Status: Caretaker
Taming Status: Wild
Ownership Status: Unowned
Contract Status: No Contract
```

Relationship status standar:
- `None`
- `Encountered`
- `Familiar`
- `Caretaker`
- `Friendly`
- `Companion`
- `Bonded`

Relationship change harus memiliki causality: action/event, context, resolution, dan World Time.

## 4. TRUST, BOND, LOYALTY

- **Trust** = tingkat kepercayaan Beast kepada Character.
- **Bond** = kedalaman hubungan.
- **Loyalty** = kecenderungan Beast mengikuti/berpihak kepada Character.

Ketiganya bukan sinonim dan dapat memiliki nilai berbeda. Perubahan harus memiliki sebab yang dapat ditelusuri.

## 5. TAMING

Taming adalah proses valid untuk membuat Beast menerima kehidupan bersama Character. Taming bukan auto-success, mind control, ownership otomatis, atau contract otomatis.

Taming status standar:
- `Wild`
- `Wary`
- `Friendly`
- `Taming Attempt`
- `Tamed`
- `Bonded`

Resolution dapat berupa Success, Partial Success, Failure, atau Failure with Consequence. Requirement, method, cost, risk, dan hasil hanya boleh berasal dari system/species/context yang valid.

## 6. OWNERSHIP

Ownership berbeda dari Relationship dan Taming.

Ownership status standar:
- `Unowned`
- `Owned`
- `Transferred`
- `Released`
- `Missing`
- `Deceased`

Acquisition dapat terjadi hanya melalui mekanisme resmi seperti valid taming, purchase, gift, rescue/adoption mechanism, contract, breeding, event, atau faction/system mechanism yang benar-benar tersedia.

Transfer ownership adalah material state transition. Catat previous owner, new owner, reason/method, World Time, resolution, dan origin. `BEAST_ID` tetap sama.

Release dapat membuat Beast kembali `Unowned` tanpa mengharuskan Relationship menjadi `None`.

## 7. CONTRACT

Contract berbeda dari Relationship, Taming, Ownership, dan Bond.

Contract status:
- `No Contract`
- `Pending`
- `Active`
- `Suspended`
- `Terminated`
- `Broken`

Contoh contract type dapat mencakup `Companion Bond`, `Beast Contract`, `Soul Contract`, atau `Special Contract`, tetapi tipe tersebut tidak otomatis tersedia. Contract hanya aktif bila Canon/Admin/system resmi mendefinisikan method, requirement, cost, effect, risk, duration, termination, dan failure condition.

Contract aktif wajib memiliki Contract Origin. Termination/breaking adalah material change dan harus melewati validation, resolution, Origin Log, integrity, dan save.

## 8. BEAST STATE

Current Beast State disimpan terpisah dari Character State.

Suggested canonical path:

`characters/beasts/<BEAST_ID>.md`

Minimum state:

```text
Beast ID:
Name:
Species:
Classification:

Relationship Character ID:
Relationship Status:
Trust:
Bond:
Loyalty:

Owner Character ID:
Ownership Status:

Taming Status:
Taming Origin:

Contract Status:
Contract Type:
Contract Origin:

Tier:
Realm:
Stage:
Age:
Maturity:
Growth Potential:
Bloodline:

HP:
Qi:
Stamina:
Satiety:
Condition:
Health Status:

Temperament:
Intelligence:
Behavior:

Current Location:
Habitat:
Last World Time:

Abilities:
Techniques:
Equipment:
Inventory:

Origin:
Status:
```

`Equipment`/`Inventory` hanya digunakan jika benar-benar berlaku menurut system. Jika tidak berlaku gunakan `N/A`; data yang belum diketahui gunakan `???`.

Beast tidak boleh dianggap berada bersama Character hanya karena memiliki owner.

## 9. BEAST HISTORY

Persistent Beast memiliki history terpisah.

Suggested canonical path:

`beast_history/<BEAST_ID>_HISTORY.md`

Character History menyimpan apa yang dialami Character. Beast History menyimpan apa yang dialami Beast. Event yang sama boleh direferensikan tanpa menduplikasi seluruh isi.

Material event minimum:

```text
World Time:
BEAST_ID:
Action/Event:
Cause:
Resolution:
Before:
After:
Source:
```

History bersifat append-oriented dan tidak boleh digunakan untuk retcon.

## 10. GROWTH

Growth adalah perkembangan normal yang dapat dipengaruhi age, nutrition, environment, species, cultivation, training, bloodline, condition, atau growth mechanics resmi.

Growth tidak otomatis memberikan Realm, Tier, ability, atau technique baru.

## 11. EVOLUTION

Evolution adalah major state transition.

Evolution hanya boleh terjadi bila terdapat mechanism dan requirement resmi, misalnya species rule, bloodline, item, technique, cultivation requirement, environment, event, atau mekanisme Canon/Admin lain.

Resolution dapat berupa Success, Failure, Partial Evolution, atau Evolution with Consequence.

Evolution wajib dicatat dengan before/after species, Tier, Realm, cause, method, requirement, resolution, World Time, dan Source. `BEAST_ID` tetap sama.

## 12. COMBAT INTEGRATION

Spirit Beast adalah combat entity independen jika valid untuk ikut combat.

Beast memiliki HP, Qi, Stamina, Condition, dan combat state sendiri. Beast dapat menerima damage, menjadi critical, dan mati. Combat menggunakan `12_COMBAT.md` dan modifier resmi yang berlaku.

Innate/species/bloodline/technique abilities hanya digunakan jika memiliki source/definition valid.

Memiliki Beast tidak memberikan free action atau serangan gratis. Action economy mengikuti Combat System.

HP 0 diproses sebagai critical/death sesuai combat/vitality rules. Permanent death hanya setelah resolution yang mengonfirmasi. Resurrection hanya melalui mekanisme resmi.

## 13. FEEDING, CARE, DAN TRAINING

Feeding, healing, grooming, training, dan care adalah actions terhadap Beast.

Efek terhadap Satiety, HP, Stamina, Condition, Trust, Bond, atau Loyalty hanya diterapkan jika mekanisme valid.

Item yang diberikan kepada Beast harus benar-benar berasal dari Character Inventory atau sumber resmi lain. Consumption/transfer harus tercatat pada kedua state bila keduanya berubah.

Tidak ada free healing.

Training tidak otomatis memberikan technique. Technique baru harus mengikuti `15_TECHNIQUES.md` dan memiliki Origin yang valid.

## 14. LOCATION & HABITAT

Beast memiliki `Current Location` dan `Habitat`. Keduanya dapat berbeda.

Perpindahan mengikuti Geography, Travel, Time, terrain, mobility, dan action yang relevan. Tidak ada hidden teleport/time skip.

## 15. CHARACTER ↔ BEAST TRANSACTION

Satu action dapat mengubah Character State dan Beast State sekaligus.

Contoh feeding:

```text
Character Inventory: Spirit Fish -1
Beast Satiety: +X
```

Setiap perubahan harus memiliki hubungan sebab-akibat dan traceability. Resolver mempertahankan hasil aktual bila salah satu perubahan berhasil dan perubahan lain gagal; tidak boleh membuat rollback fiktif.

## 16. VALIDATION

State Validator wajib memeriksa, bila Spirit Beast relevan:

- BEAST_ID unique/stable dan owner mapping valid;
- species/classification/Tier/Realm/Stage valid;
- Character ID relationship/owner valid;
- Trust/Bond/Loyalty changes memiliki causality;
- taming method dan transition valid;
- ownership acquisition/transfer/release valid;
- contract type/origin/status transition valid;
- growth/evolution requirements dan before→after valid;
- HP/Qi/Stamina/Satiety dalam batas yang berlaku;
- ability/technique memiliki Origin;
- location dan World Time konsisten;
- missing/deceased state valid;
- Beast History dan Origin Log traceable;
- Character History tetap terisolasi;
- shared memory hanya diperbarui bila memang shared.

Jika pemeriksaan material gagal, jangan menerapkan state. Gunakan last verified state atau minta klarifikasi.

## 17. ORIGIN LOG

Setiap material Beast change wajib memiliki Origin Log minimal:

```text
World Time:
BEAST_ID:
Action/Event:
Cause:
Resolution:
Before:
After:
Source:
```

Material change mencakup registration, taming, ownership, transfer, release, contract, injury/recovery yang material, Tier/Realm/Stage change, evolution, ability/technique acquisition, dan permanent death.

## 18. SAVE PIPELINE

Beast mengikuti Save Pipeline:

```text
LOAD VERIFIED STATE
→ LOAD BEAST HISTORY
→ LOAD CHARACTER STATE
→ LOAD WORLD CONTEXT
→ VALIDATE
→ COST
→ RESOLVE
→ BEAST REACTION
→ APPLY BEAST STATE
→ APPLY CHARACTER STATE
→ ORIGIN LOG
→ INTEGRITY
→ HISTORY
→ SAVE
→ WRITE-BACK
→ VERIFY
```

Jika write-back gagal, GM tidak boleh menyatakan state sudah tersinkron.

## 19. RUNTIME INTEGRATION

Saat action melibatkan Beast:

```text
PLAYER INTENT
→ CONTEXT LOAD
→ CHARACTER STATE LOAD
→ BEAST STATE LOAD
→ VALIDATION
→ COST
→ RESOLUTION
→ BEAST REACTION
→ STATE APPLY
→ ORIGIN LOG
→ INTEGRITY
→ HISTORY
→ SAVE
→ WRITE-BACK VERIFY
→ RESPONSE
```

Beast reaction mempertimbangkan species, intelligence, temperament, condition, needs, relationship, trust, bond, loyalty, history, dan environment.

## 20. PRIORITY

Jika terjadi konflik:

`Canon/Admin/Custom → System Rules → Realm/Species/Lore → Current State → History/Persistent Memory → Player Intent`

Player intent tidak dapat mengoverride state atau requirement sistem.

## 21. INTEGRATION

Module 24 terintegrasi dengan:

- `core/05_SAVE_INTEGRITY.md`
- `core/06_ID_AND_SAVE_SYSTEM.md`
- `systems/09_CULTIVATION.md`
- `systems/12_COMBAT.md`
- `systems/13_MONSTERS.md`
- `systems/14_ITEMS.md`
- `systems/15_TECHNIQUES.md`
- `gm/GM_PROMPT.md`
- `gm/RUNTIME_ENGINE.md`
- `gm/STATE_VALIDATOR.md`
- `gm/ACTION_RESOLVER.md`
- `gm/SAVE_PIPELINE.md`
- `gm/RESPONSE_FORMAT.md`

Integration hanya berarti modul terkait harus memahami/merujuk Module 24 ketika relevan; tidak ada mekanisme baru yang dianggap tersedia tanpa definisi resmi.

## 22. MISSING & PERMANENT DEATH

`Missing` tidak sama dengan `Deceased`. Beast yang hilang tidak boleh dianggap mati atau diteleport kembali.

Permanent-dead Beast mempertahankan State/History sebagai historical record. `BEAST_ID` tidak boleh digunakan ulang.

## 23. FINAL HARD RULES

1. Spirit Beast bukan Item, Equipment, atau Inventory object.
2. BEAST_ID unique, stable, permanent, dan tidak pernah reused setelah permanent death.
3. Tier ≠ Realm.
4. Relationship ≠ Taming.
5. Taming ≠ Ownership.
6. Ownership ≠ Contract.
7. Trust ≠ Bond ≠ Loyalty.
8. Model B berlaku: relationship dapat ada tanpa ownership/taming.
9. Tidak ada automatic taming, ownership, contract, ability, technique, evolution, atau healing.
10. Beast adalah entitas independen dan tidak memiliki plot armor.
11. Beast dapat terluka, hilang, critical, dan mati.
12. Resurrection hanya melalui mekanisme resmi.
13. Material Beast changes wajib memiliki Origin Log.
14. Current Beast State harus traceable ke History dan Origin.
15. `???` tidak boleh diisi melalui tebakan.
16. Ownership transfer mempertahankan BEAST_ID dan History.
17. Permanent-dead BEAST_ID tidak boleh digunakan ulang.
18. Write-back failure tidak boleh diklaim synchronized.
19. Semua mekanisme baru tunduk pada Canon/Admin dan hierarchy sistem.
