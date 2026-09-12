# Runtime State Validator

## Tujuan
Memastikan state dan persistent memory yang akan diterapkan merupakan hasil transisi sah, bukan klaim, kebocoran antar-character/entity, atau retcon.

## Pre-Resolution Validation
- [ ] Waktu dunia valid dan tidak mundur.
- [ ] Lokasi karakter diketahui dan konsisten.
- [ ] Target berada pada lokasi/jarak yang masuk akal.
- [ ] Realm dan stage sesuai current state.
- [ ] Teknik benar-benar dimiliki dan dapat digunakan.
- [ ] Equipment dan inventory memiliki sumber.
- [ ] HP/Qi/Stamina/Satiety berada dalam batas sistem.
- [ ] Kondisi/status yang relevan diperhitungkan.
- [ ] Informasi yang digunakan memang diketahui karakter.
- [ ] Event/faction/NPC yang relevan dimuat.
- [ ] Durasi aksi memenuhi Time System.
- [ ] Character History yang dimuat cocok dengan Active Character ID.
- [ ] Shared story memory yang digunakan memang relevan.
- [ ] Jika Spirit Beast terlibat, BEAST_ID valid, unik, dan cocok dengan Beast Registry.
- [ ] Jika Spirit Beast terlibat, Current Beast State dan Beast History yang dimuat cocok dengan BEAST_ID.
- [ ] Jika Spirit Beast terlibat, relationship/taming/ownership/contract memiliki status dan origin yang dapat dibuktikan.
- [ ] Jika Spirit Beast terlibat, Tier dan Realm/Stage tidak dicampur dan masing-masing sesuai data spesies/sistem.
- [ ] Jika Spirit Beast terlibat, HP/Qi/Stamina/Satiety dan kondisi Beast berada dalam batas sistem.
- [ ] Jika Spirit Beast terlibat, lokasi Beast, habitat, lifecycle, missing/deceased status, abilities, dan techniques konsisten.
- [ ] Jika gardening relevan, `systems/23_GARDENING.md` dimuat.
- [ ] Jika gardening relevan, Garden/Crop ID, lokasi, jenis tanaman, jumlah, waktu tanam, tahap pertumbuhan, dan sumber benih diketahui atau ditandai `???`.
- [ ] Jika gardening relevan, seluruh status numerik berada pada rentang 0–100.

## Gardening Validation
- [ ] Tanaman biasa tidak memiliki waktu pertumbuhan standar di atas 10 hari in-game.
- [ ] Tanaman spiritual tidak memiliki waktu pertumbuhan standar di atas 60 hari in-game kecuali ada aturan Admin khusus yang terdokumentasi.
- [ ] `Disease` dan `Pest` menggunakan konvensi semakin tinggi semakin buruk.
- [ ] Status positif menggunakan konvensi semakin tinggi semakin baik.
- [ ] Angka status memiliki penyebab yang dapat ditelusuri dan bukan angka acak tanpa dasar.
- [ ] Batch status hanya digunakan untuk tanaman yang cukup homogen.
- [ ] Tanaman dengan kondisi material berbeda dipisahkan bila diperlukan.
- [ ] Panen tidak dilakukan sebelum waktu pertumbuhan dan Maturity sesuai.
- [ ] Percepatan pertumbuhan memiliki metode dan Origin yang valid.
- [ ] Passive growth hanya dihitung dari waktu dunia yang benar-benar berlalu.
- [ ] Tidak ada hidden time-skip untuk mematangkan tanaman.

## Post-Resolution Validation
- [ ] Waktu bertambah tepat.
- [ ] Semua cost diterapkan.
- [ ] Tidak ada resource negatif/di atas cap tanpa aturan resmi.
- [ ] Cedera/status negatif tidak hilang tanpa penyebab sah.
- [ ] Item/uang/teknik baru memiliki Origin Log.
- [ ] Perubahan realm/cultivation memiliki jalur perkembangan sah.
- [ ] Reputation/Karma/faction rank memiliki dasar interaksi/event.
- [ ] NPC reaction tidak memberi pengetahuan yang tidak mereka miliki.
- [ ] Event hanya berubah jika trigger terpenuhi.
- [ ] State baru dapat ditelusuri ke sumber.
- [ ] Character History update hanya memuat fakta yang benar-benar terjadi.
- [ ] Beast History update hanya memuat fakta Beast yang benar-benar terjadi.
- [ ] Character History tidak memuat data Character lain.
- [ ] Beast History tidak memuat data Beast lain.
- [ ] Active Threads memiliki origin dan status yang dapat ditelusuri.
- [ ] World State/Timeline hanya diperbarui untuk fakta shared/world-level yang terkonfirmasi.
- [ ] Jika relationship/taming/ownership/contract Beast berubah, perubahan memiliki causality dan Origin.
- [ ] Jika Beast growth/evolution terjadi, requirement, method, before → after, dan Origin valid.
- [ ] Jika Beast transfer/release terjadi, owner lama/baru dan mekanisme perubahan dapat ditelusuri.
- [ ] Missing Beast tidak diperlakukan sebagai deceased atau dipindahkan tanpa dasar.
- [ ] Deceased Beast tidak kembali aktif tanpa mekanisme resmi.
- [ ] Jika Character dan Beast berubah dalam transaksi yang sama, kedua state memiliki before → after dan cost yang konsisten.
- [ ] Jika gardening berubah, jumlah tanaman, status kebun/tanaman, hasil panen, waktu panen, dan Origin konsisten.
- [ ] Write-back status diketahui dan tidak dipalsukan.

## Invalid State
Jika satu pemeriksaan material gagal, jangan menerapkan state. Kembali ke nilai terakhir yang terverifikasi atau minta klarifikasi bila konteks aksi yang sah belum cukup. Jangan menulis memory yang bergantung pada state yang gagal.
