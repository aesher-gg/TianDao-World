# 39 — Custom Events

## Status
Admin Canon — registry aktif; saat ini tidak ada Custom Event fixed yang diaktifkan.

## Boundary
File ini adalah sumber resmi untuk event khusus yang secara eksplisit ditetapkan Admin. Tidak ada entry berarti tidak ada Custom Event fixed aktif. Dynamic local event tetap mengikuti Module 26 dan tidak otomatis menjadi Custom Canon.

## Entry Schema
Setiap Custom Event fixed yang ditambahkan wajib memiliki:
- `EVT_ID`
- Nama event
- Scope
- Lokasi
- Trigger
- Waktu/jadwal bila relevan
- Kondisi awal
- Perubahan dunia/entity
- Affected entities
- Resolution/branch rules
- Completion condition
- Reward/reward provenance bila ada
- Origin
- History/Persistence boundary
- Status lifecycle

## Active Registry
`EMPTY — tidak ada Custom Event fixed aktif.`

## Runtime Rule
Custom Event hanya menjadi Canon setelah entry Admin tersimpan dan tervalidasi. Event dinamis yang dibuat Module 26 tetap berada pada scope runtime/persistence yang sah dan tidak berubah menjadi Global Canon secara otomatis.
