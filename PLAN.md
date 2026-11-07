# PLAN.md — Futuristic 3D Arcade Game Roadmap (Untuk Siswa)

Dokumen ini adalah rencana kerja dan log perkembangan proyek game arcade 3D dalam 1 file `index.html`. Dokumen ini diperbarui setiap kali ada perubahan kode sebelum push ke GitHub.

---

## 1. Ikhtisar Game

- **Judul Game**: Mario Neon 3D
- **Genre**: 3D Arcade Platformer (kamera 2.5D, geometri WebGL penuh)
- **Format**: Single-File HTML (`index.html`) tanpa dependensi eksternal
- **Renderer**: Raw WebGL 1.0 — tanpa Three.js, tanpa library, tanpa file aset
- **Karakter**: Plumber low-poly bergaya Mario (topi merah + emblem M, kumis, overall biru, sarung tangan putih) yang dibangun 100% dari primitif 3D prosedural, dengan **postur menghadap samping (profil)** dan aksesori **bendera kecil di atas topi**
- **Tema Latar**: 4 sektor futuristik — Neon City, Holo Garden, Solar District, Cryo Core
- **Portal & Flag**: Bendera kemenangan besar di atas portal + animasi karakter tersedot ke dimensi lain (kamera zoom, vortex CSS, putaran, pengecilan, dan tembus bidang portal) sebelum layar level clear muncul
- **Isi Dunia 3D**: Skyline neon prosedural, gedung berjendela holografik, mobil terbang, planet bercincin, kabut kedalaman, grid lantai, portal energi, koin torus, drone musuh, bayangan, partikel, dan glow additive
- **Audio**: Web Audio API sintetis
- **Penyimpanan**: LocalStorage (`arcade_leaderboard`, `arcade_last_username`)
- **Kebijakan Caching**: Zero-Cache (`no-cache, no-store, must-revalidate`)
- **Deployment**: GitHub Pages (Branch `master`, path `/`)
- **Catatan IP**: Fan-made tribute. Seluruh model, tekstur, dan efek dibuat prosedural; tidak memakai aset resmi Nintendo.

---

## 2. Fase Pengembangan Universal

### Phase 0: Brainstorming & Desain Game
- [x] Menentukan ide & tema: platformer 3D futuristik dengan karakter plumber bergaya Mario.
- [x] Menentukan kontrol: keyboard (Arrow/WASD/Shift/Space/P) + tombol sentuh.
- [x] Menentukan aturan menang/kalah: kumpulkan koin, injak drone, hindari pit/monster, capai portal.
- [x] Menentukan gaya visual: low-poly 3D neon cyberpunk dengan bloom additive dan 4 palet tema.

### Phase 1: Setup Single-File `index.html`
- [x] Kerangka HTML5 dengan meta tag Zero-Cache.
- [x] Kanvas WebGL responsif dengan aspect ratio 4:3.
- [x] Struktur kode modular 8 blok.
- [x] Game loop `requestAnimationFrame` dengan fixed timestep fisika 60 Hz.
- [x] Adaptive resolution untuk perangkat dengan FPS rendah.

### Phase 2: Username & Leaderboard LocalStorage
- [x] Input username dengan validasi 1–15 karakter dan sanitasi anti-XSS.
- [x] Menyimpan username terakhir di `arcade_last_username`.
- [x] Menyimpan Top 10 skor di `arcade_leaderboard`.
- [x] UI tabel leaderboard yang bisa diakses dari menu.

### Phase 3: Mekanik Inti Permainan
- [x] State `MENU`, `PLAYING`, `PAUSED`, `LEVELCLEAR`, `GAMEOVER`, `LEADERBOARD`.
- [x] Pergerakan pemain, akselerasi, gesekan, coyote time, jump buffer.
- [x] Boost dengan meter energi, lompat variabel, tunduk/fast-fall.
- [x] Rintangan, pit, platform, koin, drone patroli.
- [x] AABB collision dan kamera follow.
- [x] 4 level dengan layout berbeda dan transisi level.

### Phase 4: Render 3D, Efek Suara & Visual Juice
- [x] WebGL shader untuk objek solid, neon additive, glow billboard, dan sky prosedural.
- [x] Karakter 3D beranimasi: lari, lompat, tunduk, boost, landing squash, dan death spin.
- [x] Postur karakter menghadap samping kiri/kanan, dengan mata profil, badge topi samping, dan bendera kecil di atas topi.
- [x] Dunia 3D prosedural: gedung, jendela, mobil terbang, planet, koin, portal, drone, bayangan.
- [x] Bendera kemenangan besar di atas portal dan area final yang bersih dari platform.
- [x] Animasi masuk portal: karakter ditarik ke pusat ring, berputar, mengecil, tembus bidang portal, kamera zoom, vortex overlay, dan suara dimensi.
- [x] Efek suara arcade sintetis (jump, koin, stomp, boost, hit, game over, level clear, portal).
- [x] Partikel, floating score popup, screen shake, flash, dan level banner.
- [x] Pemilih tema latar (Background Mode) di menu untuk preview 4 sektor.

### Phase 5: Publikasi GitHub Pages
- [x] Repository GitHub publik `aoelairlines/mario-bross`.
- [x] GitHub Pages aktif dari branch `master` root `/`.
- [x] Zero-Cache terpasang agar update langsung terlihat.
- [x] Verifikasi live demo: `https://aoelairlines.github.io/mario-bross/`.

---

## 3. Matriks Tugas & Status Pelaksanaan

| ID | Tugas / Fitur | Fase | Status | Pelaksana | Catatan |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **T-00** | Template `AGENTS.md` & `PLAN.md` | Fondasi | `DONE` | AI | Template standar siswa |
| **T-01** | Konsep game 3D futuristik | Phase 0 | `DONE` | AI + Siswa | Mario-inspired 3D platformer |
| **T-02** | Skeleton `index.html` + Zero-Cache | Phase 1 | `DONE` | AI | Single-file, tanpa dependensi |
| **T-03** | Username & leaderboard Top 10 | Phase 2 | `DONE` | AI | LocalStorage, sanitasi, tabel |
| **T-04** | Fisika platformer & tabrakan | Phase 3 | `DONE` | AI | AABB, coyote time, jump buffer |
| **T-05** | Audio synth & partikel | Phase 4 | `DONE` | AI | Web Audio API, efek arcade |
| **T-06** | Deploy GitHub Pages | Phase 5 | `DONE` | AI | `https://aoelairlines.github.io/mario-bross/` |
| **T-07** | Boost, variabel jump, tunduk, tombol sentuh | Phase 3 | `DONE` | AI | Shift/B + D-pad + A/B |
| **T-08** | 4 level dengan tema futuristik | Phase 3 | `DONE` | AI | Neon City, Holo Garden, Solar District, Cryo Core |
| **T-09** | Pause, level clear, victory, leaderboard | Phase 4 | `DONE` | AI | Alur layar lengkap |
| **T-10** | Renderer WebGL 3D + karakter 3D | Phase 4 | `DONE` | AI | Prosedural, low-poly, beranimasi |
| **T-11** | Background mode 4 tema + preview menu | Phase 4 | `DONE` | AI | Tombol tema langsung mengganti scene |
| **T-12** | UI futuristik + responsif + adaptive resolution | Phase 4 | `DONE` | AI | Desktop, tablet, ponsel |
| **T-13** | Pengujian Chrome & regresi gameplay | Phase 5 | `DONE` | AI | Koin, stomp, level clear, victory, pause, localStorage, mobile |
| **T-14** | Profil samping, bendera topi, bendera portal, animasi suction | Phase 4 | `DONE` | AI | Karakter menghadap kiri/kanan; bendera di topi dan di atas portal; transisi dimensi + kamera zoom |

*Status: `TODO` | `IN-PROGRESS` | `DONE`*

---

## 4. Changelog & Riwayat Revisi

| Versi | Tanggal | Pelaksana | Ringkasan Perubahan | Referensi Commit |
| :--- | :--- | :--- | :--- | :--- |
| **v0.6.0** | 2026-11-07 | AI | Karakter diubah ke **postur profil samping** kiri/kanan dengan mata samping dan badge topi samping; aksesori **bendera kecil di atas topi**; **bendera kemenangan besar** di atas portal; **animasi tersedot portal**: kamera zoom, vortex CSS, karakter berputar-mengecil-tembus bidang portal, partikel pusaran, dan SFX dimensi; area final diperpanjang agar bendera/portal tidak tertutup platform; pengujian desktop, mobile, level clear, final victory, pause, dan retry | `-` |
| **v0.5.0** | 2026-11-07 | AI | Transformasi total ke **Mario Neon 3D**: renderer WebGL 3D prosedural tanpa library, karakter plumber low-poly beranimasi, 4 background futuristik (Neon City, Holo Garden, Solar District, Cryo Core), skyline gedung neon, planet bercincin, mobil terbang, portal energi, koin torus, drone, bayangan, fog, bloom additive, UI cyberpunk baru, preview tema di menu, mobile layout, adaptive resolution, dan pengujian lengkap | `30e897f` |
| **v0.4.2** | 2026-10-31 | AI | Efek suara baru: koin bernada cerah khas arcade, impact saat menabrak monster, dan jingle kekalahan | `-` |
| **v0.4.1** | 2026-10-31 | AI | Perbaikan hasil review: clamp kecepatan jalan vs BOOST, koin tidak tertanam di platform, hint tombol diperjelas, reset menu memakai `startLevel` | `-` |
| **v0.4.0** | 2026-10-31 | AI | Fitur BOOST, lompat variabel, tunduk, tombol on-screen, 4 level dengan tema prosedural, overlay pause/level clear/victory | `-` |
| **v0.3.0** | 2026-10-24 | AI | Rilis game lengkap Pixel Coin Adventure: platformer 2D Mario-like, 8 blok modular, leaderboard LocalStorage | `-` |
| **v0.2.2** | 2026-10-24 | AI | Panduan integrasi Google AI Studio & penegasan repo wajib Public | `07475fb` |
| **v0.2.1** | 2026-10-24 | AI | Panduan aktivasi GitHub Pages (CLI & Web UI) | `3aaf671` |
| **v0.2.0** | 2026-10-24 | AI | Single Model AI untuk siswa, modularisasi 8 blok | `2954bb0` |
| **v0.1.0** | 2026-10-24 | AI | Inisialisasi `AGENTS.md` dan `PLAN.md` | `47aa88e` |

---

## 5. Catatan Teknis

- **Tanpa dependensi**: tidak ada CDN, library, file gambar, atau model eksternal. Semua geometri dibuat dengan `SolidBuilder`/`NeonBuilder`, semua tekstur efek dibuat lewat shader.
- **Struktur 8 blok**: config/WebGL, audio, input, state/entity, collision/physics, LocalStorage, rendering/UI, game loop.
- **Kualitas adaptif**: device pixel ratio dibatasi 1.5; bila FPS terukur < 30, resolusi render diturunkan otomatis ke 72% tanpa mengubah layout.
- **Kontrol**: `← →`/`A D` gerak, `Shift`/`B` boost, `↑`/`Space` lompat, `↓` tunduk, `P`/`Esc` pause.
- **Portal entry**: saat menyentuh goal, fisika normal dihentikan sementara, kamera fokus ke portal, karakter dianimasikan masuk, lalu level clear/victory dipicu setelah ±1,27 detik. Pause dinonaktifkan selama transisi.
- **Runway final**: lebar tiap level ditambah 160 px agar portal dan bendera kemenangan berada di area kosong, tidak bertabrakan dengan platform terakhir.
- **Zero-Cache**: setiap update yang di-push langsung aktif setelah deploy GitHub Pages selesai.
