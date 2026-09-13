# 18 — LOOT

## 1. Sumber
Loot berasal dari:
- monster/spirit beast;
- peti atau lokasi;
- musuh;
- event;
- reward misi;
- sumber resmi lainnya.

## 2. Validasi
Loot hanya diberikan setelah kondisi perolehan terpenuhi. GM tidak menjamin item langka.

## 3. Loot Table
Loot table resmi adalah satu-satunya sumber untuk drop yang memiliki daftar, peluang, rarity, quantity, atau hasil numerik tertentu.

Database runtime resmi: `loot/00_LOOT_TABLE_DATABASE.md`.

Jika loot table resmi tersedia, gunakan table tersebut secara tepat. Jika tidak ada table aktif untuk sumber loot tersebut, GM **tidak boleh membuat drop spesifik** dan dapat menyatakan bahwa hasil belum dapat ditentukan dari World Bible.

## 4. Larangan Fallback Loot
Jika data loot tidak lengkap, GM dilarang membuat atau mengasumsikan:
- persentase drop;
- rarity/chance;
- jumlah item;
- kualitas item;
- nilai ekonomi/harga jual;
- currency drop;
- material tubuh/monster drop;
- tabel pengganti berdasarkan Tier, Realm, lokasi, habitat, atau genre;
- modifier atau multiplier loot;
- "drop standar", "drop minimum", atau hadiah otomatis.

**Tier, Realm, habitat, atau tingkat kesulitan encounter tidak secara otomatis menghasilkan loot tertentu.** Semua hubungan mekanis tersebut harus ditetapkan oleh sumber Canon/Admin yang sah.

## 5. Perolehan Tanpa Loot Table
Ketiadaan loot table bukan izin untuk mengarang. Bila aksi secara naratif menghasilkan akses terhadap benda/material tetapi belum ada data loot yang memvalidasi identitas, jumlah, kualitas, atau nilai benda tersebut, GM harus menahan detail mekanis yang tidak diketahui dan menggunakan `???`/hasil belum ditentukan sesuai konteks.

## 6. Kepemilikan
Loot yang berhasil diperoleh langsung menjadi bagian dari Item Origin Log dengan sumber dan timestamp. Item tidak masuk Inventory sebelum perolehan dan kepemilikannya tervalidasi.

## 7. Distribusi
Jika beberapa pihak berhak atas loot, pembagian mengikuti kepemilikan, kesepakatan, hukum faction, atau hasil konflik yang sah. GM tidak boleh menetapkan pembagian numerik tanpa dasar yang sah.

## 8. Origin & Anti-Duplikasi
Setiap loot yang benar-benar diperoleh harus dapat ditelusuri ke sumber, kondisi perolehan, waktu, dan perubahan kepemilikan melalui Item Origin Log.

Item unik/terbatas tidak dapat diduplikasi melalui klaim player, reload state, atau retcon.

## 9. Integrasi
Loot terhubung dengan Combat, Monsters, Events, Items, Economy, Organizations, Karma, Reputation, dan Save Integrity.

## 10. Prinsip Runtime
Prioritas resolusi loot:
`Loot Table/Canon Spesifik → Event/Mission Reward Resmi → Item/Source Origin Resmi → hasil belum ditentukan (???).`

Tidak ada fallback numerik tersembunyi. Bila sumber resmi tidak menyediakan angka, GM tidak boleh menciptakan angka agar resolusi terlihat lengkap.

## 11. Status Canon Saat Ini

`loot/00_LOOT_TABLE_DATABASE.md` adalah registry Admin Canon untuk loot table. Pada saat ini belum ada loot table aktif. Table baru harus dibuat dan diaktifkan oleh Admin setelah Source ID dan Item/Reward ID yang diperlukan tersedia dan tervalidasi.
