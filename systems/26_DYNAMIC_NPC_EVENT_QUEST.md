# 26 — DYNAMIC NPC, EVENT & QUEST GENERATION

> **Status:** Admin Canon v1.0
> **Tujuan:** memberi Qwen GM kerangka procedural untuk menghasilkan NPC, local event, dan quest secara dinamis tanpa mengubah TianDao-World menjadi katalog tertutup.

## 0. Prinsip Utama

TianDao-World menggunakan **open-world procedural generation**.

- Admin menetapkan formula, batas, identitas sistem, validasi, dan aturan persistence.
- Qwen GM menentukan hasil konkret saat runtime berdasarkan input yang benar-benar tersedia.
- Hasil generated bukan otomatis Global Canon.
- Fakta yang hanya muncul sebagai generated/local content tetap bersifat runtime sampai memiliki alasan persistence/Canon.
- Database fixed tetap boleh untuk NPC unik, event unik, quest resmi, tokoh penting, atau content yang sengaja ditetapkan Admin. Fixed content adalah pengecualian, bukan fondasi generasi dunia.

Urutan input:

`Canon/Admin Data → Current State → World Time → Region/Location → Faction/Organization → Active Threads/Events → Character Context → Runtime Roll → Generated Result`

Input mekanis yang diperlukan tetapi tidak tersedia dan tidak memiliki fallback resmi = `???`.

---

# 1. NPC GENERATION

## 1.1 Tujuan

NPC dinamis dipakai untuk membuat dunia terasa berpenghuni: pedagang, petani, pekerja, pengawal, murid, pemburu, tabib, pengelana, aparat lokal, praktisi lepas, saksi, rival, pemberi informasi, dan peran lokal lain yang masuk akal.

NPC dinamis tidak boleh dipakai untuk diam-diam menciptakan grandmaster, tokoh Canon besar, pemimpin faction, teknik rahasia, bloodline langka, atau lore unik tingkat tinggi.

## 1.2 Social Activity

Untuk menentukan peluang munculnya interaksi/NPC lokal, gunakan **Social Activity Base** berdasarkan tipe lokasi:

| Tipe lokasi | Base |
|---|---:|
| Ibukota/pusat pemerintahan | 70 |
| Kota/pusat perdagangan | 55 |
| Desa/permukiman kecil | 40 |
| Jalur dagang/karavan | 45 |
| Area perbatasan/pos perjalanan | 35 |
| Wilderness | 10 |
| Zona berbahaya/terisolasi | 5 |
| Tidak diketahui | `???` |

Modifier Social Activity: setiap faktor yang benar-benar relevan dapat memberi `-10` sampai `+10` berdasarkan keadaan Canon/runtime, misalnya jam aktivitas, festival terjadwal, kepadatan perjalanan, konflik lokal, cuaca ekstrem, atau event aktif.

`Social Activity = clamp(Base + Σ Modifier, 0, 100)`

Jika tipe lokasi tidak dapat ditentukan, jangan menebak base.

## 1.3 NPC Encounter Roll

`NPC Encounter Roll = d100`

NPC/local social encounter terjadi jika:

`Roll ≤ Social Activity`

Roll hanya menentukan apakah ada encounter; GM tetap menentukan siapa/berapa orang berdasarkan konteks.

## 1.4 NPC Composition

Jika encounter terjadi, GM menentukan:

1. jumlah NPC;
2. peran pekerjaan/fungsi;
3. identitas/nama bila layak diketahui;
4. faction/organization bila benar-benar ada dasar;
5. lokasi dan aktivitas;
6. temperament/personality;
7. agenda jangka pendek;
8. pengetahuan yang benar-benar tersedia;
9. sikap awal terhadap Character;
10. Realm/Stage hanya bila memiliki dasar yang sah;
11. apakah NPC sementara atau perlu persistence.

NPC biasa boleh memiliki Realm yang rendah atau `???`; **jangan mengisi Realm secara otomatis hanya karena NPC terlihat kompeten**.

## 1.5 NPC Identity & Persistence

NPC yang hanya lewat dan tidak menghasilkan perubahan material dapat tetap menjadi generated runtime NPC.

Jika NPC:
- menjadi recurring character;
- memiliki hubungan/reputasi yang berubah;
- memiliki kewajiban/kontrak penting;
- memegang informasi penting yang akan dipakai kembali;
- mengalami perubahan state material;
- menjadi target/partner quest;

maka NPC harus diberi **NPC_ID** stabil dan dapat dipersistenkan.

Format standar:

`NPC-0001`

Primary identifier adalah NPC_ID, bukan nama.

State persisten:

`characters/npcs/<NPC_ID>.md`

History opsional/persisten bila diperlukan:

`npc_history/<NPC_ID>_HISTORY.md`

Registry:

`characters/npc_registry.md`

NPC_ID tidak boleh berubah karena perubahan nama, faction, lokasi, hubungan, atau status.

NPC yang mati permanen tidak boleh membuat NPC_ID dipakai ulang.

## 1.6 NPC Knowledge Boundary

`NPC Knowledge = pengalaman + akses informasi + peran + kejadian yang benar-benar dialami`

- NPC tidak menjadi omniscient.
- Rumor dapat salah.
- NPC dapat berbohong atau menyembunyikan informasi.
- Pengetahuan Character dan NPC harus dipisahkan.
- NPC tidak otomatis mengetahui Player intent.

---

# 2. EVENT GENERATION

## 2.1 Dua Kelas Event

### A. Dynamic Local Event
Event lokal/insiden dapat dibuat Qwen secara procedural jika input valid, misalnya:
- kecelakaan perjalanan;
- perselisihan pasar;
- kehilangan barang;
- gangguan pekerjaan;
- konflik kecil;
- permintaan bantuan;
- perubahan aktivitas lokal;
- jejak creature/kriminal;
- masalah logistik;
- kejadian sosial biasa.

Local Event tidak otomatis menjadi World Event.

### B. Canon/Admin World Event
World Event regional/global tetap mengikuti `events/world_events/00_WORLD_EVENT_REGISTRY.md` dan trigger resminya. Dynamic generation tidak boleh mengganti trigger, scope, atau dampak event Canon.

Scheduled Event tetap mengikuti `events/scheduled_events/00_SCHEDULED_EVENT_REGISTRY.md`.

## 2.2 Local Event Pressure

Local Event tidak harus bergantung pada creature encounter. Gunakan **Social Activity** sebagai basis untuk event sosial/lokal. Jika event memiliki komponen creature/physical disturbance, Module 25 dapat menjadi input tambahan.

Untuk social-only/local event:

`Local Event Pressure = clamp(Social Activity + Σ Event Modifier, 0, 95)`

Untuk event yang secara material bergantung pada creature/encounter pressure:

`Local Event Pressure = clamp((Encounter Pressure + Social Activity) / 2 + Σ Event Modifier, 0, 95)`

Event Modifier per faktor yang benar-benar didukung: `-10` sampai `+10`.

Contoh faktor:
- event aktif;
- kepadatan manusia;
- gangguan baru;
- aktivitas faction;
- festival/scheduled event;
- cuaca ekstrem;
- aftermath aksi Character.

Tidak boleh membuat modifier numerik tersembunyi.

`Roll = d100`

Local event muncul jika:

`Roll ≤ Local Event Pressure`

Jika faktor mekanis yang dibutuhkan tidak tersedia, gunakan formula yang tidak membutuhkan faktor tersebut bila memang tersedia; jangan memasukkan `???` ke perhitungan seolah-olah bernilai nol.

## 2.3 Event Scope

Setiap generated event diberi scope:

- **Personal:** hanya Character/kelompok kecil.
- **Local:** lokasi/permukiman/route terbatas.
- **Regional:** memengaruhi beberapa lokasi dan membutuhkan dasar World Event/Canon.
- **Global:** hanya melalui Canon/Admin event yang sah.

Qwen tidak boleh menaikkan Local menjadi Regional/Global tanpa trigger atau Admin/Canon.

## 2.4 Event State

Event yang hanya selesai dalam satu resolusi tidak memerlukan persistence terpisah.

Event yang berlangsung lintas turn dan memengaruhi state material wajib memiliki:

- `EVENT_ID` unik;
- scope;
- waktu mulai;
- lokasi/scope;
- trigger;
- state sebelum;
- perubahan state;
- entity yang terpengaruh;
- checkpoint berikutnya;
- kondisi selesai;
- source/origin.

Format dynamic local event:

`EVT-0001`

World Event dan Scheduled Event mempertahankan ID Canon mereka (`WE-###`, `SE-###`).

Generated event tidak menjadi Canon global hanya karena memiliki EVENT_ID.

---

# 3. QUEST GENERATION

## 3.1 Prinsip

Quest adalah **tujuan/pekerjaan yang dapat dilakukan Character**, bukan hadiah gratis atau jalur cerita wajib.

Quest dapat muncul dari:
- kebutuhan NPC;
- agenda faction/organization;
- local event;
- active thread;
- kontrak yang sah;
- kebutuhan lokasi/komunitas;
- konsekuensi aksi Character;
- scheduled/world event yang benar-benar dapat diakses.

Tidak semua NPC memiliki quest.

## 3.2 Quest Generation Gate

Quest hanya boleh dihasilkan jika terdapat:

1. sumber kebutuhan/masalah yang valid;
2. tujuan yang jelas;
3. target/lokasi yang dapat dicapai;
4. metode penyelesaian yang masuk akal;
5. risiko atau biaya yang sesuai;
6. kondisi keberhasilan dan kegagalan;
7. reward yang memiliki sumber sah atau dapat dihasilkan melalui Loot/Item formula;
8. waktu/deadline bila memang ada dasar;
9. quest giver/issuer bila ada;
10. ID dan persistence bila quest lintas turn.

Jika salah satu komponen wajib tidak dapat ditentukan secara sah, quest tidak boleh dipaksakan menjadi valid; gunakan `???` atau jangan generate quest tersebut.

## 3.3 Quest Types

GM dapat memilih tipe berdasarkan sumber:

- Delivery/Transport
- Escort
- Gathering
- Hunting
- Investigation
- Rescue
- Protection
- Negotiation
- Retrieval
- Repair/Work
- Exploration
- Faction/Contract
- Personal request

Tipe quest tidak menentukan reward atau kesulitan secara otomatis.

## 3.4 Quest Difficulty

Gunakan sumber ancaman yang relevan, bukan Realm Character sebagai faktor scaling otomatis.

Untuk quest yang berhubungan dengan area/encounter:

`Quest Threat = Threat Score` dari Module 25 jika tersedia.

Untuk quest sosial/pekerjaan tanpa ancaman fisik, gunakan faktor risiko nyata: waktu, perjalanan, akses, sosial, material, dan konsekuensi. Jika tidak ada dasar numerik, tetap kualitatif (`rendah/sedang/tinggi`) dan jangan membuat angka baru hanya demi formula.

Quest tidak boleh menaikkan Threat hanya karena Character kuat.

## 3.5 Quest Resolution

Quest dapat berstatus:

`Offered → Accepted → Active → Completed`

atau:

`Offered → Declined`

`Accepted/Active → Failed`

`Accepted/Active → Abandoned`

`Active → Expired` hanya jika deadline resmi terpenuhi.

Quest gagal tidak otomatis memberi reward.

Quest sukses tidak otomatis berarti semua tujuan sekunder berhasil.

## 3.6 Quest ID & Persistence

Quest lintas turn harus memiliki:

`QST-0001`

Current Quest State:

`story/quests/<QUEST_ID>.md`

Quest yang masih aktif dicerminkan pada `story/ACTIVE_THREADS.md` bila memenuhi kriteria shared/continuity yang berlaku.

Quest History dapat dicatat pada history Character atau sumber quest sesuai scope; jangan menyalin seluruh state ke semua memory.

Quest ID stabil sampai quest selesai/diarsipkan dan tidak dipakai ulang.

## 3.7 Reward

Reward mengikuti prioritas:

`Fixed Canon/Event/Mission Reward → Valid Item/Economy/Contract Source → Dynamic Loot Formula → ???`

Tidak boleh:
- menciptakan item unik tanpa source;
- memberikan teknik baru tanpa Technique Origin;
- memberikan uang tanpa dasar ekonomi/quest;
- memberikan cultivation breakthrough gratis;
- menjadikan quest reward lebih tinggi hanya karena Character kuat.

Reward yang bersifat item wajib memiliki ownership/provenance sesuai `systems/14_ITEMS.md`.

---

# 4. RELATIONSHIP BETWEEN NPC → EVENT → QUEST

Pipeline normal:

`World Context → NPC/Social Activity → NPC Generation → NPC Agenda/Problem → Local Event (opsional) → Quest Candidate → Quest Validation → Quest Offer → Character Decision → Resolution → Consequence → State/Origin → Save`

Tidak semua tahap wajib terjadi.

Contoh:
- NPC bisa muncul tanpa quest.
- Event bisa terjadi tanpa NPC baru.
- Quest bisa berasal dari faction/contract tanpa NPC individual.
- Quest bisa menciptakan NPC target secara dynamic jika dibutuhkan dan valid.

---

# 5. ANTI-CHEAT / ANTI-RAILROADING

- Player tidak otomatis mendapat quest hanya karena meminta quest; GM harus generate berdasarkan dunia.
- Player tidak dapat memaksa NPC menerima permintaan.
- Quest tidak boleh berubah menjadi sukses karena Player menyatakan berhasil.
- NPC boleh menolak, berbohong, gagal, kabur, atau memiliki agenda sendiri.
- Event boleh tidak terjadi.
- Quest boleh gagal.
- Generated NPC/Event/Quest tidak boleh mengalahkan Canon/Admin.
- Character Realm tidak otomatis menaikkan kualitas NPC, Event, Quest, difficulty, atau reward.
- Tidak ada hidden time-skip untuk menyelesaikan quest.
- Quest dan event yang berlangsung lama tunduk pada Time System dan checkpoint maksimal sesuai Action System.

---

# 6. PERSISTENCE & ORIGIN

Perubahan material pada NPC/Event/Quest harus dapat ditelusuri:

`World Time / Entity ID / Action/Event / Cause / Resolution / Before / After / Source`

NPC material change → NPC State + NPC History bila relevan.

Quest material change → Quest State + Character History/Active Threads sesuai scope.

Event material change → Event state/log + World State/Timeline/Active Threads sesuai scope.

Generated content yang tidak material tidak perlu dipersistenkan hanya untuk membuat repository penuh.

---

# 7. VALIDATION GATE

Sebelum hasil generated diterapkan, validator memeriksa:

1. Canon/Admin consistency.
2. Location/region validity.
3. World Time validity.
4. NPC role and knowledge boundary.
5. NPC_ID uniqueness/stability bila persistent.
6. Event class/scope/trigger.
7. Event ID uniqueness/stability bila persistent.
8. Quest source, objective, target, method, risk, resolution.
9. Quest ID uniqueness/stability bila persistent.
10. Reward provenance.
11. Time/checkpoint limits.
12. Origin Log requirements.
13. Character/private/shared memory isolation.
14. Save Pipeline dan write-back verification.

Validation gagal → jangan terapkan perubahan material.

---

# 8. RUNTIME

`FRESH INDEX → LOAD RELEVANT CANON → LOAD STATE/TIME → SOCIAL/ENCOUNTER CONTEXT → NPC GENERATION → EVENT CHECK → QUEST CANDIDATE → VALIDATION → PLAYER CHOICE → ACTION RESOLUTION → CONSEQUENCE → ORIGIN/HISTORY → SAVE → WRITE-BACK VERIFY`

Module 25 tetap menjadi fondasi dynamic encounter/creature/loot. Module 26 memperluas prinsip yang sama ke NPC, local event, dan quest.

**Generated ≠ Canon. Persistent ≠ Global Canon.**

**END MODULE 26**
