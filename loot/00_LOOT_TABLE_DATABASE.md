# LOOT TABLE DATABASE — ADMIN CANON

> Database resmi untuk semua loot table TianDao-World.
> Modul `systems/18_LOOT.md` menetapkan aturan; file ini menyimpan table yang benar-benar dapat dipakai runtime.

## 1. Status

- Status: **ADMIN CANON**
- Scope: seluruh loot yang membutuhkan daftar drop, peluang, rarity, quantity, atau hasil numerik.
- Source of truth: file ini + loot table spesifik yang secara eksplisit dirujuk di sini.
- GM/Qwen tidak boleh membuat atau mengubah table runtime.
- Perubahan table dilakukan oleh Admin dan harus dapat ditelusuri melalui commit/history.

## 2. ID Loot Table

Format ID:
`LT-<SOURCE>-<NNN>`

Contoh:
- `LT-MON-001` — loot monster tertentu
- `LT-BEAST-001` — loot Spirit Beast tertentu
- `LT-CHEST-001` — loot peti/lokasi tertentu
- `LT-EVENT-001` — loot/reward event tertentu
- `LT-MISSION-001` — reward misi tertentu

ID bersifat unik dan tidak boleh digunakan ulang untuk table yang berbeda.

## 3. Schema Wajib

Setiap table aktif harus memiliki:

| Field | Wajib | Keterangan |
|---|---|---|
| Loot Table ID | Ya | ID unik permanen |
| Status | Ya | Active / Suspended / Retired |
| Source Type | Ya | Monster / Spirit Beast / Chest / Location / Enemy / Event / Mission / Other |
| Source ID | Ya | ID entitas/sumber resmi |
| Source Condition | Ya | Kondisi agar table dapat dipakai |
| Entry | Ya | Daftar hasil loot |
| Chance/Weight | Bila digunakan | Hanya angka yang ditetapkan Admin |
| Quantity | Bila digunakan | Rentang/angka yang ditetapkan Admin |
| Rarity | Bila digunakan | Nilai rarity yang ditetapkan Admin |
| Quality | Bila digunakan | Hanya bila item/system mendukung |
| Modifier | Tidak wajib | Hanya bila Admin Canon menetapkannya |
| Item/Reward ID | Ya untuk item | Harus menunjuk item/reward Canon |
| Origin Rule | Ya | Cara Origin Log dibuat |
| Notes | Ya | Batasan dan kondisi khusus |

## 4. Aturan Entry

- Setiap item/reward yang disebut harus memiliki identitas Canon yang dapat diverifikasi.
- Currency hanya boleh muncul jika table secara eksplisit menetapkan jenis dan jumlahnya.
- Item yang belum memiliki Canon Item/Reward ID tidak boleh dimasukkan ke table aktif.
- `???` bukan entry loot aktif. Jika data belum cukup, table tidak dibuat aktif.
- Tidak boleh ada table generik yang otomatis mengubah Tier, Realm, habitat, lokasi, atau tingkat kesulitan menjadi loot.

## 5. Status Database Saat Ini

**Belum ada loot table aktif yang ditetapkan.**

Alasan: repository saat ini telah memiliki sistem Loot dan sumber ekonomi/currency, tetapi belum memiliki database monster dengan Source ID yang dapat dipasangkan ke loot table dan belum memiliki katalog Item/Reward yang cukup untuk membentuk drop spesifik tanpa menciptakan Canon baru secara diam-diam.

Ini bukan fallback runtime. Ini adalah status database yang eksplisit dan dapat diaudit.

Sampai table aktif ditambahkan:
- GM tidak boleh mengarang drop monster/Spirit Beast;
- GM tidak boleh mengarang isi peti;
- GM tidak boleh mengubah Tier/Realm/habitat menjadi drop;
- reward event/misi tetap hanya berasal dari registry/event/misi yang menetapkannya secara eksplisit.

## 6. Prosedur Penambahan Table oleh Admin

Sebelum table baru menjadi `Active`, Admin wajib memastikan:

1. Source ID resmi sudah ada.
2. Item/Reward ID yang dipakai sudah ada.
3. Kondisi perolehan sudah jelas.
4. Chance/Weight/Quantity/Rarity/Quality hanya ditetapkan bila memang diperlukan.
5. Tidak ada konflik dengan Economy, Items, Monsters, Spirit Beasts, Events, atau Save Integrity.
6. Origin Rule dapat dilaksanakan.
7. Perubahan dicatat melalui commit dan dapat diverifikasi ulang.

## 7. Runtime Resolution

Urutan runtime:

`Source-specific Loot Table → Event/Mission Reward Canon → Item/Source Origin Canon → unresolved (???)`

Jika Source ID tidak memiliki table aktif, runtime **tidak membuat table sementara**.

## 8. Anti-Duplikasi

Loot yang berhasil diberikan harus menghasilkan Item Origin Log/reward record yang valid. Table tidak memberikan item dua kali hanya karena state di-reload, turn diulang, atau player mengklaim ulang hasil yang sama.

## 9. Integrasi

Database ini terhubung dengan:
- `systems/18_LOOT.md`
- `systems/13_MONSTERS.md`
- `systems/14_ITEMS.md`
- `systems/24_SPIRIT_BEASTS.md`
- event dan mission registry
- Economy
- Save Integrity
- Origin Log
- Character/Beast State
