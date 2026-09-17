# UNRESOLVED CANON GAP AUDIT — 2026-09-17

## Status
**Admin Audit — Direct-Fetch Verified**

## Tujuan
Membedakan setiap penggunaan `UNRESOLVED` yang benar-benar merupakan kekosongan Canon yang masih dapat ditetapkan oleh Admin dari `UNRESOLVED` yang memang harus tetap dinamis, runtime, discovery-dependent, atau hanya berada di aturan/template.

## Metode
- Repository: `aesher-gg/TianDao-World`
- Branch: `main`
- HEAD yang diverifikasi sebelum audit: `d5f1acf4ecb2d5df03f2d13f5ff3094becf115b6`
- Dilakukan repository-wide search untuk `UNRESOLVED`, dilanjutkan direct fetch terhadap file yang mengandung penggunaan material.
- Direct fetch branch `main` diprioritaskan bila hasil search index menunjukkan revision lama.
- Keputusan klasifikasi memakai `core/07_DATA_COMPLETENESS.md`: `UNRESOLVED` bukan izin mengarang dan hanya boleh diubah bila sumber Canon/Admin yang sah tersedia.

## Kriteria Klasifikasi

### A. CANON GAP — BOLEH DIISI ADMIN
`UNRESOLVED` dikategorikan sebagai Canon gap bila:
1. field/entity bersifat static atau recurring Canon;
2. tidak ada alasan desain untuk menyembunyikannya sampai discovery/runtime;
3. nilai dapat ditetapkan sebagai Admin Canon tanpa melanggar dependency atau state isolation;
4. penetapan tersebut memperbaiki data operasional, bukan sekadar mengganti label.

### B. DINAMIS/RUNTIME — HARUS TETAP
`UNRESOLVED` dipertahankan bila nilai bergantung pada:
- discovery in-character;
- NPC/event/quest generated pada runtime;
- state Character atau Beast yang belum diinstansiasi;
- kondisi dunia aktual pada saat resolusi;
- input formula yang memang belum tersedia;
- rute/kecepatan/metode khusus yang belum memiliki sumber resmi;
- data yang sengaja tidak diketahui oleh Character;
- template schema yang belum menjadi Current State.

### C. RULE/TEMPLATE — BUKAN KEKOSONGAN CANON
Penggunaan `UNRESOLVED` di instruction, fallback rule, checklist, atau template tidak dianggap data Canon yang harus diisi.

## Hasil Audit

### 1. CANON GAP YANG DAPAT DIISI
#### Perkumpulan Tangan Abu — Pemimpin
**File:** `factions/criminal/00_CRIMINAL_DATABASE.md`

Sebelumnya:
- `Status pimpinan: UNRESOLVED`

Keputusan Admin:
- Pemimpin ditetapkan sebagai **Shen Kuang**.
- Peran, sifat, agenda, batas pengetahuan, dan provenance Canon ditetapkan.
- Status menjadi `CANON-ESTABLISHED`.

**Alasan:** ini adalah field struktural pada faction Canon yang tidak memiliki mekanisme discovery sebagai prasyarat. Mengisinya memperbaiki database faction secara substantif dan menyediakan identity yang dapat dirujuk NPC/GM bila diperlukan.

**Sinkronisasi NPC:** `lore/NPC_DATABASE.md` sekarang juga memiliki entri Canon Shen Kuang yang merujuk langsung ke CRI-005.

### 2. DINAMIS/RUNTIME — DIPERTAHANKAN

#### NPC yang belum diketahui Character
**File:** `lore/NPC_DATABASE.md`, `gm/NPC_EVENT_RUNTIME.md`, `core/04_ANTI_CHEAT.md`

`UNRESOLVED` tetap sah untuk identity NPC yang belum diketahui Character. Menetapkan semua identitas di muka akan melanggar discovery dan knowledge boundary.

#### Kriminal lain yang belum teridentifikasi
**File:** `lore/NPC_DATABASE.md`

Entri `Identitas Kriminal Belum Terungkap` tetap `UNRESOLVED`. Entri ini sekarang secara eksplisit dibedakan dari Shen Kuang; ia merepresentasikan kriminal lain yang belum ditemukan, bukan gap pada identity pemimpin CRI-005.

#### World Time yang belum memiliki source
**File:** `lore/CALENDAR.md`, `gm/RESPONSE_FORMAT.md`

`UNRESOLVED` adalah fallback sah bila Repository World Time dan Character State sama-sama tidak menyediakan komponen waktu. Saat ini tahun dunia sudah established sebagai **1200 Era Kebangkitan** di `story/WORLD_STATE.md`, sehingga fallback ini bukan kekosongan Canon aktif.

#### Travel distance tanpa baseline sah
**File:** `systems/20_TRAVEL_ROUTES.md`

`UNRESOLVED` tetap diperlukan untuk rute yang benar-benar belum memiliki baseline. Namun registry branch `main` saat audit telah memiliki baseline rute regional dan koridor utama yang diperiksa, sehingga tidak ada nilai static route tertentu yang perlu ditebak dari `UNRESOLVED` pada tahap audit ini.

#### Gardening runtime
**File:** `systems/23_GARDENING.md`

`<DATE_OR_UNRESOLVED>` adalah schema/template field untuk estimated harvest. Nilai aktual hanya dapat dihitung setelah Garden/Crop/condition/time tersedia. Ini bukan Canon gap.

#### Spirit Beast
**File:** `systems/24_SPIRIT_BEASTS.md`

Species, individual state, relationship, taming, ownership, contract, growth, evolution, ability, location, dan kondisi lain dapat belum terinstansiasi atau belum diketahui. Dynamic generation tidak boleh diubah menjadi katalog species global. `UNRESOLVED` tetap sah sesuai state aktual.

#### Dynamic Generation
**File:** `systems/25_DYNAMIC_GENERATION.md`

Input generator yang belum tersedia tanpa fallback resmi tetap `UNRESOLVED`/status completeness terkait. Generated content bukan Global Canon.

#### Dynamic NPC/Event/Quest
**File:** `systems/26_DYNAMIC_NPC_EVENT_QUEST.md`

Identity, trigger, input, atau detail yang hanya lahir dari runtime tetap dinamis. Sistem secara eksplisit melarang dynamic NPC diam-diam menjadi pemimpin faction atau tokoh Canon besar.

#### Cultivation Law / Technique Origin
**File:** `systems/09_CULTIVATION.md`, `systems/15_TECHNIQUES.md`

`UNRESOLVED` pada Origin template atau acquisition data berarti source belum terbukti. Itu bukan alasan untuk menetapkan Law/Technique baru. Nilai baru hanya boleh ditetapkan melalui Admin/Canon atau resolusi acquisition yang sah.

#### Organization contextual state
**File:** `systems/28_ORGANIZATION_PERSISTENCE.md`

Relasi, aset, current state, dan data anggota yang belum terjadi secara runtime tidak perlu dipaksakan menjadi Canon. Static organization registry yang ada sudah memiliki identity dasar.

## 3. RULE/TEMPLATE — JANGAN DIISI

Penggunaan `UNRESOLVED` di file berikut berfungsi sebagai aturan, checklist, fallback, atau schema:
- `core/07_DATA_COMPLETENESS.md`
- `gm/CHECKLIST.md`
- `gm/GM_PROMPT.md`
- `gm/ACTION_RUNTIME.md`
- `gm/RUNTIME_ENGINE.md`
- `gm/RESPONSE_FORMAT.md`
- `gm/PLAYER_BOOT_PROMPT.md`
- `gm/YELLOW_AUDIT.md`
- `core/04_ANTI_CHEAT.md`
- `core/05_SAVE_INTEGRITY.md`
- `systems/20_TRAVEL_ROUTES.md` (rule fallback)
- template Origin/State pada modul yang belum diinstansiasi

Menghapus `UNRESOLVED` dari instruction/template akan merusak kemampuan runtime untuk membedakan data yang benar-benar belum tersedia dari fakta Canon.

## Kesimpulan

Pada audit ini ditemukan **1 kekosongan Canon statis yang jelas dan layak diisi Admin**: pemimpin Perkumpulan Tangan Abu. Kekosongan tersebut telah diisi dan disinkronkan ke NPC Canon.

Penggunaan `UNRESOLVED` lainnya yang terverifikasi pada file material saat audit terbagi ke dalam tiga kelompok:
1. **Runtime/discovery-dependent** — harus tetap dinamis;
2. **Fallback/schema** — bukan data Canon aktif;
3. **Input yang belum sah untuk resolusi** — harus tetap `UNRESOLVED` atau naik menjadi `RESOLUTION-BLOCKED` saat wajib untuk formula.

Audit ini **tidak** menyimpulkan bahwa setiap kemungkinan lore masa depan sudah lengkap. Target yang benar adalah tidak ada `UNRESOLVED` yang sebenarnya merupakan data Canon statis yang sengaja dibiarkan kosong.

## Post-Audit Verification Target
- Verifikasi `factions/criminal/00_CRIMINAL_DATABASE.md` setelah write-back.
- Verifikasi `lore/NPC_DATABASE.md` setelah write-back.
- Search ulang `UNRESOLVED` untuk memastikan tidak ada kandidat statis lain yang muncul dari hasil index terbaru.
- Jangan mengubah `UNRESOLVED` yang berada di runtime/template menjadi fakta hanya demi mengurangi jumlah token.
