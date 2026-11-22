# BATIK! — Studio Motif Batik Nusantara

Web app interaktif berbahasa Indonesia tentang motif batik tradisional: galeri
10 motif paling ikonik lengkap dengan makna dan cerita, **Studio** untuk meracik
warna motif sendiri lalu melihatnya di mockup kain & kemeja dan mengunduhnya
sebagai PNG, dan **Kuis Tebak Motif** yang menguji pengenalan motif dari
bentuknya — bukan warnanya.

> Program "1 Hari 1 Project" — 23 November 2026. Web app statis, tanpa backend,
> tanpa login, tanpa database.

## Kenapa ide ini dipilih

Kebanyakan orang Indonesia memakai batik tanpa tahu motif yang dipakainya
berarti apa. Batik adalah Warisan Budaya Takbenda UNESCO (2009) dan punya Hari
Batik Nasional tiap 2 Oktober — tapi pengetahuannya tersebar di artikel panjang
yang membosankan. BATIK! mengubahnya jadi sesuatu yang bisa **dimainkan**.

Efek kejutnya ada tiga:

1. **Bukan katalog foto.** Semua motif digambar ulang sebagai pola SVG
   prosedural orisinal dari struktur geometrinya (Kawung = 4 kelopak aren
   bersilangan, Parang = diagonal S tak putus, Mega Mendung = awan berlapis).
   Polanya hidup — bisa diwarnai ulang sesuka hati.
2. **Studio yang tak terduga.** Pilih motif + palet warna → motif langsung
   "dibuatkan kainnya" di mockup, lalu **unduh PNG pola hasil racikanmu
   sendiri**. Sebuah web batik yang jadi alat desain mini.
3. **Kuis yang mengecoh dengan benar.** Motif ditampilkan dalam palet warna
   acak — pemain harus mengenali dari **bentuk**, bukan warna. Itu cara belajar
   yang benar-benar nempel.

## Fitur

- **Galeri** — 10 kartu motif (pola SVG, nama, asal daerah, satu baris makna);
  pencarian teks; filter chip Semua / Keraton / Pesisir / Pernikahan / Favorit;
  panel detail berisi cerita lengkap + "Dipakai untuk" + tombol "Coba di Studio".
- **Favorit** — tandai motif dengan bintang, tersimpan di localStorage.
- **Studio** — strip 10 motif mini + 6 palet warna (Klasik Sogan, Indigo
  Keraton, Lasem Merah, Pesisir Cerah, Hijau Botol, Monokrom); preview langsung
  di mockup kain dan mockup kemeja (siluet SVG berisi pola); tombol Acak;
  **Unduh PNG** 600×600 pola hasil racikan.
- **Kuis Tebak Motif** — 10 soal acak, pola dalam palet acak, 4 pilihan nama;
  umpan balik langsung (jawaban benar → efek stempel "CAP!" ala cap batik;
  jawaban salah → nama + makna yang benar); progress + skor berjalan; layar
  hasil dengan gelar (Maestro Batik / Pembatik Mahir / Pecinta Batik /
  Pembatik Pemula / Masih Meraba Kain) dan skor terbaik tersimpan.
- **Navigasi** — 3 tab (Galeri / Studio / Kuis), bottom nav di HP, top nav di
  desktop, hash routing (`#galeri`, `#studio`, `#kuis`).
- **Hero** — pita pola Kawung bergerak pelan di atas kanvas indigo + 3 fakta
  (10 motif, UNESCO 2009, Hari Batik 2 Oktober).

## 10 motif (fakta terverifikasi)

| Motif | Asal | Makna |
|---|---|---|
| Kawung | Yogyakarta & Solo | Kesucian & pengendalian diri |
| Parang | Yogyakarta & Solo | Kekuatan & keberanian |
| Mega Mendung | Cirebon | Kesabaran & keteduhan hati |
| Truntum | Solo | Cinta yang tumbuh kembali |
| Sido Mukti | Solo & Yogyakarta | Makmur & bahagia |
| Sekar Jagad | Yogyakarta & Solo | Keindahan & keberagaman dunia |
| Buketan | Pekalongan | Keindahan flora pesisir |
| Lasem | Lasem, Rembang | Akulturasi Tionghoa–Jawa |
| Sido Asih | Yogyakarta & Surakarta | Kasih sayang & keharmonisan |
| Lereng | Jawa | Perlindungan & penyertaan |

Detail cerita tiap motif (termasuk Truntum yang diciptakan Permaisuri Sunan
Pakubuwana III, Parang Barong yang dulu hanya untuk raja, dan "merah getih
pitik" khas Lasem) ada di dalam aplikasi. Fakta dirangkum dari jawaku.com,
indonesia.travel, blog.knitto.co.id, dan Wikipedia (Batik Lasem), dicek
23 November 2026.

## Cara pakai

Buka aplikasinya di browser HP atau desktop. Tidak perlu install, tidak perlu
login.

- **Belajar:** buka tab Galeri, ketuk kartu motif untuk membaca ceritanya,
  tandai favorit dengan bintang.
- **Berkarya:** buka tab Studio, pilih motif dan palet, lihat hasilnya di kain
  dan kemeja, tekan **Unduh PNG** untuk menyimpan polamu.
- **Bermain:** buka tab Kuis, tebak 10 motif dari bentuknya, kejar gelar
  Maestro Batik.

## Cara menjalankan dari source

File `src/index.html` adalah aplikasi lengkap dalam satu file (HTML + CSS +
JS). Tidak ada proses build.

```bash
# cara 1: buka langsung
open src/index.html

# cara 2: sajikan lewat server statis apa pun, misal:
npx serve src
# lalu buka http://localhost:3000
```

Favorit dan skor terbaik tersimpan di localStorage browser
(`batik.favorit`, `batik.skorTerbaik`).

## Tech stack

- HTML + CSS + JavaScript murni (single-file, tanpa framework, tanpa backend)
- Pola SVG prosedural (fungsi `patternSVG(motifId, palette)`)
- Ekspor PNG via `<canvas>` (`toBlob`)
- Font: Bricolage Grotesque (display) + Inter (body), via Google Fonts
- localStorage untuk favorit & skor terbaik; hash routing untuk tab

## Struktur folder

```
2026-11-23-batik/
├── README.md
├── src/
│   └── index.html        # aplikasi lengkap (hasil export artifact)
└── openspec/
    └── changes/
        ├── 2026-11-23-batik/            # proposal, spec, design, tasks
        └── archive/
            └── 2026-11-23-batik/        # arsip change setelah selesai
```

## Link hasil

- Aplikasi: artifact `batik-studio-motif-batik-nusantara`
  (card widget: `web-artifact-build-completed-363a9d9c-aca6-4471-874d-0b09528d93b2`)
- Repo: https://github.com/junanda24/daily-batik
- Rilis: 23 November 2026

## Catatan / temuan saat build

- Semua pola adalah **interpretasi digital orisinal** dari struktur geometri
  motif tradisional — bukan foto/scan kain asli. Catatan ini juga tercantum di
  footer aplikasi.
- Verifikasi builder: filter Pesisir (3 kartu), pencarian "mega", detail
  Kawung, Studio (ganti palet Lasem Merah, Acak → Sekar Jagad × Indigo
  Keraton, Unduh PNG `batik-sekar-jagad.png` 600×600), favorit Parang, dan
  kuis penuh 10 soal sampai layar hasil (9/10, "Pembatik Mahir") — semua lolos
  tanpa error console. Satu perbaikan selama verifikasi: chip filter sempat
  tertutup nav bawah di HP saat scroll awal; diperbaiki dengan memadatkan hero
  di layar kecil, audit ulang bersih.
- Yang sengaja tidak dibuat: mode gelap/terang (dunia visual sudah dikunci
  indigo), galeri foto kain asli (butuh lisensi foto), dan motif di luar 10
  yang terverifikasi (menambah motif tanpa riset = risiko fabrikasi).
