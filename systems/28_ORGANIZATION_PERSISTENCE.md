# Module 28 — Organization Persistence

## Status
Admin Canon v1.1

## Purpose
Mengatur detail organisasi individual tanpa mengubah registry menjadi katalog naratif bebas.

## Source Priority
`Canon/Admin → Organization Registry Database → Individual Organization File → Current Organization State → Runtime Derived`

Individual file memberi granular detail, tetapi tidak boleh bertentangan dengan registry.

## Organization Identity
- ID organisasi stabil dan tidak berubah karena nama/lokasi/status.
- Membership, rank, contract, access, promotion, demotion, expulsion, dan internal status adalah state yang dapat berubah melalui resolusi sah.
- Organisasi tidak otomatis memberikan teknik, Realm, item, currency, authority, atau reward.

## Individual File Schema
- ID / nama / kategori / wilayah.
- Canon dan agenda.
- Struktur/hierarchy.
- Recruitment/access.
- Relations.
- Known NPCs bila benar-benar Canon.
- Known techniques/assets hanya jika sourced.
- Current state bila material.
- Origin/change log bila material.
- Data yang belum tersedia menggunakan status `UNRESOLVED` atau `NOT-INSTANTIATED` sesuai keadaan.

## Relations
Relasi antar-organisasi adalah contextual state. Jangan mengubah cooperative/competitive/transactional menjadi alliance/war tanpa trigger dan resolusi yang sah.

## Runtime
Jika organisasi relevan, Router memuat registry + individual file bila tersedia. Jika individual file tidak ada, gunakan registry dan jangan mengarang detail.

## Persistence
Perubahan material organisasi harus memiliki before → after, cause, resolution, source, Origin, dan write-back verification.

Character membership tidak otomatis mengubah seluruh organisasi.
