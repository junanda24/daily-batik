# Design — BATIK! Studio Motif Batik Nusantara

## Direction contract (code-led; self-approved per program)

- **THESIS:** Satu halaman ini membuktikan batik itu bukan kain museum — ia
  sistem visual yang bisa diutak-atik. Pengunjung langsung memegang motifnya:
  melihat, mewarnai, memakai, menebak. Kategori default yang ditolak: katalog
  budaya berupa grid foto + paragraf panjang.
- **OWN-WORLD:** "Ruang batik" — kanvas indigo pekat (#16283F) sebagai kain dasar,
  panel kain mori krem (#F3EAD8) untuk kartu, aksen sogan (#7A4A21) dan merah
  Lasem (#A63A2B) hanya untuk aksi & penanda penting. Pola SVG motif adalah
  elemen visual utama di mana-mana (hero band, kartu, mockup, kuis). Display
  face berkarakter (Bricolage Grotesque), body sans kerja (Inter). Radius kecil,
  garis tegas 1px, bayangan lembut ber-offset — bukan neobrutalisme, bukan kaca.
- **STORY:** Pengunjung paham dalam 5 detik: ini soal motif batik, bisa dimainkan.
  Lalu ia memilih: belajar (galeri), berkarya (studio), atau menguji diri (kuis).
- **FIRST VIEWPORT:** Pita pola Kawung raksasa yang bergerak pelan di atas hero
  indigo; judul "BATIK!" besar di kiri; subjudul satu kalimat; 3 fakta dalam
  satu baris; dua tombol (Jelajahi Motif, Main Kuis). Tanpa kicker/eyebrow.
- **FORM:** Aplikasi 3 tab (Galeri / Studio / Kuis), mobile-first, bottom nav.
- **FINISH:** unreviewed and undocumented is unfinished; this build ends with
  the finish review, the verdict, DESIGN.md, and every shipping raster carrying
  its provenance.

## Refero reference lock

- **Primary direction:** material batik itu sendiri — indigo/nila, sogan, merah
  getih pitik, kain mori krem. Bukan referensi web generik.
- **Preserve:** (1) indigo sebagai kanvas dominan, (2) pola sebagai konten utama
  bukan dekorasi, (3) tipografi display berkarakter + body netral, (4) densitas
  galeri rapat ala toko kain, (5) warna hanya dari palet batik (tanpa ungu/neon).
- **Borrow only:** pola tab-bottom ala aplikasi belanja (navigasi), dan kartu
  detail ala ensiklopedia (judul besar + fakta).
- **Reject:** hero foto stok batik, gradient dekoratif, kartu ikon generik,
  kicker di atas judul, krem + serif sebagai default aman.
- **Media strategy:** semua visual = pola SVG prosedural (code-native), tanpa
  foto. Mockup kemeja = siluet SVG berisi pola.

## Stack

Web artifact statis (single-file HTML + CSS + JS, client-side). Tanpa backend,
tanpa database, tanpa API key. Font: Bricolage Grotesque (display) + Inter
(body) via Google Fonts. Pola SVG dibuat sebagai fungsi JS
`patternSVG(motifId, palette)` → string SVG dengan `<pattern>` ber-ID unik.
Ekspor PNG via `<canvas>` (gambar SVG → canvas → `toBlob` → unduh).

## Struktur kode (ikut ARCHITECTURE.md §1 — static artifact)

```
index.html   # struktur + mounting point
styles.css   # token :root → komponen → responsive
app.js       # STATE satu objek → DATA (MOTIFS, PALETTES, QUIZ) → RENDER murni → EVENTS tipis
```

- State lokal: `tab`, `motifAktif`, `paletAktif`, `favorit[]`, `filter`, `query`,
  `kuis {soal[], idx, skor, selesai}`.
- State URL: hash `#galeri|#studio|#kuis`.
- State persisten: localStorage via satu modul `store` (`batik.favorit`,
  `batik.skorTerbaik`).
- Tidak ada import antar-fitur (single-file, modul dipisah per fungsi); tidak ada
  god component/file >300 baris — pecah app.js bila lewat (data.js terpisah
  untuk MOTIFS/PALETTES).
- Business logic (acak soal, hitung skor, ekspor PNG) di fungsi bernama, bukan
  di event handler. `querySelector` di-cache. IIFE/module scope.

## Animasi & delight (wajib)

1. Hero band pola bergerak pelan (background-position / transform, 40 detik/loop).
2. Ganti motif/palet di Studio: kain mockup "terbuka" — transisi opacity+scale
   300ms, bukan lompatan.
3. Jawaban kuis benar: efek **cap batik** — stempel "CAP!" menekan pola (scale
   1.15 → 1 + cincin) + skor bertambah dengan animasi angka.
4. Favorit: bintang berputar kecil saat ditandai.
5. Semua transisi: exponential ease-out, dari kondisi yang sudah terlihat
   (tanpa elemen tersembunyi menunggu animasi).

## Aksesibilitas & responsif

- Kontras teks ≥4.5:1; tombol ≥44px; fokus keyboard terlihat; semua kontrol
  punya label.
- Mobile-first: 1 kolom kartu di HP → 2 kolom tablet → 3 kolom desktop.
  Bottom nav HP, top nav ≥768px.
