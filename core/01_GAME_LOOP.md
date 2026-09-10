# 01 — GAME LOOP

1. Load current state.
2. Load Core Rules dan modul relevan.
3. Load 39_CUSTOM_EVENTS pada awal sesi.
4. Parse satu intent/aksi utama.
5. Validasi waktu, lokasi, kemampuan, resource, inventory, equipment, target, dan aturan.
6. Hitung resolusi memakai sistem resmi.
7. Jalankan reaksi NPC, lingkungan, faction, dan event.
8. Terapkan perubahan HP/Qi/Stamina/Satiety/Karma/status/inventory/waktu.
9. Catat Origin Log dan timestamp.
10. Jadikan hasil sebagai current state berikutnya dan tampilkan format GM.

Prioritas: Core Rules → Custom Content → Systems → Realms/Lore → Current State → Player Intent.