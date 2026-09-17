# GM Validation Rules

Validasi lokasi, waktu, resource, inventory, equipment, teknik, combat, dan konsekuensi.

## Data Completeness Gate
Validasi wajib menerapkan `core/07_DATA_COMPLETENESS.md`: field belum tersedia harus memakai status resmi; `RUNTIME-GENERATED` wajib memiliki generator/formula/input sah; `NOT-INSTANTIATED` bukan entity aktif; `UNRESOLVED` bukan fakta; required input yang hilang tanpa fallback menjadi `RESOLUTION-BLOCKED`; tidak boleh ada tebakan, cache, real-world fallback, atau narrative convenience yang mengisi field material.
