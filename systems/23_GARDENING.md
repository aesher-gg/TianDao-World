# 🌱 System 23 — Gardening

> **Kategori:** Life Skill · Farming · Survival · Economy
> **Tujuan:** Sistem berkebun yang realistis tetapi dipercepat untuk gameplay berbasis teks.

## 1. Prinsip Utama

Berkebun bukan aksi instan. Tanaman membutuhkan benih, media tanam, air, cahaya, nutrisi, waktu, dan perawatan.

Time-scale sengaja dipercepat agar gameplay tidak memaksa Player menunggu waktu dunia nyata yang terlalu panjang.

Prinsip desain: **Realistic Process + Accelerated Gameplay Time.**

---

## 2. Siklus Tanaman

`Benih → Penanaman → Perkecambahan → Pertumbuhan → Pematangan → Panen`

GM tidak boleh memberikan hasil panen sebelum waktu pertumbuhan yang sesuai terpenuhi.

---

## 3. Batas Waktu Pertumbuhan

### Tanaman Biasa
- Tanaman biasa: waktu tumbuh **maksimal 7 hari in-game**, tergantung jenis tanaman. Tidak ada tanaman biasa yang boleh diberi waktu tumbuh >7 hari tanpa Admin override eksplisit.
- Tanaman spiritual: waktu tumbuh **maksimal 15 hari in-game**, tergantung jenis tanaman. Tidak ada tanaman spiritual yang boleh diberi waktu tumbuh >15 hari tanpa Admin override eksplisit.
- **Batas maksimal: 10 hari in-game.**
- Berlaku untuk sayuran, tanaman pangan cepat, herbal biasa, dan tanaman non-spiritual lain yang termasuk kategori biasa.

### Tanaman Spiritual
- Durasi pertumbuhan tanaman spiritual: maksimal 15 hari in-game, tergantung jenis tanaman dan kondisi yang memiliki source sah.
- **Batas maksimal standar: 60 hari (2 bulan) in-game.**
- Tanaman khusus buatan Admin dapat memiliki aturan tersendiri jika terdokumentasi.

Angka tersebut adalah batas/spektrum gameplay, bukan jaminan panen sempurna.

---

## 4. Status Numerik Kebun

Setiap kebun yang aktif dan relevan dapat memiliki status 0–100 berikut:

| Status | Rentang | Arti |
|---|---:|---|
| Soil Quality | 0–100 | Kualitas/kesuburan media tanah |
| Moisture | 0–100 | Kelembapan/ketersediaan air |
| Nutrition | 0–100 | Nutrisi yang tersedia |
| Cleanliness | 0–100 | Kebersihan dari gulma/sisa yang mengganggu |
| Pest Control | 0–100 | Tingkat perlindungan terhadap hama; semakin tinggi semakin baik |
| Environment | 0–100 | Kesesuaian lingkungan dengan tanaman |
| Irrigation | 0–100 | Efektivitas sistem penyiraman |
| Overall Condition | 0–100 | Ringkasan kondisi kebun, bukan pengganti status individual |

**Konvensi:** untuk status positif, semakin tinggi semakin baik. Status negatif seperti Disease dan Pest menggunakan konvensi terpisah pada status tanaman.

### Interpretasi umum Overall Condition
- 90–100: Sangat baik
- 75–89: Baik
- 50–74: Cukup
- 25–49: Buruk
- 0–24: Kritis

Overall Condition harus diturunkan dari kondisi kebun yang relevan dan tidak boleh dipilih acak.

---

## 5. Status Numerik Tanaman

Setiap tanaman individual atau kelompok tanaman homogen yang perlu dilacak dapat memiliki:

| Status | Rentang | Arti |
|---|---:|---|
| Growth | 0–100 | Kemajuan pertumbuhan |
| Health | 0–100 | Kesehatan tanaman |
| Water | 0–100 | Kecukupan air |
| Nutrition | 0–100 | Kecukupan nutrisi |
| Disease | 0–100 | Beban penyakit; semakin tinggi semakin buruk |
| Pest | 0–100 | Tekanan hama; semakin tinggi semakin buruk |
| Quality Potential | 0–100 | Potensi kualitas hasil jika kondisi tetap mendukung |
| Maturity | 0–100 | Tingkat kematangan menuju panen |

**Catatan penting:** Growth dan Maturity tidak harus selalu identik. Growth menggambarkan perkembangan biologis, sedangkan Maturity menentukan kesiapan panen.

---

## 6. Jumlah dan Kelompok Tanaman

GM boleh memakai satu status bersama untuk satu batch tanaman apabila tanaman:
- jenisnya sama,
- ditanam pada waktu yang sama atau hampir sama,
- berada pada kondisi lingkungan yang sama.

Tanaman harus dilacak secara individual apabila terdapat kondisi material yang berbeda, misalnya penyakit, mutasi, kualitas langka, atau status spiritual khusus.

Contoh:

```text
Crop Batch: Sayuran
Quantity: 10
Growth: 45/100
Health: 88/100
Water: 72/100
Nutrition: 61/100
Disease: 3/100
Pest: 8/100
Quality Potential: 67/100
Maturity: 45/100
```

---

## 7. Hubungan Status

Status tidak berubah tanpa sebab.

Contoh hubungan normal:
- Penyiraman yang efektif → Moisture kebun dan Water tanaman meningkat.
- Kekurangan air berkepanjangan → Water turun, lalu Health dan Growth dapat turun.
- Pemupukan → Nutrition meningkat dalam batas yang sesuai.
- Pemupukan berlebihan → dapat menurunkan Health.
- Gulma/perawatan buruk → Cleanliness turun.
- Hama → Pest naik dan dapat menurunkan Health/Growth.
- Penyakit → Disease naik dan dapat menurunkan Health/Growth.
- Lingkungan tidak sesuai → Environment turun atau efektivitasnya terhadap tanaman berkurang.
- Perawatan baik → membantu mempertahankan Health dan Quality Potential.

Tidak semua aksi harus mengubah semua angka.

---

## 8. Threshold Kondisi

Status 0–100 digunakan sebagai nilai kontinu, bukan tombol otomatis.

Panduan umum:

- 90–100: optimal/sangat baik
- 75–89: baik
- 50–74: normal/cukup
- 25–49: buruk
- 1–24: kritis
- 0: gagal/terputus total untuk status yang relevan

Untuk **Disease** dan **Pest**, interpretasinya terbalik:
- 0–10: minimal
- 11–25: ringan
- 26–50: sedang
- 51–75: berat
- 76–100: kritis

Threshold tidak boleh menyebabkan efek ajaib. GM tetap mempertimbangkan jenis tanaman dan konteks.

---

## 9. Perawatan

Aksi berkebun dapat meliputi:
- membersihkan lahan,
- menggemburkan tanah,
- menanam,
- menyiram,
- menyiangi,
- memberi pupuk,
- memeriksa tanaman,
- mengendalikan hama/penyakit,
- memperbaiki irigasi,
- memanen.

Aksi menggunakan waktu dan stamina sesuai Action System. Aktivitas fisik tidak boleh mengabaikan batas aksi biasa.

---

## 10. Passive Growth

Tanaman tetap tumbuh ketika Player melakukan aktivitas lain atau tidur, selama waktu benar-benar berlalu dan kondisi kebun memungkinkan.

GM harus menghitung perubahan berdasarkan durasi yang telah berlalu. Tidak boleh membuat tanaman matang melalui hidden time skip.

Player tidak harus menyiram atau mengamati tanaman setiap jam. Frekuensi perawatan mengikuti kebutuhan tanaman dan kondisi aktual.

---

## 11. Risiko

Kegagalan tidak otomatis terjadi setiap siklus. GM menilai risiko berdasarkan kondisi nyata:
- benih buruk,
- tanah buruk,
- air tidak cukup/berlebihan,
- lingkungan buruk,
- hama,
- penyakit,
- cuaca ekstrem,
- kerusakan fisik,
- kelalaian perawatan.

Hasil panen tidak dijamin 100% sempurna.

---

## 12. Panen

Tanaman dapat dipanen setelah Maturity mencapai tingkat yang sesuai dengan spesiesnya dan kondisi dunia.

Hasil dipengaruhi oleh:
- jumlah tanaman yang bertahan,
- Health,
- Quality Potential,
- kondisi kebun,
- waktu panen,
- metode panen,
- faktor khusus tanaman.

Benih yang ditanam tidak otomatis menghasilkan jumlah hasil yang identik.

---

## 13. Tanaman Spiritual

Tanaman spiritual hanya boleh ada jika sumbernya sah melalui Canon, Admin, penemuan gameplay yang valid, perdagangan, hadiah, eksplorasi, atau Origin lain yang dapat dibuktikan.

Tanaman spiritual dapat memiliki kebutuhan tambahan seperti Qi lingkungan atau media khusus.

Efek spiritual tidak boleh diciptakan hanya karena Player menyatakannya.

---

## 14. Percepatan

Pertumbuhan dapat dipercepat hanya dengan metode valid seperti pupuk khusus, tanah khusus, air spiritual, teknik, formation, artefak, atau kemampuan yang memiliki Origin.

Percepatan tidak boleh mengabaikan batas logika tanaman tanpa sumber resmi.

---

## 15. Ekonomi

Harga hasil panen dipengaruhi oleh kualitas, jumlah, permintaan, lokasi, musim, kelangkaan, dan kondisi pasar.

Panen dalam jumlah besar tidak menjamin harga maksimum.

Tanaman spiritual dapat memiliki pasar dan pembeli yang lebih terbatas daripada tanaman biasa.

---

## 16. Penyimpanan

Hasil panen dapat kehilangan kualitas atau membusuk seiring waktu jika tidak disimpan dengan benar.

Penyimpanan khusus dapat memperpanjang masa simpan jika tersedia secara sah.

---

## 17. Origin dan Save Integrity

Benih, pupuk, alat, hasil panen penting, tanaman spiritual, dan aset kebun yang material harus memiliki Origin yang dapat ditelusuri.

Perubahan material harus mengikuti:

`Intent → Context → Validation → Cost → Resolution → Consequence → State Update → Origin Log → State Validator → Memory Update → Write-Back`

Perubahan dapat mencakup:
- jumlah benih,
- jumlah tanaman,
- status kebun,
- status tanaman,
- hasil panen,
- inventory,
- currency,
- kepemilikan lahan,
- kontrak perdagangan.

---

## 18. Persistent Story Memory

Masukkan ke Character History hanya jika memiliki konsekuensi jangka panjang, misalnya:
- Player memperoleh kebun tetap.
- Player menemukan tanaman spiritual penting.
- Player mendapatkan teknik berkebun.
- Player membuat hubungan penting dengan petani/pembeli.
- Kebun menjadi sumber ekonomi tetap.
- Kebun hancur akibat peristiwa penting.
- Terbentuk kontrak perdagangan penting.

Aktivitas rutin tanpa konsekuensi penting tidak perlu memenuhi memory persisten.

---

## 19. Anti-Exploit

Dilarang:
- panen instan,
- menggandakan benih tanpa metode,
- menggandakan hasil,
- menciptakan tanaman spiritual tanpa Origin,
- mengklaim semua tanaman berhasil,
- mengklaim semua hasil sempurna,
- menjual hasil dengan harga tidak masuk akal,
- membuat waktu berlalu secara tersembunyi.

---

## 20. Format Status Runtime

Jika status kebun relevan dalam gameplay, GM dapat menggunakan format:

```text
┌── Garden Status ──┐
Garden ID: <GARDEN_ID>
Location: <LOCATION>
Area: <AREA>
Soil Quality: <VALUE_0_100>/100
Moisture: <VALUE_0_100>/100
Nutrition: <VALUE_0_100>/100
Cleanliness: <VALUE_0_100>/100
Pest Control: <VALUE_0_100>/100
Environment: <VALUE_0_100>/100
Irrigation: <VALUE_0_100>/100
Overall Condition: <VALUE_0_100>/100

Crop Batch: <CROP_BATCH>
Quantity: <QUANTITY>
Growth: <VALUE_0_100>/100
Health: <VALUE_0_100>/100
Water: <VALUE_0_100>/100
Nutrition: <VALUE_0_100>/100
Disease: <VALUE_0_100>/100
Pest: <VALUE_0_100>/100
Quality Potential: <VALUE_0_100>/100
Maturity: <VALUE_0_100>/100
Estimated Harvest: <DATE_OR_UNRESOLVED>
└────────────────────┘
```

Gunakan `UNRESOLVED` jika data belum diketahui. Jangan mengisi angka yang tidak memiliki dasar.

### Template Status
- `<GARDEN_ID>` adalah field identitas yang harus diganti dengan Garden ID nyata saat kebun dipersistenkan.
- `<LOCATION>` dan `<AREA>` harus diisi dari state/lokasi yang sah.
- `<VALUE_0_100>` adalah placeholder schema, bukan nilai runtime.
- `<QUANTITY>` harus berupa jumlah yang benar-benar diketahui setelah validasi.
- `<DATE_OR_UNRESOLVED>` harus berupa waktu panen yang dapat dihitung dari data sah, atau `UNRESOLVED` bila belum dapat dihitung.
- Template tidak boleh disimpan sebagai Current State aktif tanpa mengganti placeholder schema dengan data valid atau status yang sesuai.

---

## 21. Aturan untuk AI Game Master

1. Load modul ini bila berkebun/tanaman/kebun relevan.
2. Jangan membuat angka secara acak tanpa sebab.
3. Setiap perubahan numerik harus mempunyai penyebab yang dapat dijelaskan.
4. Gunakan skala 0–100 secara konsisten.
5. Bedakan status positif dan status negatif.
6. Jangan memberikan panen sebelum waktu pertumbuhan terpenuhi.
7. Tanaman biasa memiliki batas maksimal 10 hari.
8. Tanaman spiritual memiliki batas maksimal standar 60 hari.
9. Jangan membuat hidden time skip.
10. Jangan menjamin hasil panen sempurna.
11. Tanaman spiritual membutuhkan Origin yang valid.
12. Material change wajib masuk Save Pipeline dan State Validator.
13. Gunakan Current Character State sebagai state aktif, bukan Player Registry.
14. Jika data tidak diketahui, gunakan `UNRESOLVED`.

## 22. Prinsip Akhir

Sistem berkebun harus memberikan rasa:

**menanam → merawat → melihat angka berkembang → menghadapi risiko → menunggu waktu yang wajar → memanen → memperoleh hasil yang masuk akal.**

Sistem harus realistis dalam sebab-akibat, tetapi cepat dalam time-scale agar cocok untuk game berbasis teks.


## 23. Persistence and Runtime Integrity Gate
Gardening entities that persist across turns must use stable IDs and explicit state/history rather than narrative-only memory.

Recommended persistence paths:
- `characters/garden_registry.md`
- `characters/gardens/<GARDEN_ID>.md`
- `garden_history/<GARDEN_ID>_HISTORY.md`

Minimum persistent Garden State: GARDEN_ID, owner/controller or `UNRESOLVED`, location, area, garden statuses, active Crop Batch IDs or `NOT-INSTANTIATED`, Last World Time, and Origin.

Minimum persistent Crop Batch State: CROP_BATCH_ID, Garden ID, crop identity/source, quantity, planting World Time, Growth, Health, Water, Nutrition, Disease, Pest, Quality Potential, Maturity, Estimated Harvest or `UNRESOLVED`, and Origin.

A template or narrative mention does not create a persistent garden. Create/update registry, state, and history only after a valid resolution.

## 24. Numeric Resolution and Anti-Cheat Gate
The 0–100 ranges define domains, not free numeric choices. Every numeric change must have a source, cause, and bounded rule.

- Do not invent numeric changes such as `+10` or `-20` when Canon provides no rate.
- Passive Growth requires a sourced growth-rate rule; otherwise the numeric result is `UNRESOLVED` or `RESOLUTION-BLOCKED`.
- Random pest, disease, weather, failure, or similar outcomes require the verifiable RNG contract in `core/04_ANTI_CHEAT.md`.
- No narrative reroll, substitution, or result rewrite is permitted.
- Harvest quantity/quality requires a valid formula or fixed source; a 0–100 plant status is not itself a harvest formula.

## 25. Cross-Module Boundary
- Time/growth: `core/02_TIME_SYSTEM.md` + Gardening.
- Action/time/stamina cost: `core/03_ACTION_SYSTEM.md` + `systems/11_VITALITY.md` when Vitality is affected.
- Seed/material/item identity: `systems/14_ITEMS.md` and valid acquisition source.
- Harvest/loot: `systems/18_LOOT.md` + `systems/25_DYNAMIC_GENERATION.md` when dynamic loot is used.
- Economy/market: `systems/10_ECONOMY.md` + `systems/21_REGIONAL_ECONOMY.md` when regional market data is required.
- Crafting/processing: `systems/31_CRAFTING_FORGING.md` or `systems/32_ALCHEMY_PILLS.md` when applicable.
- Persistence: `core/05_SAVE_INTEGRITY.md`, `core/06_ID_AND_SAVE_SYSTEM.md`, State Validator, and Save Pipeline.

A consumer module may not invent gardening values supplied by this module, and Gardening may not invent values owned by another source.

## DATA COMPLETENESS GARDEN GATE
Seed identity, growth, maturity, yield, quality, effect, harvest time, dan mutation hanya boleh berasal dari source/formula/state yang sah. Jangan mengisi field kebun dengan angka atau properti yang tidak bersumber. Entity/state yang belum dibuat tetap NOT-INSTANTIATED; data yang belum dapat ditentukan tetap UNRESOLVED.
