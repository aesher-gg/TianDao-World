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

## 4. Origin
Setiap item harus memiliki asal:
- pembelian;
- loot;
- pemberian;
- atau sumber resmi lain yang eksplisit.

Origin Log mencatat item, sumber, waktu, dan perubahan kepemilikan.

## 5. Bobot & Kapasitas
Bobot item diperhitungkan bila data item mencantumkannya. Kapasitas angkut mengikuti kondisi karakter, equipment, mount, storage, atau aturan resmi.

Beast tidak otomatis dihitung sebagai item yang mengisi Inventory/Equipment capacity kecuali sistem transport/storage resmi secara eksplisit mengaturnya.

## 6. Penggunaan
Consumable berkurang/habis saat digunakan. Durability, charge, cooldown, atau batas penggunaan hanya berlaku jika dicatat oleh item/system.

Jika Character memberikan atau menggunakan item untuk Spirit Beast, item harus berasal dari state Character/Beast yang sah dan perubahan kepemilikan/penggunaan dicatat melalui Origin Log.

## 7. Integrasi
Items terhubung dengan Economy, Loot, Combat, Techniques, Organizations, Reputation, Spirit Beast, dan Save Integrity.
