# AUDIT FINAL INTEGRITAS — TIANDAO-WORLD

## Status
**AUDIT MIGRATION — IN PROGRESS / DIRECT-FETCH VERIFIED**

Dokumen ini mencatat hasil audit dan migrasi status data. `UNRESOLVED` adalah status data resmi, bukan placeholder bebas. Audit lama yang masih menyebut legacy unknown marker tidak lagi menjadi acuan.

## 1. INDEX ↔ STRUKTUR REPOSITORY
Path yang menjadi bagian Load Order harus diverifikasi terhadap `INDEX.md` dan struktur branch `main`. Direct fetch branch `main` menjadi sumber verifikasi bila hasil search index tertinggal.

## 2. LOKASI / GEOGRAFI
World Map menetapkan kawasan Canon dan melarang GM mengasumsikan lokasi, jarak, atau rute yang belum memiliki dasar. `systems/20_TRAVEL_ROUTES.md` memakai Li sebagai satuan resmi dan menggunakan `UNRESOLVED` untuk rute yang belum memiliki baseline.

## 3. FACTION / NPC
Faction regional memakai database dan file individual sebagai sumber detail. NPC yang belum memiliki identitas/state sah menggunakan status data resmi dan tidak ditebak.

## 4. EVENT / QUEST
World Event dan Scheduled Event harus memakai registry dan trigger resmi. Dynamic local event/quest tidak menjadi Global Canon hanya karena generated atau persistent.

## 5. CANON / DERIVED / GENERATED
Canon Admin, Derived World Logic, dan Generated GM Content tetap dipisahkan. Persistence mempertahankan continuity tetapi tidak otomatis mengubah generated content menjadi Global Canon.

## 6. TRAVEL
`systems/20_TRAVEL_ROUTES.md` telah dimigrasikan dari legacy unknown marker ke `UNRESOLVED`. Baseline kecepatan resmi tetap:
- Jalan kaki: 8 Li/jam.
- Tunggangan darat biasa: 20 Li/jam.
- Karavan darat biasa: 12 Li/jam.
- Kapal dagang/kapal perjalanan biasa: 30 Li/jam.

Metode khusus tanpa nilai resmi tidak memiliki fallback numerik. Perjalanan lebih dari 3 jam memakai checkpoint.

## 7. LOOT
`systems/18_LOOT.md` menggunakan fixed table atau Dynamic Loot Formula sesuai source. Tidak ada automatic drop, hidden rarity, hidden quantity, atau Realm scaling. Jika source/input wajib tidak dapat divalidasi, hasil mekanis dapat menjadi `RESOLUTION-BLOCKED`.

## 8. DYNAMIC GENERATION
`systems/25_DYNAMIC_GENERATION.md` menggunakan status `UNRESOLVED` ketika input formula belum tersedia tanpa fallback resmi. Tier tetap berbeda dari Realm dan generated content tidak menjadi katalog global.

## 9. NPC / EVENT / QUEST
`systems/26_DYNAMIC_NPC_EVENT_QUEST.md` menggunakan `UNRESOLVED`, `NOT-ESTABLISHED`, dan `RESOLUTION-BLOCKED` sesuai keadaan data. NPC_ID, EVT_ID, dan QST_ID persisten harus stabil dan tidak digunakan ulang.

## 10. GARDENING
`systems/23_GARDENING.md` telah dimigrasikan ke schema-safe placeholders:
- `<GARDEN_ID>`
- `<LOCATION>`
- `<AREA>`
- `<VALUE_0_100>`
- `<CROP_BATCH>`
- `<QUANTITY>`
- `<DATE_OR_UNRESOLVED>`

Placeholder schema tidak boleh disimpan sebagai Current State aktif. Nilai runtime harus berasal dari state/resolusi yang sah.

## 11. SPIRIT BEAST
`systems/24_SPIRIT_BEASTS.md` menggunakan Model B. Beast bukan Item/Equipment/Inventory. BEAST_ID stabil dan persistent. Data yang belum tersedia mengikuti Data Completeness; tidak ada automatic taming, ownership, contract, evolution, healing, atau ability.

## 12. RUNTIME CHAIN
Chain yang harus konsisten:
`INDEX → MODULE_ROUTER → RUNTIME_ENGINE → STATE_VALIDATOR → ACTION_RESOLVER → SAVE_PIPELINE`

Setiap REQUIRED module harus berhasil dimuat. Tidak ada silent fallback. Save hanya dianggap synchronized setelah write-back dan fetch verification berhasil.

## 13. DATA COMPLETENESS
Status resmi:
- `CANON-ESTABLISHED`
- `STATE-ESTABLISHED`
- `RUNTIME-GENERATED`
- `NOT-ESTABLISHED`
- `NOT-INSTANTIATED`
- `UNRESOLVED`
- `RESOLUTION-BLOCKED`
- `NOT-APPLICABLE`

Legacy unknown marker tidak boleh digunakan pada active Canon/runtime.

## 14. HASIL MIGRASI SAAT INI
Direct fetch telah memverifikasi dan memigrasikan file-file yang diaudit pada tahap ini, termasuk Travel, Gardening, Core Rules, Techniques, Spirit Beast, Dynamic Generation, Dynamic NPC/Event/Quest, GM Checklist, State Validator, Save Pipeline, serta runtime terkait.

Status ini **bukan klaim bahwa setiap byte di seluruh repository telah melalui line-by-line static scan**. GitHub search index dapat tertinggal; direct fetch branch `main` adalah acuan verifikasi file yang disentuh.

## FINAL TARGET
Target Admin Canon:
1. Tidak ada legacy unknown marker di active Canon/runtime.
2. Tidak ada pola placeholder generik yang dapat disalahartikan sebagai nilai runtime.
3. Semua unknown menggunakan status data resmi.
4. Semua persistent entity memiliki ID/state/history/origin yang konsisten.
5. Pipeline runtime dan save tidak memiliki silent fallback.
6. CI lint menolak legacy unknown marker dan pola placeholder generik pada active Canon/runtime.
