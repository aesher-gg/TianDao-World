# 14 — ITEMS

## 1. Kategori
Item dapat berupa consumable, material, weapon, armor/protection, accessory, artifact, currency, quest item, atau kategori resmi lain.

Spirit Beast bukan Item dan tidak boleh dimasukkan ke kategori Item hanya karena dimiliki, dibawa, dipanggil, atau memiliki contract.

## 2. Equipment
Equipment adalah item yang sedang aktif dipakai/digenggam dan dapat memengaruhi combat hanya jika efeknya tercatat.

Spirit Beast tidak menjadi Equipment. Jika Beast memiliki perlengkapan sendiri, perlengkapan tersebut tetap merupakan item yang memiliki origin dan tercatat pada Beast sesuai aturan Module 24, tanpa mengubah identitas Beast menjadi item.

## 3. Inventory
Inventory adalah barang yang dibawa tetapi tidak sedang dipakai. Item tetap membutuhkan sumber kepemilikan.

BEAST_ID tidak boleh disimpan sebagai Inventory Item ID. Beast State berada di `characters/beasts/<BEAST_ID>.md`.

## 4. Canon Item Identity
Item Canon yang dapat digunakan oleh fixed loot, recipe, quest reward, atau event reward menggunakan ID stabil berikut. ID ini adalah identity/content reference; kepemilikan individual tetap dicatat melalui Origin Log.

| Item ID | Nama | Kategori | Baseline fungsi |
|---|---|---|---|
| ITEM-MAT-001 | Bijih Besi Kasar | Material | bahan logam umum |
| ITEM-MAT-002 | Kayu Keras Cangyuan | Material | bahan konstruksi umum |
| ITEM-MAT-003 | Kulit Binatang Biasa | Material | bahan kulit umum |
| ITEM-MAT-004 | Taring Binatang Biasa | Material | komponen material umum |
| ITEM-HERB-001 | Rumput Embun Pagi | Herb | bahan herbal dasar |
| ITEM-HERB-002 | Rumput Jarum Beracun | Herb | bahan herbal beracun |
| ITEM-CONS-001 | Bubuk Penghenti Darah | Consumable | menghentikan perdarahan ringan sesuai prosedur medis |
| ITEM-CONS-002 | Pil Penetral Racun Dasar | Consumable | penanganan racun dasar; tidak universal |
| ITEM-WPN-001 | Pisau Belati Besi Tempa | Weapon | belati besi sederhana |
| ITEM-WPN-002 | Pedang Besi Standar | Weapon | pedang besi sederhana |
| ITEM-MAT-005 | Serat Rami | Material | bahan tali/kerajinan |
| ITEM-MAT-006 | Batu Api | Material/Tool | sumber api sederhana |

### Aturan Identity
- Item ID tidak berubah ketika item berpindah tangan.
- Dua item dengan Item ID sama tetap dapat menjadi dua instance fisik berbeda.
- Instance individual wajib memiliki Origin dan riwayat kepemilikan bila perubahan material.
- Nama item tidak otomatis menentukan kualitas, durability, effect, atau rarity di luar data Canon item.
- Item yang belum mempunyai Item ID Canon tidak boleh dimasukkan ke fixed loot table sebagai item spesifik.

## 5. Origin
Setiap item harus memiliki asal:
- pembelian;
- loot;
- pemberian;
- crafting/forging;
- alchemy;
- atau sumber resmi lain yang eksplisit.

Origin Log mencatat item, sumber, waktu, dan perubahan kepemilikan.

## 6. Bobot & Kapasitas
Bobot item diperhitungkan bila data item mencantumkannya. Kapasitas angkut mengikuti kondisi karakter, equipment, mount, storage, atau aturan resmi.

Beast tidak otomatis dihitung sebagai item yang mengisi Inventory/Equipment capacity kecuali sistem transport/storage resmi secara eksplisit mengaturnya.

## 7. Penggunaan
Consumable berkurang/habis saat digunakan. Durability, charge, cooldown, atau batas penggunaan hanya berlaku jika dicatat oleh item/system.

Jika Character memberikan atau menggunakan item untuk Spirit Beast, item harus berasal dari state Character/Beast yang sah dan perubahan kepemilikan/penggunaan dicatat melalui Origin Log.

## 8. Integrasi
Items terhubung dengan Economy, Loot, Combat, Techniques, Organizations, Reputation, Spirit Beast, Crafting, Alchemy, Formation, Refinement, dan Save Integrity.
