# 07 — DATA COMPLETENESS & UNRESOLVED STATE

## Status
Admin Canon v1.1

## Purpose
Menetapkan satu cara resmi untuk merepresentasikan data yang belum diinstansiasi tanpa memakai tanda tanya dan tanpa mengizinkan GM mengarang nilai.

## Canonical Status Vocabulary
Gunakan salah satu status berikut:

- `CANON-ESTABLISHED` — nilai ditetapkan oleh World Bible/Admin Canon.
- `STATE-ESTABLISHED` — nilai berasal dari Current State yang telah diverifikasi.
- `RUNTIME-GENERATED` — nilai dibuat oleh Dynamic Generation yang valid untuk turn tersebut.
- `NOT-APPLICABLE` — field memang tidak berlaku untuk entity/action tersebut.
- `NOT-INSTANTIATED` — entity/field belum dibuat atau belum memiliki record runtime.
- `NOT-ESTABLISHED` — field relevan tetapi belum ditetapkan oleh Canon, State, atau resolusi valid.
- `RESOLUTION-BLOCKED` — hasil mekanis belum boleh ditetapkan karena input/validasi wajib belum terpenuhi.

## Hard Rule
- Legacy unknown marker tidak digunakan lagi di repository Canon/runtime.
- Token resmi untuk data yang belum tersedia adalah `UNRESOLVED` atau status yang lebih spesifik dari vocabulary di atas.
- Menggunakan `UNRESOLVED` atau `NOT-ESTABLISHED` tidak berarti GM boleh mengarang nilai.
- Jika nilai diperlukan untuk resolusi dan statusnya `NOT-ESTABLISHED`, gunakan rule fallback resmi bila tersedia; jika tidak tersedia, status resolusi menjadi `RESOLUTION-BLOCKED`.
- `NOT-INSTANTIATED` berbeda dari `NOT-ESTABLISHED`: yang pertama berarti record/entity belum dibuat; yang kedua berarti field pada entity yang sudah ada belum memiliki nilai Canon/state.

## Runtime Resolution
Prioritas:
`Canon/Admin → Fixed Source → Verified Current State → Valid Runtime Generation → NOT-ESTABLISHED`

Jika sebuah field wajib untuk formula tetapi belum tersedia:
`Required Input Missing → RESOLUTION-BLOCKED`

Tidak boleh:
- memakai angka dunia nyata sebagai fallback;
- memakai cache lama untuk menutup data hilang;
- mengubah status unresolved menjadi fakta hanya karena Player menginginkannya;
- menyimpan spekulasi sebagai Canon.

## Templates
Template boleh memakai placeholder deskriptif seperti `<CHARACTER_ID>`, `<LOCATION>`, `<TIME>`, `<VALUE>`, dan `<NOT-INSTANTIATED>`. Template tidak boleh memakai tanda tanya sebagai placeholder.

## Persistence
Status completeness tidak menggantikan Origin. Setiap nilai material yang kemudian ditetapkan tetap membutuhkan source, cause/resolution bila relevan, before → after, Origin/History, dan Save Pipeline.

## Audit Rule
Audit repository harus mencari:
1. legacy unknown marker;
2. placeholder `XX`, `XXXX`, `<...>` yang muncul di Current State aktif;
3. field wajib tanpa schema/default/status;
4. registry yang hanya berisi nama tanpa identity boundary, source, atau persistence rule;
5. modul yang dirujuk INDEX tetapi belum memiliki isi operasional.

Target production: tidak ada legacy unknown marker dan tidak ada field runtime aktif yang tidak memiliki status atau sumber.
