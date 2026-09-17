# LOOT TABLE DATABASE — ADMIN CANON

> Database resmi untuk semua loot table TianDao-World.
> Modul `systems/18_LOOT.md` menetapkan aturan; file ini menyimpan table yang benar-benar dapat dipakai runtime.

## 1. Status
- Status: **ADMIN CANON**
- Scope: fixed loot yang secara eksplisit memiliki Source ID dan Item ID.
- Dynamic loot tetap mengikuti `systems/25_DYNAMIC_GENERATION.md`.

## 2. ID Loot Table
Format: `LT-<SOURCE>-<NNN>`.

## 3. Schema Wajib
Setiap table aktif memiliki Source ID, condition, entry, quantity/weight bila digunakan, Item/Reward ID, Origin Rule, dan Notes.

## 4. Baseline Fixed Tables
Table berikut adalah baseline Canon untuk source yang sudah mempunyai identitas resmi. Table tidak membatasi dynamic loot di luar source yang tercantum.

### LT-MON-001 — Binatang Liar Umum
- Status: Active
- Source Type: Monster
- Source ID: MON-GENERIC-BEAST
- Source Condition: hasil panen/loot sah dari binatang liar umum; tidak berlaku otomatis untuk semua monster.
- Entries:
  - `ITEM-MAT-003` Kulit Binatang Biasa — Quantity 1–2
  - `ITEM-MAT-004` Taring Binatang Biasa — Quantity 1–2
- Origin Rule: Item Origin mencatat source entity, metode perolehan, World Time, dan perubahan kepemilikan.

### LT-MON-002 — Predator Besar Biasa
- Status: Active
- Source Type: Monster
- Source ID: MON-GENERIC-PREDATOR
- Source Condition: predator besar biasa telah dikalahkan atau dipanen secara sah.
- Entries:
  - `ITEM-MAT-003` Kulit Binatang Biasa — Quantity 1–3
  - `ITEM-MAT-004` Taring Binatang Biasa — Quantity 1–4
- Origin Rule: source, acquisition method, World Time, before/after ownership.

### LT-BEAST-001 — Spirit Beast Umum
- Status: Active
- Source Type: Spirit Beast
- Source ID: BEAST-GENERIC-COMMON
- Source Condition: hanya berlaku bila source secara eksplisit diklasifikasikan sebagai Spirit Beast umum dan loot acquisition sah.
- Entries:
  - `ITEM-MAT-003` Kulit Binatang Biasa — Quantity 1–2
  - `ITEM-MAT-004` Taring Binatang Biasa — Quantity 1–2
- Origin Rule: source BEAST_ID wajib dicatat; Beast tidak menjadi item.

### LT-CHEST-001 — Peti Perbekalan Dasar
- Status: Active
- Source Type: Chest
- Source ID: CHEST-SUPPLY-BASIC
- Source Condition: peti perbekalan resmi dibuka dengan cara yang sah.
- Entries:
  - `ITEM-MAT-006` Batu Api — Quantity 1
  - `ITEM-MAT-005` Serat Rami — Quantity 1–3
- Origin Rule: peti/source, lokasi, World Time, acquisition method.

### LT-MISSION-001 — Paket Material Dasar
- Status: Active
- Source Type: Mission
- Source ID: REWARD-MATERIAL-BASIC
- Source Condition: mission/quest yang secara eksplisit menunjuk table ini berhasil dan reward berhak diterima.
- Entries:
  - `ITEM-MAT-001` Bijih Besi Kasar — Quantity 1–3
  - `ITEM-MAT-005` Serat Rami — Quantity 1–3
- Origin Rule: Quest/Event ID, resolution, claimant, World Time.

## 5. Dynamic Boundary
Tidak adanya fixed table untuk source tertentu bukan berarti loot tidak dapat dihasilkan. Source valid yang tidak tercakup fixed table menggunakan Dynamic Loot Formula. Fixed table hanya mengoverride formula pada Source ID yang tercantum di sini.

## 6. Anti-Duplikasi
Loot yang berhasil diberikan menghasilkan Item Origin Log/reward record. Reload atau claim ulang tidak membuat instance kedua tanpa acquisition yang sah.

## 7. Integrasi
Terhubung dengan `systems/18_LOOT.md`, `systems/13_MONSTERS.md`, `systems/14_ITEMS.md`, `systems/24_SPIRIT_BEASTS.md`, event/mission registry, Economy, dan Save Integrity.
