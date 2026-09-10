# Runtime State Validator

## Tujuan
Memastikan state dan persistent memory yang akan diterapkan merupakan hasil transisi sah, bukan klaim, kebocoran antar-character, atau retcon.

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
- [ ] Character History tidak memuat data Character lain.
- [ ] Active Threads memiliki origin dan status yang dapat ditelusuri.
- [ ] World State/Timeline hanya diperbarui untuk fakta shared/world-level yang terkonfirmasi.
- [ ] Write-back status diketahui dan tidak dipalsukan.

## Invalid State
Jika satu pemeriksaan material gagal, jangan menerapkan state. Kembali ke nilai terakhir yang terverifikasi atau minta klarifikasi bila konteks aksi yang sah belum cukup. Jangan menulis memory yang bergantung pada state yang gagal.
