# Persistent World State

> Shared world facts with ongoing consequences. Bukan pengganti Canon database, faction registry, atau event registry.

## Current World Year
- Status: Established by Admin
- World Year: **1200 Era Kebangkitan**
- Era: Era Kebangkitan

## Per-Character Time
Musim, tanggal, hari, cuaca, dan jam tidak ditetapkan global. Komponen tersebut dapat berbeda per Character dan ditentukan GM dari konteks awal yang sah. Waktu nyata/2026 bukan World Year.

## Active Shared Facts
- Current World Year is officially **1200 Era Kebangkitan**.

## Dynamic World State Rules
Catat hanya fakta dunia yang telah terselesaikan dan memiliki konsekuensi terhadap lebih dari satu Character atau terhadap simulasi dunia berikutnya.

### Scope
- Personal → Character History, bukan World State.
- Local → hanya shared bila memengaruhi lokasi/kelompok lebih luas.
- Regional → membutuhkan resolusi/trigger yang benar-benar berdampak regional.
- Global → hanya Canon/Admin atau resolusi yang secara sah berdampak global.

### State Categories
- keamanan/konflik wilayah
- kondisi jalur perjalanan
- perubahan ekonomi/logistik yang terkonfirmasi
- event aktif dan konsekuensinya
- perubahan lingkungan/habitat yang menetap
- faction/organization state yang benar-benar berscope shared
- NPC/Quest/Beast consequences yang berdampak pada dunia bersama

## Update Gate
Perubahan World State wajib memiliki:
`World Time / Scope / Entity/Event ID bila ada / Cause / Resolution / Before → After / Source`

Perubahan speculative, rumor, niat NPC, atau kemungkinan masa depan tidak boleh dicatat sebagai fakta.

## Cross-Entity Rule
Character State tidak otomatis menjadi World State. NPC/Event/Quest/Organization hanya masuk shared state jika scope dan konsekuensinya memenuhi validation.

## Persistence
Setelah resolusi, gunakan State Validator dan Save Pipeline. Jika write-back gagal, gunakan `PENDING SYNC`; jangan menganggap fakta sudah Repository Saved.

## Metadata
- Version: 5
- Last Admin Expansion: 2026-09-14
