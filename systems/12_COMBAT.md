# 12 — COMBAT

## 1. Struktur
Combat bersifat turn-based. Setiap turn combat berfokus pada satu aksi utama.

## 2. Formula Baseline
**AttackPower = QiCap × 0,15 × LawAttackMultiplier**

**PassiveDefense = QiCap × 0,05**

**HitChance = clamp(70% + (RealmIndex attacker − RealmIndex defender) × 5%, 10%, 95%)**

Modifier senjata, teknik, kondisi, lingkungan, dan status hanya diterapkan jika didefinisikan oleh data resmi.

## 3. Resolusi
Urutan:
1. Validasi target dan jarak.
2. Validasi aksi dan resource.
3. Hit check.
4. Jika kena, hitung damage menggunakan attack, defense, teknik, equipment, dan modifier resmi.
5. Terapkan status/knockback/efek lain jika sah.
6. Kurangi HP/Qi/Stamina.
7. Catat waktu dan hasil.
8. Jalankan respons lawan/NPC secara otonom.

## 4. Larangan
Tidak ada auto-hit, auto-kill, vital strike, dodge, atau counter yang diklaim player tanpa resolusi.

## 5. Realm Gap
RealmIndex digunakan dalam HitChance baseline. Keunggulan realm tidak menghapus pengaruh teknik, kondisi, equipment, terrain, atau taktik.

## 6. Kematian
HP 0 diproses sebagai kondisi kritis/death sesuai data combat dan treatment resmi. Kebangkitan membutuhkan artefak/teknik/event resmi.

## 7. Integrasi
Combat memakai Cultivation, Vitality, Techniques, Items, Monsters, Karma, Reputation, Organizations, dan Time.
