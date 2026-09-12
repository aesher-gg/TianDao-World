# Spirit Beast Registry

Registry global untuk pemetaan `BEAST_ID` ke Current Beast State dan lifecycle status.

## Rules

- Setiap persistent Spirit Beast wajib memiliki `BEAST_ID` unik.
- Format standar: `BEAST-0001`.
- BEAST_ID stabil dan permanen sepanjang lifecycle data.
- Nama Beast bukan primary identifier.
- BEAST_ID tidak berubah karena rename, ownership transfer, contract, atau evolution.
- BEAST_ID tidak boleh digunakan ulang setelah permanent death/archive.
- Registry bukan Current Beast State dan bukan Beast History.
- Current State berada di `characters/beasts/<BEAST_ID>.md`.
- History berada di `beast_history/<BEAST_ID>_HISTORY.md`.
- Registry hanya mencatat mapping dan status administratif minimum yang diperlukan untuk discovery/integrity.

## Record Format

```text
BEAST_ID:
Name:
Current State:
History:
Owner Character ID:
Ownership Status:
Lifecycle Status:
```

Unknown tetap `???`; jangan mengarang record Beast yang belum resmi dibuat.
