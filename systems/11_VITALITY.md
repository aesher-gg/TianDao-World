# 11 — VITALITY

## 1. HP
**HPMax = QiCap × 0,4 × LawHPMultiplier**

LawHPMultiplier harus berasal dari law resmi/kustom. Jika multiplier = 1, HPMax mengikuti baseline QiCap × 0,4.

## 2. Qi
Qi memiliki batas maksimum **QiCap**. Qi yang digunakan teknik/combat berkurang dari current Qi; regenerasi harus mengikuti law, kondisi, teknik, item, lingkungan, atau waktu yang sah.

## 3. Stamina
Stamina adalah resource aktivitas fisik. TianDao-World menggunakan **Konsep C — Hybrid** untuk kapasitas maksimum stamina.

### 3.1 Stamina Baseline per Realm
Realm menentukan baseline kapasitas stamina. Baseline standar:

| Realm | Stamina Baseline |
|---|---:|
| Mortal | 100 |
| Meridian Opening | 120 |
| Qi Refining | 150 |
| Foundation Establishment | 200 |
| Core Formation | 300 |
| Nascent Soul | 450 |
| Soul Transformation | 650 |
| Void Severing | 900 |
| Tribulation Crossing | 1.200 |
| Immortal Ascension | 1.600 |

Mortal tidak memiliki Stage kultivasi dan menggunakan baseline Mortal 100.

### 3.2 Stage Multiplier
Untuk Realm yang memiliki Stage:
- **Early:** ×1,00
- **Middle:** ×1,10
- **Peak:** ×1,20

**StageBaselineStamina = RealmStaminaBaseline × StageMultiplier**

Contoh:
- Foundation Establishment Early = 200
- Foundation Establishment Middle = 220
- Foundation Establishment Peak = 240
- Core Formation Early = 300

### 3.3 Modifikasi Aktual
Nilai maksimum stamina aktual tidak hanya ditentukan oleh Realm. Setelah StageBaselineStamina ditetapkan, nilai dapat berbeda berdasarkan faktor yang benar-benar tercatat:
- latihan fisik yang terdokumentasi;
- kondisi dan kualitas tubuh;
- Body-Refining atau law resmi yang memberi efek stamina;
- cedera permanen atau kerusakan tubuh;
- efek item, buff, debuff, atau kondisi khusus yang sah.

**StaminaMaxAktual = StageBaselineStamina + ModifierResmi**

`ModifierResmi` hanya boleh berasal dari sumber yang tercatat/tervalidasi. GM tidak boleh memberikan bonus atau penalti stamina secara arbitrer.

Realm breakthrough meningkatkan baseline sesuai Realm baru, tetapi **tidak otomatis menghapus cedera, memberi bonus latihan, atau menciptakan modifier khusus**.

Jika tidak ada modifier yang sah, gunakan StageBaselineStamina sebagai StaminaMaxAktual.

Contoh karakter Foundation Establishment Early:
- Normal tanpa modifier = 200 stamina maksimum.
- Latihan fisik yang memberi modifier +20 = 220.
- Law resmi dengan modifier +30 = 230.
- Cedera permanen dengan modifier −20 = 180.

### 3.4 Pemulihan dan Biaya
Stamina tidak boleh dipulihkan secara gratis. Pemulihan membutuhkan waktu dan kondisi yang sesuai. Biaya aktivitas fisik harus ditentukan berdasarkan aktivitas, durasi, kondisi karakter, dan aturan sistem yang relevan.

Naik Realm tidak berarti stamina current otomatis kembali penuh. Setelah breakthrough, **StaminaMax** berubah mengikuti Realm/Stage baru, sedangkan **Current Stamina** tetap mengikuti hasil resolusi breakthrough dan kondisi pemulihan yang sah.

## 4. Satiety
Satiety dicatat sebagai persentase 0–100%. Makanan mengembalikan satiety sesuai item resmi. Kelaparan memengaruhi kondisi, stamina, fokus, dan pemulihan sesuai tabel/modifier resmi.

Baseline durasi tanpa makanan:
**JamSampaiKosong = 6 jam × FastingMultiplier(realm)**.
FastingMultiplier harus berasal dari tabel resmi; tidak boleh ditebak bila tabel belum tersedia.

## 5. Kondisi
Status seperti Normal, Terluka, Keracunan, Kutukan, Trauma, atau kondisi khusus memiliki sumber, durasi bila ada, efek, dan metode pemulihan.

## 6. Damage & Recovery
Damage mengurangi HP. Jika HP mencapai 0, karakter berada pada kondisi kritis/death sesuai Combat dan tidak menerima free heal. Pemulihan memerlukan waktu, treatment, teknik, item, atau kondisi resmi.

## 7. Integrasi
Vitality menjadi input Combat, Cultivation, Action, Time, Hunger, dan Character Save. Semua perubahan HP, Qi, Stamina, dan Satiety dicatat pada current state dan perubahan material harus memiliki sumber/log yang sah.
