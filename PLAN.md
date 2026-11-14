# PLAN.md — Classic 2D Pixel Platformer Roadmap (Untuk Siswa)

Dokumen ini adalah rencana kerja dan log perkembangan proyek game arcade 2D dalam 1 file `index.html`. Dokumen diperbarui setiap kali ada perubahan kode sebelum push ke GitHub.

---

## 1. Ikhtisar Game

- **Judul Game**: Mario 2D Adventure
- **Genre**: 2D Classic Pixel Platformer (side-scrolling, gaya 8-bit)
- **Format**: Single-File HTML (`index.html`) tanpa dependensi eksternal
- **Renderer**: Canvas 2D murni, resolusi internal **320 × 240** (4:3), di-upscale dengan `image-rendering: pixelated`
- **Karakter**: Plumber pixel-art detail 18 × 24 (small) / 24 × 32 (big), menghadap samping kiri/kanan; topi merah dengan emblem **M putih**, kumis dan rambut cokelat, mata dengan kilau, sarung tangan putih, overall biru dengan dua kancing kuning, serta sepatu cokelat ber-outline hitam tebal
- **Dunia**: 4 world bertema klasik 2D — **Overworld, Underground, Sunset, Snowy Peaks**
- **Elemen Visual**: langit biru, awan pixel, bukit dan semak hijau, tanah bata, pipa hijau, blok bata, blok tanya, koin berputar, mushroom, bintang, tiang bendera, dan kastil
- **Item & Skor**:
  - Koin: +100 poin dan menambah penghitung koin
  - Blok tanya: mengeluarkan koin, mushroom, atau bintang
  - Mushroom: +100 poin dan membuat karakter menjadi besar
  - Bintang: +1000 poin, booster kecepatan, dan kebal (invincible) selama 10 detik
  - Menginjak Goomba: +200 poin
- **Goal**: mencapai tiang bendera di ujung world; bendera turun dan skor bonus waktu ditambahkan
- **Nyawa & Waktu**: 3 nyawa, timer 300 detik per world, HUD klasik (SCORE / COINS / WORLD / TIME / LIVES)
- **Audio**: Web Audio API sintetis — jump, koin, blok, power-up, bintang, stomp, hurt, death, flag, game over
- **Penyimpanan**: LocalStorage (`arcade_leaderboard`, `arcade_last_username`)
- **Kebijakan Caching**: Zero-Cache (`no-cache, no-store, must-revalidate`)
- **Deployment**: GitHub Pages (Branch `master`, path `/`)
- **Catatan IP**: Fan-made tribute. Seluruh sprite, tile, dan efek digambar prosedural; tidak memakai aset resmi Nintendo.

---

## 2. Fase Pengembangan

### Phase 0: Brainstorming & Desain 2D
- [x] Mengubah arah visual dari 3D futuristik menjadi **2D pixel-art klasik** seperti referensi Super Mario Bros.
- [x] Menentukan palet 4 world: Overworld, Underground, Sunset, Snowy Peaks.
- [x] Menentukan elemen wajib: koin, pipa hijau, blok tanya, mushroom +100, bintang booster, dan tiang bendera.
- [x] Menentukan kontrol: keyboard (Arrow/WASD/Shift/Space/P) + tombol sentuh.

### Phase 1: Setup Single-File `index.html`
- [x] Kerangka HTML5 dengan meta tag Zero-Cache.
- [x] Canvas 2D 320 × 240 responsif dengan aspect ratio 4:3.
- [x] Struktur kode modular (config, themes, audio, input, state, physics, rendering, UI, loop).
- [x] Game loop `requestAnimationFrame` dengan fixed timestep fisika 60 Hz.
- [x] `imageSmoothingEnabled = false` agar pixel-art tetap tajam.

### Phase 2: Username & Leaderboard LocalStorage
- [x] Input username 1–15 karakter + sanitasi anti-XSS.
- [x] Menyimpan username terakhir di `arcade_last_username`.
- [x] Menyimpan Top 10 skor di `arcade_leaderboard`.
- [x] Tabel leaderboard klasik yang dapat diakses dari menu.
- [x] Tombol “Ganti Nama” setelah username tersimpan.

### Phase 3: Mekanik Inti Platformer
- [x] State `MENU`, `INTRO`, `PLAYING`, `PAUSED`, `DYING`, `FLAG`, `LEVELCLEAR`, `GAMEOVER`, `LEADERBOARD`.
- [x] Akselerasi, gesekan, coyote time, jump buffer, lompat variabel, dan fast-fall.
- [x] AABB collision untuk tanah, blok, pipa, tangga, dan platform.
- [x] Kamera follow horizontal dengan parallax background.
- [x] Nyawa, timer, level intro, respawn, game over, dan victory.
- [x] 4 world dengan layout handcrafted (1-1) dan generator deterministik (1-2 s.d. 1-4).

### Phase 4: Konten Khas Mario 2D
- [x] **Koin** 8-bit berputar dengan animasi lebar, +100 poin dan penghitung koin.
- [x] **Pipa hijau** solid dengan bibir pipa, highlight, dan bayangan.
- [x] **Blok bata** dan **blok tanya** yang bisa dipukul dari bawah.
- [x] **Mushroom** keluar dari blok, berjalan, +100 poin, dan membuat pemain besar.
- [x] **Bintang** keluar dari blok, memantul, +1000 poin, dan memberikan **Star Power** (kebal + kecepatan) selama 10 detik.
- [x] **Goomba** berpatroli, bisa diinjak (+200), dan menyakiti pemain.
- [x] **Tiang bendera** merah dengan huruf M, animasi bendera turun, kastil di belakangnya.
- [x] **Redesign karakter Mario**: sprite pixel-art lebih besar dan detail seperti referensi — emblem M pada topi, sarung tangan putih, kumis tebal, rambut, shading, kancing overall kuning, dan animasi idle/run/jump/climb.
- [x] Hitbox karakter disesuaikan (small 14 × 24, big 16 × 32) agar kepala tidak menembus blok saat melompat.
- [x] Efek suara arcade, partikel, floating score, dan HUD pixel.

### Phase 5: UI, Responsif & Publikasi
- [x] Menu klasik dengan panel krem, border hitam tebal, aksen merah/kuning/biru.
- [x] Overlay pause, leaderboard, level clear, game over, dan victory.
- [x] Tombol D-pad + A/B di perangkat sentuh.
- [x] Layout responsif desktop, tablet, dan ponsel.
- [x] Repository GitHub publik `aoelairlines/mario-bross`.
- [x] GitHub Pages aktif dari branch `master` root `/`.
- [x] Verifikasi live demo: `https://aoelairlines.github.io/mario-bross/`.

---

## 3. Matriks Tugas & Status Pelaksanaan

| ID | Tugas / Fitur | Fase | Status | Pelaksana | Catatan |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **T-00** | Template `AGENTS.md` & `PLAN.md` | Fondasi | `DONE` | AI | Template standar siswa |
| **T-01** | Konsep 2D classic pixel platformer | Phase 0 | `DONE` | AI + Siswa | Referensi World 1-1 |
| **T-02** | Skeleton `index.html` + Zero-Cache | Phase 1 | `DONE` | AI | Single-file, tanpa dependensi |
| **T-03** | Username & leaderboard Top 10 | Phase 2 | `DONE` | AI | LocalStorage, sanitasi, tabel |
| **T-04** | Fisika platformer & tabrakan | Phase 3 | `DONE` | AI | AABB, coyote time, jump buffer |
| **T-05** | Audio synth & partikel | Phase 4 | `DONE` | AI | Web Audio API, efek arcade |
| **T-06** | Deploy GitHub Pages | Phase 5 | `DONE` | AI | `https://aoelairlines.github.io/mario-bross/` |
| **T-07** | Nyawa, timer, intro, respawn, victory | Phase 3 | `DONE` | AI | Alur klasik lengkap |
| **T-08** | 4 world 2D dengan tema berbeda | Phase 3 | `DONE` | AI | Overworld, Underground, Sunset, Snowy Peaks |
| **T-09** | Koin, pipa hijau, blok bata/tanya | Phase 4 | `DONE` | AI | Desain dan collision |
| **T-10** | Mushroom +100 & transformasi besar | Phase 4 | `DONE` | AI | Muncul dari blok tanya |
| **T-11** | Bintang & Star Power booster | Phase 4 | `DONE` | AI | Kebal, lebih cepat, +1000 |
| **T-12** | Tiang bendera, kastil, level clear | Phase 4 | `DONE` | AI | Animasi bendera turun |
| **T-13** | HUD pixel, sprite, background 2D | Phase 4 | `DONE` | AI | Semua digambar via Canvas 2D |
| **T-14** | Menu, pause, game over, leaderboard | Phase 5 | `DONE` | AI | UI retro responsif |
| **T-15** | Tombol sentuh + keyboard | Phase 5 | `DONE` | AI | D-pad, A/B, Shift, Space, P |
| **T-16** | Pengujian Chrome desktop/mobile | Phase 5 | `DONE` | AI | Level 1–4, item, death, flag, victory, leaderboard, touch |
| **T-17** | Redesign sprite Mario detail + hitbox baru | Phase 4 | `DONE` | AI | Emblem M, sarung tangan putih, overall detail, animasi; hitbox 14×24 / 16×32 agar tidak clipping |

*Status: `TODO` | `IN-PROGRESS` | `DONE`*

---

## 4. Changelog & Riwayat Revisi

| Versi | Tanggal | Pelaksana | Ringkasan Perubahan | Referensi Commit |
| :--- | :--- | :--- | :--- | :--- |
| **v0.8.1** | 2026-11-14 | AI | **Upgrade kualitas sprite Mario**: karakter digambar ulang lebih detail (emblem M pada topi, sarung tangan putih, kumis/rambut, mata berkilau, shading overall biru, dua kancing kuning, sepatu cokelat, outline hitam tebal), ukuran visual small 18×24 / big 24×32, animasi idle/run/jump/climb, dan hitbox baru 14×24 / 16×32 agar tidak ada clipping kepala saat memukul blok | `-` |
| **v0.8.0** | 2026-11-14 | AI | **Redesign total ke 2D classic pixel-art**: renderer Canvas 2D 320×240, langit biru, awan, bukit/semak, tanah bata, blok bata & blok tanya, koin berputar, **pipa hijau**, **mushroom +100 & menjadi besar**, **bintang booster/kebal**, Goomba, tiang bendera, kastil, HUD SCORE/COINS/WORLD/TIME/LIVES, 3 nyawa, timer 300 detik, 4 world bertema, menu/overlay retro, kontrol sentuh, serta leaderboard tetap dipertahankan | `642c41d` |
| **v0.7.0** | 2026-11-14 | AI | **Mario 3D Adventure**: perbaikan wajah profil satu sisi; tema non-futuristik Sunny Plaza, Candy Clouds, Golden Autumn, Snowy Town; bendera topi/portal, animasi suction | `b659b39` |
| **v0.6.0** | 2026-11-07 | AI | Karakter profil samping, bendera topi, bendera portal, animasi tersedot portal | `1830137` |
| **v0.5.0** | 2026-11-07 | AI | Transformasi 3D WebGL prosedural dengan 4 background futuristik | `30e897f` |
| **v0.4.2** | 2026-10-31 | AI | Efek suara koin, impact monster, dan jingle kekalahan | `-` |
| **v0.4.1** | 2026-10-31 | AI | Perbaikan clamp kecepatan, koin, hint tombol, reset menu | `-` |
| **v0.4.0** | 2026-10-31 | AI | Fitur BOOST, variabel jump, tunduk, tombol on-screen, 4 level, overlay | `-` |
| **v0.3.0** | 2026-10-24 | AI | Rilis game lengkap Pixel Coin Adventure 2D + leaderboard | `-` |
| **v0.2.2** | 2026-10-24 | AI | Panduan Google AI Studio & repo wajib Public | `07475fb` |
| **v0.2.1** | 2026-10-24 | AI | Panduan aktivasi GitHub Pages | `3aaf671` |
| **v0.2.0** | 2026-10-24 | AI | Single Model AI untuk siswa, modularisasi 8 blok | `2954bb0` |
| **v0.1.0** | 2026-10-24 | AI | Inisialisasi `AGENTS.md` dan `PLAN.md` | `47aa88e` |

---

## 5. Catatan Teknis

- **Tanpa dependensi**: tidak ada CDN, library, font eksternal, atau file gambar. Seluruh sprite, tile, blok, pipa, koin, mushroom, bintang, bendera, kastil, dan background digambar dengan `CanvasRenderingContext2D`.
- **Resolusi internal**: 320 × 240 (4:3), HUD 28 px di bagian atas, permukaan tanah pada `y = 208`, tile 16 px.
- **Struktur kode**: config/canvas → themes & level data → audio → input → state/level building → physics/flow → rendering → UI → main loop.
- **Fisika**: fixed timestep 60 Hz, AABB collision, coyote time, jump buffer, variable jump, dan fast-fall.
- **Hitbox karakter**: small 14 × 24 px, big 16 × 32 px. Sprite visual small 18 × 24 dan big 24 × 32; tinggi hitbox dibuat sama dengan tinggi visual agar ujung topi tidak menembus blok saat melompat.
- **Sprite Mario**: digambar prosedural per piksel pada grid 24 × 32 (big), dengan palet outline, merah, kulit, rambut, biru, putih, kuning, dan cokelat. Small Mario dirender dari sprite yang sama lalu diperkecil nearest-neighbor menjadi 18 × 24 agar detail dan proporsi tetap konsisten.
- **Koin**: `+100` poin, animasi berputar; koin dari blok tanya muncul sebagai animasi pop.
- **Mushroom**: keluar dari blok tanya, berjalan, memberi `+100` poin dan mengubah pemain menjadi big (tinggi 28 px).
- **Bintang**: `+1000` poin; `starTimer = 600` frame (±10 detik) dengan kecepatan naik, kebal, dan efek pelangi.
- **Pipa hijau**: solid, tinggi 2–4 tile, dapat dipijak/dilompati.
- **Tiang bendera**: goal di akhir world; saat disentuh pemain meluncur ke bawah, bendera turun, lalu level clear/victory.
- **Nyawa**: 3; jatuh ke pit, tersentuh musuh saat kecil, atau waktu habis mengurangi nyawa. Nyawa 0 → Game Over.
- **HUD**: SCORE, COINS, WORLD, TIME, LIVES, indikator STAR saat aktif.
- **Kontrol**: `← →`/`A D` gerak, `Shift`/`B` lari, `↑`/`Space` lompat, `↓` tunduk/fast-fall, `P`/`Esc` pause, `Enter` mulai.
- **Touch**: D-pad kiri/bawah/kanan + tombol A (lompat) dan B (lari), muncul otomatis di perangkat sentuh/layar sempit.
- **Zero-Cache**: setiap update yang di-push langsung aktif setelah deploy GitHub Pages selesai.
- **Fan-made**: bukan produk resmi Nintendo; seluruh visual dibuat ulang secara prosedural.
