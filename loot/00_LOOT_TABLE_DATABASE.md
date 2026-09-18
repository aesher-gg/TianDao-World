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

## 4A. ADMIN CANON — REGIONAL RESOURCE LOOT

> Table berikut ditambahkan karena ada source material Canon yang memiliki asal dan dampak sistemik yang jelas. Table tidak menjamin drop; ia hanya aktif ketika source condition dan acquisition benar-benar terpenuhi.

### LT-RES-001 — Serat Sungai Cangyuan
- Status: Active
- Source Type: Regional Resource
- Source ID: SRC-RES-CGY-001
- Source Condition: Character/party melakukan pengumpulan sah pada tepian sungai Dataran Cangyuan dan menemukan tanaman serat yang memenuhi source condition.
- Entries: ITEM-MAT-013 Serat Sungai Cangyuan — Quantity 1–3
- Origin Rule: lokasi/source ID, metode pengumpulan, World Time, claimant, dan perubahan kepemilikan.

### LT-RES-002 — Getah Pinus Roh Qingluan
- Status: Active
- Source Type: Regional Resource
- Source ID: SRC-RES-QGL-001
- Source Condition: pengumpulan getah dari pohon yang benar-benar menghasilkan getah di habitat yang valid.
- Entries: ITEM-MAT-007 Getah Pinus Roh Qingluan — Quantity 1–2
- Origin Rule: source tree/location atau resource context, method, World Time, claimant.

### LT-RES-003 — Jamur Kabut Wuyin
- Status: Active
- Source Type: Regional Resource
- Source ID: SRC-RES-QGL-002
- Source Condition: pengumpulan sah pada habitat lembap berkabut Hutan Wuyin; tidak berlaku untuk seluruh Pegunungan Qingluan.
- Entries: ITEM-HERB-003 Jamur Kabut Wuyin — Quantity 1–3
- Origin Rule: source location, collection method, World Time, claimant.

### LT-RES-004 — Terak Besi Api Huoyan
- Status: Active
- Source Type: Regional Resource
- Source ID: SRC-RES-YHS-001
- Source Condition: pengambilan endapan/terak mineral pada zona panas bumi yang dapat diakses secara sah.
- Entries: ITEM-MAT-008 Terak Besi Api Huoyan — Quantity 1–3
- Origin Rule: deposit/source location, extraction method, World Time, claimant.

### LT-RES-005 — Madu Seratus Bunga
- Status: Active
- Source Type: Regional Resource
- Source ID: SRC-RES-YHS-002
- Source Condition: madu benar-benar tersedia dari koloni penyerbuk lokal di Lembah Seratus Bunga dan dapat dipanen tanpa melanggar kondisi source.
- Entries: ITEM-HERB-004 Madu Seratus Bunga — Quantity 1–2
- Origin Rule: colony/source context, collection method, World Time, claimant.

### LT-RES-006 — Mutiara Pasang Dongming
- Status: Active
- Source Type: Regional Resource
- Source ID: SRC-RES-DGM-001
- Source Condition: mutiara ditemukan/diperoleh melalui pengambilan sah dari sumber laut yang memang menghasilkan mutiara.
- Entries: ITEM-MAT-009 Mutiara Pasang Dongming — Quantity 1
- Origin Rule: marine source/location, acquisition method, World Time, claimant.

### LT-RES-007 — Cangkang Karang Lanyue
- Status: Active
- Source Type: Regional Resource
- Source ID: SRC-RES-DGM-002
- Source Condition: cangkang berasal dari organisme laut bercangkang yang memenuhi source condition; tidak boleh dibuat dari batu karang biasa.
- Entries: ITEM-MAT-014 Cangkang Karang Lanyue — Quantity 1–3
- Origin Rule: source organism/location, acquisition method, World Time, claimant.

### LT-RES-008 — Kulit Dingin Beiming
- Status: Active
- Source Type: Regional Resource
- Source ID: SRC-RES-BMG-001
- Source Condition: hasil pengulitan sah dari fauna/monster yang benar-benar memiliki material kulit/fur yang dapat digunakan.
- Entries: ITEM-MAT-010 Kulit Dingin Beiming — Quantity 1–2
- Origin Rule: source entity/encounter, harvest method, World Time, claimant.

### LT-RES-009 — Kristal Garam Jinyan
- Status: Active
- Source Type: Regional Resource
- Source ID: SRC-RES-GJY-001
- Source Condition: penambangan/pengumpulan endapan garam mineral yang benar-benar ditemukan pada lokasi resource.
- Entries: ITEM-MAT-011 Kristal Garam Jinyan — Quantity 1–4
- Origin Rule: deposit/location, extraction method, World Time, claimant.

### LT-RES-010 — Pecahan Giok Baiyu
- Status: Active
- Source Type: Regional Resource
- Source ID: SRC-RES-TYN-001
- Source Condition: material merupakan pecahan/limbah pengerjaan giok yang benar-benar tersedia melalui jalur produksi Kota Baiyu.
- Entries: ITEM-MAT-012 Pecahan Giok Baiyu — Quantity 1–3
- Origin Rule: workshop/source context, acquisition method, World Time, claimant.

## 4B. Fixed Loot Integrity Rules
- Table regional resource hanya berlaku pada Source ID yang tercantum; tidak boleh dipindahkan ke habitat lain hanya karena nama material terlihat cocok.
- Fixed table tidak menjamin resource tersedia pada setiap kunjungan.
- Resource depletion, access, ownership, weather, hazard, dan local control tetap diproses dari Current State/World Context bila relevan.
- Quantity table adalah range Canon untuk source tersebut; Qwen tidak boleh mengubahnya berdasarkan Realm Character.
- Item hasil tetap memerlukan instance Origin Log dan tidak menjadi inventory sebelum acquisition tervalidasi.
- Jika source condition tidak terpenuhi, table tidak aktif dan Qwen mengikuti Dynamic Loot Formula atau RESOLUTION-BLOCKED sesuai input yang tersedia.
- Table regional resource tidak membatasi dynamic loot dari monster/Spirit Beast atau source lain.
