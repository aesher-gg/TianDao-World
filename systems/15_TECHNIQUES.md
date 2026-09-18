# 15 — TECHNIQUES

## 1. Sumber Teknik
Teknik harus memiliki **Technique Origin** yang menjelaskan sumber dan cara teknik diperoleh. Sumber yang valid dapat berupa Law, guru, manual, event, item, faction/organization, atau sumber Official/Custom yang benar-benar tersedia dan tercatat.

**Law Origin dan Technique Origin berbeda.** Law Origin membuktikan asal Cultivation Law; Technique Origin membuktikan asal teknik tertentu. Memiliki suatu Law tidak otomatis memberikan semua teknik yang berkaitan dengan Law tersebut.

## 2. Technique Origin — Definisi Operasional
Technique Origin adalah provenance resmi untuk setiap teknik yang dipasang pada Character State.

Minimal mencatat, sejauh relevan:
- `Technique`: nama teknik;
- `Source Type`: Law, Teacher, Manual, Event, Item, Faction, Official/Custom, atau tipe valid lain;
- `Source`: sumber spesifik;
- `Acquisition Method`: cara memperoleh/mempelajari;
- `Requirements`: syarat;
- `Training/Insight Process`: proses belajar/pemahaman;
- `World Time`: waktu resolusi;
- `Resolution`: hasil;
- `Status`: `VALIDATED & ACTIVE`, `VALIDATED & INACTIVE`, `PENDING VALIDATION`, atau `REJECTED`;
- `Origin Reference`: rujukan ke log/history/event/item/law yang mendukung.

Jika status belum dapat ditentukan secara sah, gunakan status kelengkapan data `UNRESOLVED` dan tahan aktivasi teknik.

## 3. Teknik Berbasis Law
Jika Source Type = `Law`, Technique Origin harus menunjuk ke **Cultivation Law yang aktif** dan Law Origin yang sah. Ini membuktikan hubungan sumber, tetapi tetap membutuhkan proses penguasaan teknik.

Contoh:

```text
Cultivation Law:
  Hukum Pedang Bunga Aprikot
Law Origin:
  Teacher → Li Xingchun → pengajaran langsung

Technique:
  Teknik X
Technique Origin:
  Source Type: Law
  Source: Hukum Pedang Bunga Aprikot
  Acquisition Method: latihan/pemahaman teknik
  Origin Reference: Law Origin + Character History
```

Teknik tidak boleh dianggap otomatis diperoleh hanya karena karakter memiliki Law.

## 4. Penguasaan
Penguasaan memiliki tingkat/progres hanya bila sistem teknik atau law mendefinisikannya. GM tidak menaikkan mastery secara otomatis.

## 5. Pengembangan Teknik Baru
Wajib memiliki sumber/panduan yang sah, waktu latihan realistis, biaya resource, dan risiko kegagalan. Pedoman minimum: teknik sederhana ≥1 minggu; teknik kompleks dapat membutuhkan berbulan-bulan.

Teknik baru tidak boleh dibuat hanya untuk memenuhi permintaan Player atau untuk memberikan power-up gratis.

## 6. Combat
Teknik dapat mengubah attack, defense, hit chance, status, mobilitas, resource cost, atau efek lain hanya jika definisinya tersedia.

## 7. Qi Cost
Biaya Qi/Stamina harus berasal dari teknik resmi/kustom. Jika biaya belum didefinisikan, GM tidak mengarang angka.

## 8. Origin Log
Setiap teknik baru dipasang ke karakter melalui Technique Origin dan timestamp. Klaim teknik tanpa asal ditolak.

Untuk perubahan penting, minimal catat:

```text
World Time
Character ID
Action/Event
Cause
Resolution
Before: Technique + Technique Origin
After: Technique + Technique Origin
Source
```

## 9. Validasi
Validator wajib memastikan:
1. teknik memiliki sumber yang valid;
2. Source Type sesuai sumber nyata;
3. jika berbasis Law, Law aktif dan Law Origin tervalidasi;
4. requirements dan training tidak dilewati;
5. efek, mastery, dan cost tidak diimprovisasi jika belum didefinisikan;
6. perubahan memiliki Origin Log/History yang dapat ditelusuri;
7. teknik tidak diberikan otomatis karena Realm atau kepemilikan Law.

## 10. Integrasi
Techniques terhubung dengan Cultivation Law, Law Origin, Combat, Vitality, Items, Organizations, dan Save Integrity.


## DATA COMPLETENESS TECHNIQUE GATE
Technique identity, source, acquisition, requirements, training, mastery, effect, cost, dan status wajib dapat ditelusuri ke source/Origin yang sah. UNRESOLVED berarti tidak aktif dan tidak boleh ditebak. Missing required provenance/acquisition → tahan aktivasi atau gunakan RESOLUTION-BLOCKED sesuai konteks.


## 11. Flight / Mobility Technique Boundary
- Teknik yang memberikan flight/aerial mobility harus mendefinisikan efeknya secara eksplisit sebelum efek tersebut dipakai dalam Travel.
- Bila teknik menetapkan flight capability tetapi tidak menetapkan speed, maximum range, duration, atau cost, field tersebut tidak boleh diimprovisasi.
- Travel mengambil flight speed dan batas penggunaan dari Technique/Item/Ability source yang tervalidasi; Travel tidak menciptakan stat flight baru.
- Teknik terbang yang baru diperoleh tetap membutuhkan Technique Origin, acquisition method, requirements, training/insight, dan validasi sebelum dapat dipasang sebagai aktif.


## 11A. Canon Flight Source References
Teknik flight yang menggunakan baseline Admin Canon harus menunjuk ke salah satu source resmi pada Module 20:
- FLY-SRC-001 — Teknik Perjalanan Awan Dasar — 60 Li/jam.
- FLY-SRC-002 — Teknik Perjalanan Awan Lanjutan — 120 Li/jam.
- FLY-SRC-003 — Teknik Arus Langit — 240 Li/jam.
- FLY-SRC-004 — Teknik Langit Roh — 480 Li/jam.
- FLY-SRC-005 — Teknik Melintasi Kekosongan — 800 Li/jam.
- FLY-SRC-006 — Teknik Jalan Bintang — 1.200 Li/jam.
- FLY-SRC-007 — Teknik Menembus Langit — 1.800 Li/jam.
- FLY-SRC-008 — Teknik Kenaikan Abadi — 2.500 Li/jam.

Reference ke source tersebut tidak menggantikan Technique Origin. Character tetap wajib memiliki acquisition, requirements, training/insight, dan status ACTIVE yang tervalidasi.


## 11B. Canon Boundary — Intrinsic Flight Is Not a Technique
- `FLY-INTRINSIC-001` is a **Cultivation/Realm capability** beginning at Realm 4, not a Technique record.
- It therefore does not require Technique Origin, acquisition event, manual, teacher, or learning history.
- Any **named Flight Technique** remains a separate technique entity and cannot be granted merely because the Character reaches Realm 4.
- A Flight Technique must still satisfy the complete Technique Origin gate: source, acquisition method, requirements, training/insight, resolution, status, and origin reference.
- The intrinsic capability does not satisfy the provenance requirements of any `FLY-SRC-*` technique.