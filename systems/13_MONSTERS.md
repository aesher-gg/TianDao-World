# 13 — MONSTERS

## 1. Encounter
Monster dan Spirit Beast hanya berasal dari data wilayah atau database makhluk resmi/kustom. GM tidak menciptakan spesies, tier, kemampuan, atau drop baru tanpa sumber.

Spirit Beast adalah subset khusus makhluk yang dapat memiliki persistent identity dan lifecycle melalui `systems/24_SPIRIT_BEASTS.md`. Tidak setiap monster otomatis merupakan Spirit Beast.

## 2. Data Encounter
Encounter dapat memuat:
- identitas/species;
- tier dan realm;
- lokasi/habitat;
- perilaku;
- agresivitas;
- kemampuan;
- kelemahan jika diketahui karakter;
- loot table resmi.

Jika encounter melibatkan Spirit Beast yang telah memiliki BEAST_ID, runtime wajib menggunakan Current Beast State/Beast History yang sesuai dan tidak membuat entity baru dengan identitas berbeda.

## 3. AI Makhluk
Monster bertindak berdasarkan naluri, habitat, kondisi, dan data perilaku. Spirit Beast juga mempertahankan otonomi sesuai intelligence, temperament, relationship, taming, ownership, contract, condition, dan aturan Module 24. Mereka tidak otomatis menyerang, jinak, setia, memiliki, atau kalah.

## 4. Tier vs Realm
Tier makhluk dan realm adalah atribut terpisah kecuali modul resmi menyatakan hubungan. Jangan mengubah tier menjadi realm secara otomatis. Spirit Beast mengikuti aturan yang sama; realm/stage hanya berlaku bila didukung spesies/data/sistem.

## 5. Loot
Loot hanya dihasilkan setelah encounter/combat yang sah dan mengikuti Loot Table. Item tidak otomatis jatuh hanya karena player mengalahkan makhluk. Spirit Beast yang dimiliki/berkontrak tidak diperlakukan sebagai loot/item.

## 6. Integrasi
Monster memakai Combat, Vitality, Items, Loot, Geography, Time, dan Reputation/Karma jika perilaku atau konsekuensinya melibatkan pihak lain. Spirit Beast memakai modul-modul tersebut bila relevan dan menggunakan `systems/24_SPIRIT_BEASTS.md` untuk relationship, taming, ownership, contract, growth/evolution, lifecycle, state, history, dan save integration.
