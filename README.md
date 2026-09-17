# 🏯 TianDao-World

> **AI-driven Xianxia · Wuxia · Jianghu · Cultivation RPG**
>
> Dunia kultivasi open-world dengan **World Bible modular, AI Game Master, persistent state, dynamic generation, strict validation, dan konsekuensi yang konsisten**.

---

## 🌏 Tentang TianDao-World

**TianDao-World** adalah framework dunia dan runtime untuk roleplay kultivasi yang menempatkan **konsistensi dunia dan state** sebagai sumber kebenaran utama.

Dunia tidak dibatasi oleh daftar encounter atau NPC statis. AI Game Master dapat menghasilkan kejadian baru berdasarkan wilayah, habitat, waktu, aktivitas, event aktif, kondisi karakter, dan aturan yang ditetapkan Admin.

### Prinsip Utama

- 📖 **World Bible = Source of Truth**
- ⚔️ **Hardcore realism — tanpa plot armor**
- 🧭 **Open-world procedural generation**
- 👤 **Persistent Character / NPC / Spirit Beast State**
- 🧬 **Origin & provenance untuk perubahan material**
- 🎲 **Dynamic encounter, monster, loot, NPC, event, dan quest**
- 🔐 **Validation sebelum state diterapkan**
- 💾 **Save Pipeline + write-back verification**
- 🚫 **Tanpa free power-up, free item, free healing, atau hidden time skip**

---

## 🗺️ World Realms

| # | Realm | Modul |
|---|---|---|
| 01 | World Map | `realms/01_WORLD_MAP.md` |
| 02 | Cangyuan Plains | `realms/02_CANGYUAN_PLAINS.md` |
| 03 | Qingluan Mountains | `realms/03_QINGLUAN_MOUNTAINS.md` |
| 04 | Southern Yaohuang Domain | `realms/04_SOUTHERN_YAOHUANG_DOMAIN.md` |
| 05 | Dongming Sea | `realms/05_DONGMING_SEA.md` |
| 06 | Beiming Snowlands | `realms/06_BEIMING_SNOWLANDS.md` |
| 07 | Jinyan Desert | `realms/07_JINYAN_DESERT.md` |

Nama dan isi Realm mengikuti World Bible resmi repository.

---

## ⚙️ Sistem Utama

| Sistem | Fungsi |
|---|---|
| `09_CULTIVATION.md` | Realm, Stage, Qi, breakthrough, Cultivation Law & Law Origin |
| `11_VITALITY.md` | HP, Qi, Stamina, Satiety, fasting & recovery |
| `12_COMBAT.md` | Turn combat, Attack, Defense, Hit Chance & konsekuensi |
| `13_MONSTERS.md` | Monster & creature framework |
| `14_ITEMS.md` | Item, equipment, inventory & ownership |
| `15_TECHNIQUES.md` | Technique, mastery, source & Technique Origin |
| `18_LOOT.md` | Loot eligibility, quality, quantity & provenance |
| `19_REGIONAL_MONSTER_ECOSYSTEM.md` | Tekanan dan konteks ekologi wilayah |
| `20_TRAVEL_ROUTES.md` | Perjalanan, rute, kecepatan & waktu |
| `24_SPIRIT_BEASTS.md` | Spirit Beast lifecycle, relationship & persistence |
| `25_DYNAMIC_GENERATION.md` | Dynamic encounter, creature, Threat/Tier & loot |
| `26_DYNAMIC_NPC_EVENT_QUEST.md` | Dynamic NPC, event & quest |

---

## 🎲 Dynamic World Engine

TianDao-World menggunakan procedural generation dengan **batas dan formula ditentukan Admin**, sementara hasil konkret ditentukan saat runtime oleh AI Game Master.

```text
CANON / ADMIN DATA
        ↓
CURRENT STATE
        ↓
WORLD TIME
        ↓
REGION / HABITAT
        ↓
ACTIVE EVENT / THREAD
        ↓
CHARACTER CONTEXT
        ↓
RUNTIME ROLL
        ↓
GENERATED RESULT
        ↓
VALIDATION
        ↓
ORIGIN / HISTORY
        ↓
SAVE
        ↓
WRITE-BACK VERIFY
```

### Contoh Encounter

```text
World Context
 → Habitat
 → Encounter Pressure
 → d100 Roll
 → Encounter Composition
 → Threat Score
 → Creature Generation
 → Interaction / Combat
 → Loot Eligibility
 → Loot Potential
 → Loot Generation
 → Validation
 → Save
```

**Hasil procedural tidak otomatis menjadi Global Canon.** Dengan demikian dunia dapat terus berkembang tanpa berubah menjadi katalog statis.

---

## 🧬 Origin System

Setiap perubahan material membutuhkan asal-usul yang dapat diverifikasi.

### Cultivation Law → Law Origin

**Law Origin** menjelaskan bagaimana karakter memperoleh, mempelajari, mewarisi, mengembangkan, atau mengaktifkan Cultivation Law.

### Technique → Technique Origin

**Technique Origin** menjelaskan sumber dan proses karakter memperoleh teknik tertentu.

> Memiliki sebuah Cultivation Law **tidak otomatis memberikan semua teknik** yang berhubungan dengannya.

Origin system mencegah kemampuan, item, perubahan hukum, atau reward muncul tanpa sumber dan proses yang sah.

---

## 💾 Persistent State

State gameplay dipisahkan dari registry awal agar perkembangan karakter tidak tertukar dengan data awal.

```text
characters/
├── players.md                  # Player Registry
├── character_registry.md       # Character Registry
├── players/                    # Current Character State
├── beast_registry.md           # Spirit Beast Registry
├── beasts/                     # Current Spirit Beast State
├── npc_registry.md             # Persistent NPC Registry
└── npcs/                       # Persistent NPC State

character_history/              # Character continuity
beast_history/                  # Spirit Beast continuity
npc_history/                    # Persistent NPC continuity

story/
├── WORLD_STATE.md              # Shared world consequences
├── ACTIVE_THREADS.md           # Unresolved story threads
├── STORY_TIMELINE.md           # Major chronology
└── quests/                     # Persistent Quest State
```

Perubahan material harus melewati **Save Pipeline**, lalu hasil write-back diverifikasi.

---

## 🤖 AI Game Master Runtime

AI Game Master menjalankan dunia berdasarkan repository; ia tidak boleh menciptakan aturan baru secara sembarangan.

### Setiap Turn

1. **Fresh fetch `INDEX.md`**
2. Muat Core Rules dan sumber yang relevan
3. Muat Current State yang sesuai
4. Evaluasi player intent
5. Resolve aksi berdasarkan aturan
6. Validasi hasil
7. Catat Origin/History bila diperlukan
8. Save perubahan material
9. Verify write-back
10. Tampilkan hasil kepada player

Jika write-back gagal, perubahan yang belum tersinkron **bukan Canon tersimpan** dan harus mengikuti `gm/PENDING_SYNC.md`.

---

## 🚫 Hardcore & Anti-Cheat

TianDao-World secara eksplisit menolak:

- ❌ Plot armor
- ❌ Auto-hit / auto-kill
- ❌ Free healing
- ❌ Free item atau currency
- ❌ Free technique / breakthrough
- ❌ Inventaris tanpa asal-usul
- ❌ Hidden time skip
- ❌ NPC maha tahu
- ❌ Automatic Realm-based reward scaling
- ❌ Player intent yang diperlakukan sebagai fakta tanpa resolusi
- ❌ Hasil procedural yang otomatis menjadi Global Canon

Jika informasi memang belum tersedia dan tidak memiliki fallback resmi, gunakan **`UNRESOLVED`** atau status Data Completeness yang lebih spesifik, bukan mengarang fakta.

---

## 📚 Repository Structure

```text
TianDao-World/
├── core/                       # Aturan fundamental game
├── realms/                     # Geografi & wilayah dunia
├── systems/                    # Gameplay systems
├── factions/                   # Sect / Dojo / Faction databases
├── loot/                       # Fixed loot table registry
├── characters/                 # Character / Beast / NPC state
├── character_history/          # Character history
├── beast_history/              # Spirit Beast history
├── npc_history/                # Persistent NPC history
├── story/                      # World state & quest state
├── events/                     # Custom / World / Scheduled events
├── custom/                     # Custom Law / Sect / Technique
├── lore/                       # Cities, NPC, history & lore
├── gm/                         # AI Game Master runtime
└── audits/                     # Repository audits
```

---

## 🧭 Source of Truth

Mulai dari:

- `INDEX.md` — **World Bible Index & Load Order**
- `core/00_CORE_RULES.md` — Core Rules
- `core/05_SAVE_INTEGRITY.md` — Save Integrity
- `core/06_ID_AND_SAVE_SYSTEM.md` — ID & Save System
- `gm/RUNTIME_ENGINE.md` — Runtime Engine
- `gm/STATE_VALIDATOR.md` — State Validation
- `gm/SAVE_PIPELINE.md` — Save Pipeline
- `gm/GM_PROMPT.md` — AI Game Master contract
- `gm/ACTION_RUNTIME_PROMPT.md` — Runtime action contract

### Dynamic Systems

- `systems/25_DYNAMIC_GENERATION.md`
- `systems/26_DYNAMIC_NPC_EVENT_QUEST.md`

### Spirit Beast

- `systems/24_SPIRIT_BEASTS.md`
- `characters/beast_registry.md`

---

## 🚀 Memulai Roleplay

### Character Boot

Gunakan:

`gm/PLAYER_BOOT_PROMPT.md`

Boot memuat World Bible, current state, dan memory yang relevan sesuai Load Order.

### Gameplay Turn

Gunakan:

`gm/ACTION_RUNTIME_PROMPT.md`

Setiap player message adalah turn baru dan memulai dengan fresh repository verification sesuai Runtime Contract.

### Response Format

`gm/RESPONSE_FORMAT.md`

---

## 🏯 Filosofi Dunia

> **Dunia tidak berputar mengelilingi player.**

Dunia berjalan berdasarkan aturan, waktu, manusia, monster, organisasi, sumber daya, dan konsekuensi.

Player dapat menjadi tokoh penting melalui **tindakan, keputusan, hubungan, dan pencapaian nyata** — bukan karena sistem memberikan perlindungan khusus.

Setiap pilihan dapat membuka peluang, menciptakan hubungan, menghasilkan keuntungan, menimbulkan risiko, atau meninggalkan konsekuensi jangka panjang.

**Di TianDao-World, tindakan memiliki asal-usul. Dunia memiliki ingatan. Dan setiap konsekuensi harus dapat dipertanggungjawabkan oleh state.**

---

## 📜 Status

**TianDao-World — Admin Canon · Active Development**

Repository terus dikembangkan dan diaudit untuk menjaga konsistensi:

**World Bible → Runtime → Validation → Origin/History → Save → Persistent State**

---

<p align="center">
  <b>天道无情 · 众生自渡</b><br>
  <i>The Heavenly Dao is impartial. Every being walks its own path.</i>
</p>
